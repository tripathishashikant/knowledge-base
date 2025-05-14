## 📌 Time Complexity vs Space Complexity vs Auxiliary Space

Understanding the differences between time, space, and auxiliary space is key when analyzing an algorithm's efficiency.

---

### 🕒 Time Complexity

- **Definition:**  
  Measures the number of operations an algorithm performs as the input size increases.

- **Focus:**  
  Execution speed.

- **Example:**  
  Looping through `n` items → `O(n)`

- **Question it answers:**  
  *How fast does the algorithm run?*

---

### 💾 Space Complexity

- **Definition:**  
  Total memory used by the algorithm, including:
  - Input data
  - Output data
  - Temporary variables
  - Call stack (if recursive)

- **Focus:**  
  Total memory consumption.

- **Example:**  
  Sorting an array in-place → `O(1)`  
  Cloning an array → `O(n)`

- **Question it answers:**  
  *How much memory is needed in total?*

---

### 🧠 Auxiliary Space

- **Definition:**  
  Extra memory used by the algorithm **excluding** input and output storage.

- **Focus:**  
  Working memory overhead.

- **Example:**  
  - **Merge Sort:**  
    - Total space: `O(n)`  
    - Auxiliary space: `O(n)`
  - **Quick Sort (in-place):**  
    - Total space: `O(log n)`  
    - Auxiliary space: `O(log n)`

- **Question it answers:**  
  *How much memory does the algorithm need to work (besides inputs/outputs)?*

---

### ✅ Quick Comparison Table

| Metric            | Includes Input/Output? | Focus           | Measures             |
|-------------------|------------------------|------------------|----------------------|
| **Time Complexity**   | ❌                     | Speed            | Steps/Operations     |
| **Space Complexity**  | ✅                     | Total memory     | All storage          |
| **Auxiliary Space**   | ❌                     | Extra memory     | Only temporary data  |

---

### 🧩 Ask Yourself

- Do you create new data structures? → **Affects auxiliary space**
- Is your input size large? → **Affects space complexity**
- Does your algorithm slow down with big `n`? → **Affects time complexity**
