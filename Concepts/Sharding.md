---
tags:
  - Database
  - HLD
  - interview-prep
aliases:
  - sharding
---
Sharding is a **[[database partitioning technique]]** that distributes large datasets across multiple databases (shards) to improve **[[Scalability|scalability]], [[performance]], and [[Availability|availability]]**. Each shard is an independent database that contains a subset of the overall data.

### **Why Use Sharding?**

1. **Improves Performance** – Reduces query load on a single database by distributing it across multiple shards.
2. **Scales Horizontally** – Instead of upgrading a single powerful database (vertical scaling), new shards can be added (horizontal scaling).
3. **Reduces Latency** – Queries run faster as they operate on smaller datasets.
4. **Increases Availability** – Failure of one shard does not affect the entire system.

### **Types of Sharding**

1. **Range-Based Sharding**
    - Data is partitioned based on a range of values.
    - Example:
        - **Users with ID 1-1000 → Shard 1**
        - **Users with ID 1001-2000 → Shard 2**
    - Issue: Uneven load distribution if data is not uniform.
2. **[[Hash-Based Sharding]]**
    - A **hash function** is applied to a key (e.g., User ID) to determine which shard stores the data.
    - Example:
		```Java
		shard_number = hash(user_id) % total_shards;
		```
    - Balances load but makes data migration tricky if shards need to be added.
3. **Geo-Based Sharding**
    - Data is partitioned by geographic location.
    - Example:
        - **Users from the US → Shard 1**
        - **Users from Europe → Shard 2**
    - Best for globally distributed applications.
4. **Directory-Based Sharding**
    - A lookup table determines which shard stores the data.
    - Example:
        - **User 123 → Shard 2 (Lookup Table Entry)**
    - Requires an additional metadata store.

### **Example of Sharding in Practice**

Imagine an **e-commerce** platform with millions of users and orders.
- Without sharding: A single **monolithic** database struggles with performance.
- With sharding:
    - **Orders** are stored in multiple shards based on `user_id`.
    - A `hash-based sharding` strategy distributes users evenly across shards.

### **Challenges of Sharding**
1. **Complex Queries** – Joins across shards are difficult.
2. **Data Migration** – Adding/removing shards requires rebalancing.
3. **Increased Operational Complexity** – Needs proper shard mapping and routing.
4. **Cross-Shard Transactions** – ACID compliance is harder to maintain.

### **Sharding vs [[Replication]]**

| Feature               | Sharding                        | Replication                              |
| --------------------- | ------------------------------- | ---------------------------------------- |
| **Purpose**           | Scalability                     | High availability                        |
| **Data Distribution** | Different data in each shard    | Same data in all replicas                |
| **Performance Boost** | Queries run on smaller datasets | Read queries improve, writes remain same |
| **Complexity**        | High                            | Moderate                                 |
### **When to Use Sharding?**
✅ **Large-scale applications** (e.g., LinkedIn, Facebook, E-commerce platforms).  
✅ **High write throughput** (many transactions per second).  
✅ **Data too large** for a single database server.