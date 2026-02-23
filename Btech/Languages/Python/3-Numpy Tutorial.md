````markdown
---
tags: [python, numpy, data-science, ml-foundations]
created: {{date}}
---

# 🧮 NumPy – Tutorial 3
Links: [[Python]], [[Data Science]], [[Linear Algebra]]

--- 
## 📌 What is NumPy?

**NumPy (Numerical Python)** is a library for fast numerical computation using multidimensional arrays.

> [!NOTE]
> NumPy is faster than Python lists because:
> - Contiguous memory
> - Vectorized operations
> - Implemented in C

---

## ⚙️ Import

```python
import numpy as np
````

---

# 📊 Creating Arrays

## From List

```python
arr = np.array([1, 2, 3, 4])
```

## 2D Array

```python
arr2 = np.array([[1, 2, 3],
                 [4, 5, 6]])
```

---

## 🔍 Array Attributes

```python
arr.shape      # dimensions
arr.ndim       # number of axes
arr.size       # total elements
arr.dtype      # data type
```

Example:

```python
arr = np.array([[1,2,3],[4,5,6]])
print(arr.shape)   # (2, 3)
```

---

# 🔢 Special Arrays

Links: [[Matrix Initialization]]

## Zeros

```python
np.zeros((3, 3))
```

## Ones

```python
np.ones((2, 4))
```

## Identity Matrix

```python
np.eye(3)
```

$$  
I_n =  
\begin{bmatrix}  
1 & 0 & 0 \  
0 & 1 & 0 \  
0 & 0 & 1  
\end{bmatrix}  
$$

---

## Range

```python
np.arange(0, 10, 2)
```

## Even Spacing

```python
np.linspace(0, 1, 5)
```

$$  
\text{Creates evenly spaced values between } a \text{ and } b  
$$

---

# 📏 Reshaping Arrays

Tags: #array-operations  
Links: [[Matrix Operations]]

```python
arr = np.arange(12)
arr.reshape(3, 4)
```

$$  
\text{Total elements must remain the same}  
$$

> [!WARNING]  
> If element count changes → ValueError

---

# 🔍 Indexing & Slicing

Links: [[Python Indexing]]

## 1D

```python
arr[2]
arr[1:4]
```

## 2D

```python
arr2[0, 1]
arr2[:, 1]   # column
arr2[1, :]   # row
```

> [!TIP]  
> `:` means select all elements.

---

# ⚡ Vectorized Operations

Tags: #vectorization  
Links: [[Broadcasting]]

```python
arr = np.array([1, 2, 3])
arr * 2
```

Result:

$$  
y_i = 2x_i  
$$

## Element-wise Operations

```python
a + b
a - b
a * b
a / b
```

> [!NOTE]  
> No loops required → faster computation.

---

# 📡 Broadcasting

Links: [[Vectorization]]

Allows operations between arrays of different shapes.

Example:

```python
arr = np.array([[1, 2, 3],
                [4, 5, 6]])

arr + 10
```

$$  
\text{Smaller array is stretched to match the larger one}  
$$

> [!WARNING]  
> Shapes must be compatible.

---

# 📈 Statistical Functions

Tags: #statistics

```python
arr.mean()
arr.std()
arr.min()
arr.max()
arr.sum()
```

Axis operations:

```python
arr.sum(axis=0)   # column sum
arr.sum(axis=1)   # row sum
```

---

# 🔄 Copy vs View

Links: [[Memory Management]]

```python
a = np.array([1, 2, 3])
b = a
b[0] = 10
```

Now `a` is also changed because both share memory.

Proper copy:

```python
b = a.copy()
```

> [!IMPORTANT]  
> Use `.copy()` to avoid unintended changes.

---

# 🧠 NumPy Mindset

Bad (loop):

```python
for i in range(len(arr)):
    arr[i] *= 2
```

Good (vectorized):

```python
arr *= 2
```

> [!NOTE]  
> Think in arrays, not loops.

---

# 🔗 Related Notes

- [[NumPy]]
    
- [[Vectorization]]
    
- [[Broadcasting]]
    
- [[Matrix Operations]]
    
- [[Linear Algebra]]
    
- [[Memory Management]]
    
- [[Python Performance]]
    

---

# 🏷️ Tags

#numpy  
#data-science  
#ml-foundations  
#array-operations  
#vectorization