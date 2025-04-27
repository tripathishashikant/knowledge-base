# Summary

- `call`, `apply`, and `bind` are methods to control the `this` keyword inside a function.

- `call` and `apply` invoke the function immediately.

- `bind` returns a new function without invoking it.

- `call` passes arguments one by one.

- `apply` passes arguments as an array.

- `bind` permanently sets `this` for future calls.

<br/>

# call

Calls a function with a given `this` and arguments one by one.

## Syntax

```javascript
functionName.call(thisContext, arg1, arg2, ...)
```

## Use Case

Borrow a method from one object for another object.

### Example

```javascript
const user = { name: 'John' };

function greet(age) {
  console.log(`Hi, I'm ${this.name} and I'm ${age} years old.`);
}

greet.call(user, 30); 
// Output: Hi, I'm John and I'm 30 years old.
```

<br/>

# apply

Same as `call` but arguments are passed as an array.

## Syntax

```javascript
functionName.apply(thisContext, [arg1, arg2, ...])
```

## Use Case

You don't know how many arguments you'll get dynamically.

### Example

```javascript
const user = { name: 'Jane' };

function introduce(city, country) {
  console.log(`${this.name} lives in ${city}, ${country}.`);
}

introduce.apply(user, ['Paris', 'France']);
// Output: Jane lives in Paris, France.
```

<br/>

# bind

Returns a new function with a fixed `this` context.

It does not call the function immediately.

## Syntax

```javascript
const newFunction = functionName.bind(thisContext, arg1, arg2, ...)
```

## Use Case

Useful for event handlers or delayed function execution where you want `this` to stay consistent.

### Example

```javascript
const person = { name: 'Mike' };

function sayName() {
  console.log(this.name);
}

const boundSayName = sayName.bind(person);

boundSayName();
// Output: Mike
```

<br/>

# Real Life Examples

## Borrowing Methods

```javascript
const car = { brand: 'Toyota' };
const bike = { brand: 'Yamaha' };

function showBrand() {
  console.log(this.brand);
}

showBrand.call(car);   // Toyota
showBrand.call(bike);  // Yamaha
```

## Merging Arrays (apply)

```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

arr1.push.apply(arr1, arr2);
console.log(arr1); // [1, 2, 3, 4, 5, 6]
```

## Setting `this` in Event Listeners (bind)

```javascript
function Button(name) {
  this.name = name;
}

Button.prototype.click = function() {
  console.log(`${this.name} button clicked`);
};

const saveButton = new Button('Save');
document.getElementById('saveBtn').addEventListener('click', saveButton.click.bind(saveButton));
```

<br/>

# Interview Questions

## Beginner

### What is the purpose of `call`, `apply`, and `bind` in JavaScript?

**Answer:** These methods are used to control the value of `this` inside a function.

### What happens when you call a function without binding its context?

**Answer:** In non-strict mode, `this` will default to the global object (e.g., `window` in browsers). In strict mode, `this` will be `undefined`.

### Can you bind a function to multiple contexts?

**Answer:** No, `bind` creates a new function with a fixed `this` value. You can only bind it to one context at a time.

### What will `func.call()` return if no arguments are passed?

**Answer:** The function will be called with the default `this` value, but no arguments are passed.

---

## Intermediate

### What is the difference between `call` and `apply`?

**Answer:** Both `call` and `apply` call a function with a specific `this` context, but `call` passes arguments individually, while `apply` passes them as an array.

### Explain how `bind` works with callback functions.

**Answer:** `bind` allows you to set a specific `this` context for a function that is later called as a callback. It ensures that `this` remains consistent when the function is executed.

### What will happen if you call a bound function multiple times?

**Answer:** The function will retain the same `this` context each time, and the arguments will be passed as defined by the `bind` operation.

### What does `bind` return?

**Answer:** `bind` returns a new function with the specified `this` context, which can be called later.

---

## Advanced

### How would you implement a polyfill for `bind`?

**Answer:** A custom implementation for `bind` involves using `apply` inside the new function to ensure the correct `this` context and arguments.

```javascript
Function.prototype.myBind = function(context, ...args) {
  const fn = this;
  return function(...innerArgs) {
    return fn.apply(context, [...args, ...innerArgs]);
  };
};
```

### What is the difference between `bind` and `call` when used in an event listener?

**Answer:** `call` will immediately invoke the function with the provided `this`, while `bind` creates a new function that binds `this` and returns it. This is crucial in event listeners where `this` must refer to a specific object even after the event occurs.

<br/>

# Tricky Output-Based Questions (Beginner to Advanced)

## Beginner

### What will be the output of the following code?

```javascript
const obj = { name: 'Alice' };
function greet() {
  console.log(this.name);
}
greet();
```

**Answer:** `undefined`  
**Explanation:** `this` refers to the global object, and `name` is not defined in the global object.

### What will be the output of the following code?

```javascript
const obj = { name: 'Bob' };
function greet() {
  console.log(this.name);
}
greet.call(obj);
```

**Answer:** `Bob`  
**Explanation:** `call` sets `this` to the `obj` object.

### What will the following code print?

```javascript
const person = { name: 'Eve' };
const greet = function() {
  console.log(this.name);
};
const greetPerson = greet.bind(person);
greetPerson();
```

**Answer:** `Eve`  
**Explanation:** `bind` locks `this` to `person` permanently.

---

## Intermediate

### What is the output of this code?

```javascript
const obj = { name: 'Charlie' };
function greet(city) {
  console.log(`${this.name} is from ${city}`);
}
greet.apply(obj, ['London']);
```

**Answer:** `Charlie is from London`  
**Explanation:** `apply` sets `this` to `obj` and passes the arguments as an array.

### What will the output of this be?

```javascript
function multiply(a, b) {
  console.log(this.name);
  return a * b;
}
const multiplyBy2 = multiply.bind({ name: 'Math' }, 2);
console.log(multiplyBy2(3));
```

**Answer:**  
```
Math
6
```

**Explanation:** `bind` sets `this` to `{ name: 'Math' }` and binds the first argument (`2`). The second argument (`3`) is passed during the function call.

### What will the following output?

```javascript
const person = { name: 'Mark' };
function greet(age, country) {
  console.log(`${this.name} is ${age} years old and lives in ${country}`);
}
greet.call(person, 28, 'USA');
```

**Answer:** `Mark is 28 years old and lives in USA`  
**Explanation:** `call` sets `this` to `person` and passes `28` and `'USA'` as arguments.

---

## Advanced

### What will the output of this code be?

```javascript
const user = { name: 'Jordan' };
function greet(message) {
  console.log(`${message}, ${this.name}`);
}
const boundGreet = greet.bind(user, 'Hello');
setTimeout(boundGreet, 1000);
```

**Answer:** `Hello, Jordan`  
**Explanation:** `bind` locks `this` to `user` and passes `'Hello'` as the first argument. The function is called after 1000ms.

### What is the output of the following?

```javascript
const obj = { name: 'Anna' };
function greet(city) {
  console.log(`${this.name} lives in ${city}`);
}
greet.call(null, 'Paris');
```

**Answer:** `null lives in Paris`  
**Explanation:** When you pass `null` as `this`, it defaults to the global object in non-strict mode, or `null` in strict mode.

### What will the output be?

```javascript
const obj = { name: 'Leo' };
function greet() {
  console.log(this.name);
}
setTimeout(greet.bind(obj), 1000);
```

**Answer:** `Leo`  
**Explanation:** `bind` ensures that `this` remains tied to `obj` when `greet` is executed after the timeout.

### What will the output be in this scenario?

```javascript
const func = function(a, b) {
  console.log(this.name, a, b);
};
const newFunc = func.bind({ name: 'Sam' }, 1);
newFunc(2);
```

**Answer:** `Sam 1 2`  
**Explanation:** `bind` fixes `this` and the first argument (`1`) for the function, and `2` is passed as the second argument.


