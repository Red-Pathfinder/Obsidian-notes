---  
Links: [[Python]] | [[Data Science]] | [[Linear Algebra]] | [[Vectorization]] | [[Broadcasting]]  
  
##  What is NumPy?  
  
**NumPy (Numerical Python)** is a library for fast numerical computation using multidimensional arrays.  
  
> [!NOTE]  
> NumPy is faster than Python lists because:  
> - Contiguous memory  
> - Vectorized operations  
> - Implemented in C  
  
##  Import  
  
```python  
import numpy as np
```

##  Creating Arrays

### From List

arr = np.array([1, 2, 3, 4])

### 2D Array

arr2 = np.array([  
    [1, 2, 3],  
    [4, 5, 6]  
])

##  Special Arrays

np.zeros((3, 3))  
np.ones((2, 4))  
np.eye(3)

In=[100010001]I_n = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}In​=​100​010​001​​

## ⚡ Vectorization

arr = np.array([1, 2, 3])  
arr * 2

yi=2xiy_i = 2x_iyi​=2xi​

## 📡 Broadcasting

arr2 + 10

> [!WARNING]  
> Shapes must be compatible.

---

#numpy #vectorization #broadcasting #array-operations