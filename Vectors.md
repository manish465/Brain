---
tags:
  - Math
---
Think of a **vector** as:
- A point in space, like an arrow from the origin to a location.
- A list of numbers representing magnitude and direction.

```Python
import numpy as np
v = np.array([3, 4])
```

This is a 2D vector. Its length (magnitude) is `sqrt(3² + 4²) = 5`.
### Operations:
- **Addition**: `[1, 2] + [3, 4] = [4, 6]`
- **Dot product**: `a · b = |a||b|cosθ` (measures similarity)
- **Scalar multiplication**: Stretch/shrink the vector