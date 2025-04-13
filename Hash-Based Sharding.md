---
tags:
  - HLD
---
Hash-based sharding is a **[[database partitioning technique]]** where a **hash function** is applied to a key (e.g., `user_id`, `order_id`) to determine which shard will store the data. This method ensures an **even distribution** of data across multiple shards and avoids range-based hotspots.

## **How Hash-Based Sharding Works**

1. **Choose a Hash Function**
    - A deterministic hash function (e.g., `MD5`, `SHA-256`, or a simple modulo operation) is applied to the **sharding key**.

2. **Compute the Shard Number**
    - The hashed key is divided by the number of shards (`N`), and the remainder (`mod N`) determines the shard.
   
```Java
int shard = hash(key) % totalShards;
```

3. **Route the Data to the Corresponding Shard**
    - The database stores or retrieves the record from the assigned shard.
## **Example: Hash-Based Sharding in Action**

Let's assume we have **4 shards (0, 1, 2, 3)** and we are sharding user data based on `user_id`.

### **Step 1: Compute the Hash**

A simple hash function:
```Java
int hashFunction(int key) {
    return key % 4;  // 4 shards
}
```

### **Step 2: Assign Shards**

For different `user_id` values:

|`user_id`|`hash(user_id) % 4`|Assigned Shard|
|---|---|---|
|105|`105 % 4 = 1`|**Shard 1**|
|208|`208 % 4 = 0`|**Shard 0**|
|317|`317 % 4 = 1`|**Shard 1**|
|429|`429 % 4 = 1`|**Shard 1**|

This ensures an **even distribution** of data.

## **Advantages of Hash-Based Sharding**

✅ **Even Distribution** – Data is spread evenly if the hash function is good.  
✅ **Prevents Hotspots** – Unlike range-based sharding, skewed data does not overload one shard.  
✅ **Fast Lookups** – Hashing provides a quick way to find the right shard.

## **Disadvantages of Hash-Based Sharding**

❌ **Shard Addition Problem (Resharding Issue)**

- If you **increase the number of shards (e.g., from 4 to 5)**, all existing keys will **map to different shards**, requiring a full data migration.
- Example
```Java
int shard = hash(user_id) % 5;  // New total shards = 5
```

- Almost **all** data must be moved, causing **downtime**.

❌ **Cross-Shard Queries Are Difficult**
- Joins across shards are **expensive** and need application-level logic.

❌ **Complex Scaling**
- Unlike **consistent hashing**, adding shards disrupts the entire system.

## **Solution: [[Consistent Hashing]] (Fixing the Scaling Issue)**
To **solve the resharding problem**, **consistent hashing** is used instead of `mod N`.
### **How Consistent Hashing Fixes the Issue**
- Instead of `mod N`, **a circular hash space** is created.
- New shards **take over only a portion of the data**, avoiding full migration.