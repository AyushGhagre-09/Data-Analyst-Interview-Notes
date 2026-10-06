# NumPy Interview Questions

A collection of **NumPy interview questions** from basic to advanced level, with concise answers and examples.

---

# 🟢 Beginner Level

## 1. What is NumPy?

NumPy is a Python library used for **numerical computing**. Its main object is the **ndarray**, which supports fast operations on large numerical datasets.

---

## 2. Why is NumPy faster than Python lists?

NumPy is faster because:

- It stores data efficiently in memory.
- It performs operations using optimized compiled code.
- It supports **vectorized operations**, reducing the need for Python loops.

---

## 3. What is an ndarray?

`ndarray` is NumPy's **multidimensional array object**.

```python
import numpy as np

arr = np.array([10, 20, 30])
```

---

## 4. How do you create a NumPy array?

```python
import numpy as np

arr = np.array([10, 20, 30])
```

---

## 5. How do you check the dimensions of an array?

```python
arr.ndim
```

`ndim` returns the number of dimensions.

---

## 6. How do you check the shape of an array?

```python
arr.shape
```

Example:

```python
arr = np.array([[1, 2, 3],
                [4, 5, 6]])

print(arr.shape)
# (2, 3)
```

---

## 7. Difference between `shape`, `size`, and `ndim`

```python
arr.shape   # dimensions of the array
arr.size    # total number of elements
arr.ndim    # number of dimensions
```

---

## 8. How do you check the data type?

```python
arr.dtype
```

---

## 9. How do you create an array of zeros and ones?

```python
np.zeros((2, 3))
np.ones((2, 3))
```

---

## 10. What is `np.arange()`?

`np.arange()` creates values within a range using a specified step.

```python
np.arange(1, 10, 2)
```

Output:

```text
[1 3 5 7 9]
```

---

## 11. What is `np.linspace()`?

`np.linspace()` creates a specified number of **evenly spaced values** between two endpoints.

```python
np.linspace(0, 10, 5)
```

Output:

```text
[ 0.   2.5  5.   7.5 10. ]
```

---

## 12. Difference between `arange()` and `linspace()`

- `arange()` → based on **step size**
- `linspace()` → based on **number of values**

---

## 13. What is indexing?

Indexing is used to access individual elements of an array.

```python
arr[0]
```

---

## 14. What is slicing in NumPy?

Slicing is used to select a portion of an array using:

```text
[start : stop : step]
```

Example:

```python
arr = np.array([10, 20, 30, 40, 50])

arr[1:4]
# [20 30 40]

arr[:3]
# [10 20 30]

arr[2:]
# [30 40 50]

arr[::2]
# [10 30 50]

arr[::-1]
# [50 40 30 20 10]
```

### Important: Does slicing create a copy?

**Basic slicing usually returns a view, not a copy.**

```python
arr = np.array([10, 20, 30, 40, 50])

b = arr[1:4]

b[0] = 999

print(arr)
# [ 10 999  30  40  50]
```

Because `b` is a **view** of `arr`.

### Slicing in 2-D arrays

```python
arr = np.array([[1, 2, 3],
                [4, 5, 6],
                [7, 8, 9]])

arr[0:2, 1:3]
```

Output:

```text
[[2 3]
 [5 6]]
```

Here:

```text
rows    → 0:2
columns → 1:3
```

### Common slicing patterns

```python
arr[start:stop]
arr[start:stop:step]
arr[:, 1]       # all rows, column 1
arr[1, :]       # row 1, all columns
arr[::-1]       # reverse
```

> **Interview Rule:** Basic slicing → **View**. Fancy indexing and Boolean indexing → **Copy**.

---

# 🟡 Intermediate Level

## 15. What is reshaping?

Reshaping changes the structure of an array without changing its values.

```python
arr.reshape(2, 3)
```

---

## 16. What is boolean indexing?

Boolean indexing selects elements based on a condition.

```python
arr[arr > 50]
```

Example:

```python
arr = np.array([10, 60, 30, 80])

arr[arr > 50]
# [60 80]
```

Boolean indexing returns a **copy**.

---

## 17. What does `np.where()` do?

`np.where()` returns values based on a condition.

```python
np.where(arr > 50, "High", "Low")
```

---

## 18. What is broadcasting?

Broadcasting allows NumPy to perform operations between arrays with **different but compatible shapes**.

```python
arr = np.array([1, 2, 3])

print(arr + 10)
```

Output:

```text
[11 12 13]
```

---

## 19. What is vectorization?

Vectorization means performing operations on an entire array without explicitly writing a Python loop.

```python
arr * 2
```

Instead of:

```python
for i in arr:
    print(i * 2)
```

---

## 20. What does `axis=0` mean?

For a 2-D array:

```text
axis=0 → operation down the rows → result for each column
```

Example:

```python
np.sum(arr, axis=0)
```

---

## 21. What does `axis=1` mean?

For a 2-D array:

```text
axis=1 → operation across the columns → result for each row
```

Example:

```python
np.sum(arr, axis=1)
```

---

## 22. How do you calculate the mean?

```python
np.mean(arr)
```

---

## 23. How do you calculate the median?

```python
np.median(arr)
```

---

## 24. How do you find unique values?

```python
np.unique(arr)
```

---

## 25. How do you count unique values?

```python
values, counts = np.unique(arr, return_counts=True)
```

---

## 26. How do you sort a NumPy array?

```python
np.sort(arr)
```

---

## 27. Difference between `np.sort()` and `arr.sort()`?

```python
np.sort(arr)
```

Returns a **sorted copy**.

```python
arr.sort()
```

Sorts the original array **in place**.

---

## 28. How do you concatenate arrays?

```python
np.concatenate((a, b))
```

---

## 29. Difference between `concatenate()`, `vstack()`, and `hstack()`?

```python
np.concatenate((a, b))
np.vstack((a, b))
np.hstack((a, b))
```

- `concatenate()` → joins arrays along a specified axis
- `vstack()` → vertical stacking
- `hstack()` → horizontal stacking

---

## 30. How do you find NaN values?

```python
np.isnan(arr)
```

---

## 31. How do you replace NaN values?

```python
arr[np.isnan(arr)] = 0
```

---

# 🔴 Advanced Level

## 32. What is a view and a copy?

### View

A view shares the same underlying data.

```python
b = a.view()
```

### Copy

A copy creates independent data.

```python
b = a.copy()
```

Changes to the copy do not affect the original array.

---

## 33. What happens with `b = a`?

```python
b = a
```

Both variables refer to the **same array object**.

---

## 34. Difference between `*` and `@`?

```python
A * B
```

Element-wise multiplication.

```python
A @ B
```

Matrix multiplication.

---

## 35. What is matrix multiplication?

Matrix multiplication can be performed using:

```python
np.matmul(A, B)
```

or:

```python
A @ B
```

---

## 36. What is a dot product?

```python
np.dot(a, b)
```

For vectors, the dot product multiplies corresponding elements and then adds them.

Example:

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

np.dot(a, b)
```

Output:

```text
32
```

---

## 37. What is a cross product?

```python
np.cross(a, b)
```

It calculates the cross product of two vectors.

---

## 38. How do you generate random numbers?

### Random floats

```python
np.random.rand(3, 3)
```

### Random integers

```python
np.random.randint(1, 10, 3)
```

---

## 39. Difference between `rand()` and `randint()`?

```python
np.random.rand(3)
```

Generates random **floating-point numbers**.

```python
np.random.randint(1, 10, 3)
```

Generates random **integers**.

---

## 40. What is a random seed?

A seed makes random results **reproducible**.

```python
np.random.seed(42)
```

Running the same random code after setting the same seed produces the same results.

---

## 41. What is `np.argmax()`?

Returns the index of the maximum value.

```python
np.argmax(arr)
```

---

## 42. What is `np.argmin()`?

Returns the index of the minimum value.

```python
np.argmin(arr)
```

---

## 43. How do you find the maximum value for each column?

```python
np.max(arr, axis=0)
```

---

## 44. How do you find the minimum value for each row?

```python
np.min(arr, axis=1)
```

---

# ⭐ Most Important Interview Topics

For NumPy interviews, focus strongly on:

- `ndarray`
- `shape`, `size`, `ndim`, `dtype`
- Indexing and slicing
- Basic slicing vs fancy indexing
- Boolean indexing
- `axis=0` vs `axis=1`
- `reshape()`
- `flatten()` vs `ravel()`
- Broadcasting
- Vectorization
- View vs copy
- `concatenate()`, `vstack()`, `hstack()`
- `np.where()`
- `np.unique()`
- `np.sort()`
- `*` vs `@`
- Dot product and matrix multiplication
- Random functions
- `argmax()` and `argmin()`
- Handling `NaN`

> **Interview Tip:** Be ready to explain the concept **and write a small code example** for each important topic.
