---
tags:
  - HLD
  - interview-prep
---
To solve the **scaling problem**, **Consistent Hashing** is used instead of simple modulo hashing.

### **How Consistent Hashing Works**

1. **Map shards to a circular hash ring**
    - Instead of using `mod N`, assign each shard a position in a **hash ring** (0 to 2³²).
2. **Assign Data Based on the Ring**
    - Each key is hashed and placed on the ring.
    - The key is assigned to the **next available shard** in a clockwise direction.
3. **Scaling Without Major Data Migrations**
    - When adding a new shard, only **some** data is remapped instead of **all**.

### **Example of Consistent Hashing:**

#### Before Adding a New Shard
```css
   [Shard 1] → [Shard 2] → [Shard 3] (Keys assigned to nearest shard)
```
``
#### After Adding a New Shard

```css
   [Shard 1] → [Shard 2] → [Shard 4] → [Shard 3] (Only part of the keys rebalanced)
```

Only the keys between `Shard 2` and `Shard 3` are reassigned to `Shard 4`, instead of rehashing everything.

