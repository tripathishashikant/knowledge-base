## Checking for NaN in JavaScript

**Summary:** In JavaScript, `NaN` is best checked using `variable !== variable` (after converting to a Number) or `!Number.isNaN(variable)`. The `isNaN()` function is less reliable due to its type coercion.

# Checking for NaN in JavaScript

It's crucial to use a reliable method when checking if a variable holds the value `NaN` in JavaScript. Here are two recommended approaches:

### 1. `variable !== variable`

* This method leverages the unique property of `NaN`: it's the only value not strictly equal to itself.
* **Important:** To ensure accuracy, the variable should be explicitly converted to a Number using `Number()` before the comparison.

    ```javascript
    let value = Number("abc"); // value is now NaN
    if (value !== value) {
      console.log("value is NaN");
    } else {
      console.log("value is not NaN");
    }
    ```

### 2. `!Number.isNaN(variable)`

* This method uses the `Number.isNaN()` function, which checks if a value is strictly equal to `NaN` without any type coercion.
* The `!` operator negates the result, effectively checking if the variable is *not* NaN.

    ```javascript
    let value1 = 123;
    let value2 = NaN;

    if (!Number.isNaN(value1)) {
      console.log("value1 is not NaN");
    } else {
      console.log("value1 is NaN");
    }

    if (!Number.isNaN(value2)) {
      console.log("value2 is not NaN");
    } else {
      console.log("value2 is NaN");
    }
    ```

### Why `isNaN()` is not preferred

* The global `isNaN()` function performs type coercion before checking for `NaN`, which can lead to unexpected and incorrect results.
* For example, `isNaN("abc")` returns `true` because `"abc"` is coerced to `NaN`.

## Interview Questions on NaN

Here are some common interview questions related to NaN and how to check for it in JavaScript:

* **What is `NaN` in JavaScript?**
    * Short Answer: `NaN` stands for "Not a Number" and represents an invalid or undefined numerical value.

* **How do you check if a value is `NaN` in JavaScript?**
    * Short Answer: Use `variable !== variable` (after converting to a Number) or `!Number.isNaN(variable)`.

* **What is the difference between `isNaN()` and `Number.isNaN()`?**
    * Short Answer: `isNaN()` performs type coercion before checking, while `Number.isNaN()` does not.

* **Why is `Number.isNaN()` generally preferred over `isNaN()`?**
    * Short Answer: `Number.isNaN()` is more reliable because it avoids unexpected results due to type coercion.

* **Explain why `NaN !== NaN` evaluates to `true`.**
    * Short Answer: `NaN` is the only value in JavaScript that is not equal to itself.

* **Can you describe a scenario where `isNaN()` might give an unexpected result?**
    * Short Answer: `isNaN("abc")` returns `true`, even though "abc" is a string, because `isNaN` coerces it to `NaN`.

* **What will be the output of `typeof NaN` and why?**
    * Short Answer: "number". `NaN` is considered a numerical value, albeit an invalid one.

* **Is `NaN` a primitive data type in JavaScript?**
    * Short Answer: Yes, `NaN` is a property of the Number primitive type.

* **How does JavaScript handle `NaN` in arithmetic operations?**
    * Short Answer: Any arithmetic operation involving `NaN` will result in `NaN`.

* **Write a function to check if a given input is `NaN`**
    * ```javascript
        function isNaNValue(value) {
          return value !== value;
        }
        ```

## Tricky Output-Based Questions

These questions test a deeper understanding of NaN and its behavior in JavaScript.

1.  **What is the output of the following expressions?**

    ```javascript
    console.log(NaN === NaN);
    console.log(isNaN("hello"));
    console.log(Number.isNaN("123"));
    console.log(typeof NaN);
    console.log(0 / 0);
    console.log(1 + NaN);
    console.log(NaN - NaN);
    ```

    * Output:

        ```
        false
        true
        false
        "number"
        NaN
        NaN
        NaN
        ```

2.  **Explain the behavior of the following code snippet:**

    ```javascript
    let x = "hello" / 5;
    if (x == NaN) {
      console.log("x is equal to NaN");
    } else {
      console.log("x is not equal to NaN");
    }
    ```

    * Explanation:
        * `"hello" / 5` results in `NaN` because "hello" cannot be coerced into a valid number for division.
        * The condition `x == NaN` evaluates to `false` because `NaN` is not equal to any value, including itself.
        * Therefore, the output will be "x is not equal to NaN".

3.  **What will be the output of the following function calls?**

    ```javascript
    function checkNaN(value) {
      if (value !== value) {
        return true;
      }
      return false;
    }

    console.log(checkNaN(NaN));
    console.log(checkNaN(Number("123")));
    console.log(checkNaN(Number("abc")));
    ```

    * Output:

        ```
        true
        false
        true
        ```

4.  **Predict the output of the following code:**

    ```javascript
    let arr = [1, 2, NaN, 4, 5];
    let sum = 0;
    for (let i = 0; i < arr.length; i++) {
      if (!Number.isNaN(arr[i])) {
        sum += arr[i];
      }
    }
    console.log(sum);
    ```

    * Output:
        ```
        12
        ```
    * Explanation: The code iterates through the array, checks for NaN using `!Number.isNaN()`, and adds only the non-NaN values to the sum.

5.  **Explain why the following code does not work as expected for checking NaN:**

    ```javascript
    let value = "abc";
    if (isNaN(value)) {
      console.log("Value is NaN");
    } else {
      console.log("Value is not NaN");
    }
    ```

    * Explanation:
        * `isNaN("abc")` returns `true` because `isNaN` coerces the string "abc" to a number, which results in `NaN`.
        * The code incorrectly identifies "abc" as NaN due to this type coercion, which is why `Number.isNaN()` is preferred for accurate NaN checks.
