---
tags:
  - HLD
  - Database
  - interview-prep
---
Replication is the process of **copying and maintaining the same data** across multiple database servers to improve **[[Availability|availability]], [[reliability,]] and read performance**. It ensures that if one database fails, another can take over, minimizing downtime.

### **Why Use Replication?**
1. **High Availability** – If the primary database crashes, a replica can take over.
2. **Improved Read Performance** – Read-heavy applications can distribute queries across multiple replicas.
3. **Fault Tolerance** – Protects against hardware failures.
4. **Disaster Recovery** – Data is backed up across multiple locations.
5. **Geographical Distribution** – Keeps copies of data closer to users for reduced latency.

### **Types of Replication**

1. **Master-Slave Replication (Primary-Replica)**
    - **One primary (master)** database handles all writes.
    - **Multiple replicas (slaves)** handle only read operations.
    - Example:
        - **Write → Master DB**
        - **Read → Replicas**
    - **Use case:** High-read, low-write applications like content-serving platforms.
    
2. **Master-Master Replication (Multi-Primary)**
    - **Multiple masters**, each handling both read and write operations.
    - **Syncing complexity** – Conflict resolution needed when updates happen in different masters.
    - **Use case:** Distributed applications with multiple active databases (e.g., fintech, e-commerce).
    
3. **Synchronous Replication**
    - Data is copied to replicas **immediately** after a write.
    - Ensures **strong consistency** but increases latency.
    - **Use case:** Banking transactions where every copy must be 100% consistent.
    
4. **Asynchronous Replication**
    - The master writes data first, and replication happens **with a delay**.
    - Improves performance but may have **stale data** in replicas.
    - **Use case:** Social media feeds where eventual consistency is acceptable.
    
5. **Geo-Replication**
    - Data is copied to servers in different geographical locations.
    - Reduces **latency** by serving users from the nearest replica.
    - **Use case:** Global applications like Netflix or AWS RDS Multi-Region.