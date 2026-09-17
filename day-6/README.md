# 🔢 NumPy Practice Notebook - Python Mini-Project (Day 6)

**Student Name:** Patel Harshilkumar Rajubhai
**Project Track:** Day 6 NumPy Practice Notebook
**Deliverable:** `IDRA DAY 6.ipynb` (Google Colab Notebook)

---

## 📌 Executive Summary

This project is a **Google Colab Notebook** that shows my understanding of **NumPy** and how it is used for numerical data analysis in Python.

The notebook is organised into clear sections, each covering one important NumPy operation with simple code and output. It starts with creating 1D, 2D, and 3D arrays, then checks the array dimensions and data types, does indexing and slicing, reshapes arrays, generates arrays using `zeros()`, `ones()`, `arange()`, and `linspace()`, and carries out mathematical and vectorized operations)Skip. It also demonstrates **boolean masking**, **broadcasting**, and common **aggregate functions** like `sum()`, `mean()`, `min()`, `max()`, and `median()`.

Every section has a heading, the code, and the result printed, so the whole notebook works as a complete NumPy cheat-sheet built from scratch in Colab.

---

## 🎯 Assignment Statement (Day 6)

> Create a Google Colab Notebook demonstrating your understanding of NumPy and its use for numerical data analysis. The notebook should include examples of creating 1D, 2D, and 3D arrays, checking array dimensions and data types, indexing and slicing, reshaping arrays, generating arrays using functions such as `zeros()`, `ones()`, `arange()`, and `linspace()`, and performing mathematical and vectorized operations. Also demonstrate boolean masking, broadcasting, and common aggregate functions such as `sum()`, `mean()`, `min()`, `max()`, and `median()`. Keep the notebook well organized with clear headings, code, and outputs for each operation.

---

## 🧰 What We Used

| Library | Purpose |
|---------|---------|
| NumPy (`import numpy as np`) | All numerical array creation, manipulation, and analysis |

Only one `import numpy as np` line is needed at the very start of the notebook.

---

## 📚 Topics Covered in the Notebook

| # | Section | What It Shows |
|---|---------|---------------|
| 1 | Import NumPy | Import the library as `np` |
| 2 | Create 1D, 2D, 3D arrays | `np.array()` with one, two, and three dimensions |
| 3 | Dimensions and data types | `.shape`, `.ndim`, `.dtype` |
| 4 | Indexing and slicing | Pick single elements, rows, columns, and ranges |
| 5 | Reshape | Change array shape with `.reshape()` |
| 6 | `zeros()`, `ones()`, `arange()`, `linspace()` | Generate arrays easily |
| 7 | Mathematical & vectorized operations | Add, subtract, multiply, powers, sqrt |
| 8 | Boolean masking | Filter values with a condition |
| 9 | Broadcasting | Work with different sized arrays together |
| 10 | Aggregate functions | `sum()`, `mean()`, `min()`, `max()`, `median()` |

---

## 🔍 Code Walkthrough

### 1. Import NumPy

```python
import numpy as np
```

### 2. Create 1D, 2D and 3D arrays

```python
arr1 = np.array([1, 2, 3, 4])
arr2 = np.array([[1, 2, 3], [4, 5, 6]])
arr3 = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])

print("1D array is:", arr1)
print("2D array is:")
print(arr2)
print("3D array is:")
print(arr3)
```

### 3. Check dimension and data type

```python
print("1D shape:", arr1.shape, "| dim:", arr1.ndim, "| type:", arr1.dtype)
print("2D shape:", arr2.shape, "| dim:", arr2.ndim, "| type:", arr2.dtype)
print("3D shape:", arr3.shape, "| dim:", arr3.ndim, "| type:", arr3.dtype)
```

### 4. Indexing and slicing

```python
print("First element:", arr1[0])
print("Last element:", arr1[-1])
print("First two elements:", arr1[0:2])
print("Row 1 col 2:", arr2[1, 2])
print("First row:", arr2[0])
print("Second column:", arr2[:, 1])
```

### 5. Reshape

```python
arr4 = np.arange(1, 13)
print("Normal array:", arr4)
print("Reshape to 3 rows 4 cols:")
print(arr4.reshape(3, 4))
print("Reshape to 2 rows 6 cols:")
print(arr4.reshape(2, 6))
```

### 6. Generate arrays with zeros, ones, arange, linspace

```python
z = np.zeros((2, 3))
o = np.ones((2, 3))
a = np.arange(0, 10, 2)
l = np.linspace(0, 1, 5)

print("zeros result:")
print(z)
print("ones result:")
print(o)
print("arange result:", a)
print("linspace result:", l)
```

### 7. Mathematical and vectorized operations

```python
x = np.array([1, 2, 3])
y = np.array([4, 5, 6])

print("x is:", x)
print("y is:", y)
print("x + y is:", x + y)
print("x - y is:", x - y)
print("x * y is:", x * y)
print("x power 2 is:", x ** 2)
print("square root of x is:", np.sqrt(x))
```

### 8. Boolean masking

```python
marks = np.array([45, 80, 92, 33, 67, 55])
passed = marks >= 50

print("Marks are:", marks)
print("Pass mask is:", passed)
print("Passed marks are:", marks[passed])
print("Failed marks are:", marks[~passed])
```

### 9. Broadcasting

```python
a = np.array([1, 2, 3])
print("a is:", a)
print("a + 10 is:", a + 10)

b = np.array([[1], [2], [3]])
c = np.array([10, 20, 30])
print("b is (3 rows 1 col):")
print(b)
print("c is:", c)
print("b + c broadcast result is:")
print(b + c)
```

### 10. Aggregate functions

```python
d = np.array([10, 20, 30, 40, 50])

print("d is:", d)
print("Sum is:", np.sum(d))
print("Mean is:", np.mean(d))
print("Min is:", d.min())
print("Max is:", d.max())
print("Median is:", np.median(d))
```

---

## 💡 Example Output (Snippet)

```
1D array is: [1 2 3 4]
2D array is:
[[1 2 3]
 [4 5 6]]
3D shape: (2, 2, 2) | dim: 3 | type: int64
Marks are: [45 80 92 33 67 55]
Pass mask is: [False  True  True False  True  True]
Passed marks are: [80 92 67 55]
Sum is: 150
Mean is: 30.0
Median is: 30.0
```

---

## ✅ Why This Design Is Good

- **Well organised** — clear headings and one topic per section make it easy to follow.
- **Complete coverage** — every required NumPy operation from the assignment is included.
- **Beginner friendly** — simple variables, plain `print()` statements, and no confusion.
- **Vectorized thinking** — operations run on whole arrays without loops, which is the NumPy way.
- **Ready for Colab** — the notebook opens and runs directly in Google Colab with zero setup.
- **Good reference** — works as a quick NumPy cheat-sheet for future assignments.

---

## 🎯 Conclusion

The Day 6 notebook successfully demonstrates all the NumPy basics required by the assignment. From creating arrays of different shapes and checking their dimensions and data types, to indexing, slicing, reshaping, generating sequences, doing vectorized math, filtering with boolean masks, broadcasting, and using aggregate functions — every important NumPy skill is shown with simple code and clear output.

The notebook is well structured and beginner friendly, and it gives a strong foundation for all the numerical analysis work that comes later in the course.

---

## 👤 Author Information

**Student Name:** Patel Harshilkumar Rajubhai
**Topic:** NumPy Practice Notebook
**Project:** Day 6

---

## 📜 License

This project is open-source and released under the **MIT License**. See the [LICENSE](LICENSE) file for details.
