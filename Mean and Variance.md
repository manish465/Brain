---
tags:
  - Math
---
**Mean (μ)**: The average value.

```Python
import numpy as np
data = [2, 4, 6, 8, 10]
mean = np.mean(data)  # 6.0
```

**Variance (σ²)**: Measures how spread out the data is.

```Python
variance = np.var(data)  # 8.0
```

**Standard Deviation (σ)**: Square root of variance — same unit as original data.

![[Pasted image 20250518155028.png]]

```Python
std_dev = np.std(data)  # ~2.83
```

> Why ML cares: Understanding distribution spread helps in normalization, gradient scaling, and evaluating model consistency.