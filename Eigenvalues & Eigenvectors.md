---
tags:
  - Math
---
Eigenvectors are those special vectors that _don’t change direction_ when a transformation (matrix) is applied. They just get scaled.

> `A * v = λ * v`

Where:
- `A` is a matrix
- `v` is an eigenvector
- `λ` (lambda) is an eigenvalue (the scale factor)

Use case? Tons!
- PCA (Principal Component Analysis) uses eigenvectors to find directions of maximum variance
- Stability analysis, facial recognition, Google's PageRank...

```Python
values, vectors = np.linalg.eig(A)
```