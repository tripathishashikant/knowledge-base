# 📌 Summary

A **Stack** is a linear data structure following **LIFO (Last-In-First-Out)**.

Operations occur at one end — **the top**.

**Core operations:**

- `push()` → add  
- `pop()` → remove  
- `peek()` → view top  
- `isEmpty()` → check if empty  
- `size()` → count items  

---

# 📘 Main Concepts

## Why Use Stack?

Solves problems involving:

- Reversal  
- Backtracking  
- Nested structures  

**Used in:**

- Undo/redo operations  
- Expression evaluation  
- Syntax parsing  

## JS Implementation Options

**Using Array**

```js
let stack = [];
stack.push(1);
stack.pop();
```

## Using Object

```js
// stack implementation

function Stack() {
    this.top = -1
    this.storage = {}
    
    this.push = function(value) {
        this.top += 1
        this.storage[this.top] = value
    }
    
    this.pop = function() {
        if (this.top === -1) return null
        
        const popEle = this.storage[this.top]
        
        delete this.storage[this.top]
        this.top -= 1
        
        return popEle
    }
    
    this.peek = function() {
        if (this.top === -1) return null
        
        return this.storage[this.top]
    }
    
    this.size = function() {
        if (this.top === -1) return null
        
        return this.top + 1
    }
}

const stack1 = new Stack()
```

## Using Linked List

Nodes contain:

- `value`  
- Reference to `next` node  

More flexible with memory than arrays.

```js
function Node(value) {
  this.value = value;
  this.next = null;
}

function Stack() {
  this.top = null;

  this.push = function (val) {
    const newNode = new Node(val);
    newNode.next = this.top;
```

---

# 💡 Examples

## Easy

- Valid Parentheses  
- Reverse a String  
- Implement Stack using Queues  
- Min Stack  
- Evaluate Postfix Expression  
- Check Palindrome using Stack  
- Decimal to Binary conversion  
- Remove adjacent duplicates  
- Implement Queue using Stack  
- Balanced Brackets  

## Medium

- Next Greater Element  
- Stock Span Problem  
- Sort a Stack using recursion  
- Celebrity Problem  
- Infix to Postfix Conversion  
- Check redundant brackets  
- Decode String (Leetcode)  
- Design a browser history stack  
- Histogram area  
- Remove K digits to get smallest number  

## Hard

- Trapping Rain Water  
- Largest Rectangle in Histogram  
- Maximum Rectangular Area in Binary Matrix  
- Maximal Rectangle (Leetcode)  
- Sliding Window Maximum  
- Asteroid Collision  
- Flatten Nested List Iterator  
- Evaluate Expression with precedence  
- Histogram with varying bar width  
- Clone Stack without using extra stack  

---

# 🎯 Interview Questions (with answers)

**What is the time complexity of basic stack operations?**  
→ `O(1)` for push, pop, peek  

**What data structures can be used to implement a stack?**  
→ Array, Linked List  

**How is stack different from a queue?**  
→ Stack is LIFO, queue is FIFO  

**When would you choose a linked list over an array?**  
→ For dynamic size or frequent insertions/removals  

**Can stack be used to reverse a queue?**  
→ Yes, using two stacks  

**What is a stack overflow?**  
→ When stack exceeds its memory limit (e.g., infinite recursion)  

**Explain how browser back/forward navigation uses stacks.**  
→ Back stack for visited pages, forward stack for undone navigations  

**What is call stack?**  
→ A runtime stack to manage function calls and returns  

**How would you check for balanced parentheses?**  
→ Use a stack to match opening and closing brackets  

**Can a stack be implemented using two queues?**  
→ Yes, using two queues with extra logic to maintain order  

---

# 🔍 Output-Based Questions (with explanations)

## 1.

```js
let s = [];
s.push(10);
s.push(20);
s.pop();
console.log(s[s.length - 1]);
```
**Output:**  
```js
10
```

**Explanation:**  
20 is popped, 10 remains.

## 2.

```js
let s = [];
s.push(1);
s.push(2);
s.push(3);
console.log(s.pop());
console.log(s.pop());
```

**Output:**

```js
3
2
```

**Explanation:**  
20 is popped, 10 remains.

## 3.

```js
let s = [];
s.push('a');
s.push('b');
console.log(s.length);
```

**Output:**

```js
2
```

**Explanation:**  
Two elements in stack.

## 4.

```js
let s = [];
console.log(s.pop());
```

**Output:**

```js
undefined
```

**Explanation:**  
Nothing to pop.

## 5.

```js
let s = [];
s.push(1);
s.push(2);
s.pop();
s.push(3);
console.log(s[s.length - 1]);
```

**Output:**

```js
3
```

## 6.

```js
let s = [];
s.push(4);
s.push(5);
console.log(s.includes(4));
```

**Output:**

```js
true
```

## 7.

```js
let s = [];
s.push(100);
s.pop();
s.push(200);
console.log(s.length);
```

**Output:**

```js
1
```

## 8.

```js
let stack = [1, 2, 3];
while (stack.length) console.log(stack.pop());
```

**Output:**

```js
3
2
1
```

**Explanation:**  
Prints in reverse order.

## 9.

```js
let s = [];
for (let i = 0; i < 3; i++) s.push(i);
console.log(s);
```

**Output:**

```js
[0, 1, 2]
```

## 10.

```js
let s = [];
s.push('x');
s.pop();
console.log(s.length);
```

**Output:**

```js
0
```
