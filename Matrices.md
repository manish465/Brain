---
tags:
  - Math
---
A **matrix** is a 2D array of numbers. Think of it like:
- A transformation machine for vectors
- A way to represent systems of equations

```Python
A = np.array([[1, 2],
              [3, 4]])
```

You can multiply a vector by a matrix to rotate, scale, or skew it:

```Python
v = np.array([1, 2])
result = A @ v  # Matrix-vector multiplication
```

### Operations
- **Matrix multiplication**: Combine transformations
- **Transpose**: `A.T`
- **Inverse**: `np.linalg.inv(A)` (if it exists)
- **Determinant**: `np.linalg.det(A)` (helps in finding invertibility)