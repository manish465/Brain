---
tags:
  - HLD
  - interview-prep
---
**Consistency (C) in the CAP theorem** means that every read operation must return the most recent write operation’s result (or an error if the data is not available yet). This ensures that all nodes in a distributed system **always see the same data** at the same time.

In simpler terms, when a system is consistent, there is no scenario where different nodes return different versions of data.
## **How Consistency Works in Distributed Databases**

1. **Strong Consistency (Immediate Consistency)**
    - After a write operation, all subsequent reads will return the updated value **immediately**.
    - If a node cannot confirm the latest write, it may reject the read request until synchronization is complete.
    - **Example:**
        - In a banking system, if you transfer $500 from Account A to Account B, you expect the transaction to be reflected instantly everywhere.
2. **Eventual Consistency (Weak Consistency)**
    - Data updates propagate **over time**, meaning different nodes might return different results temporarily.
    - After some time, all nodes will eventually converge to the latest data.
    - **Example:**
        - In social media apps, when you update your profile picture, it might take a few seconds or minutes to appear the same across all devices.
3. **Causal Consistency**
    - Ensures that operations that are **logically related** are seen in the correct order.
    - If **event A happened before event B**, all nodes must see **A before B**.
    - **Example:**
        - In an e-commerce system, if a customer adds an item to a cart and then removes it, the system should never show the item again after removal.
4. **Linearizability (Strictest Form of Consistency)**
    - Ensures that all operations appear **as if they were executed in a single sequence**, in **real-time**.
    - No two clients can see different versions of the same data at any time.
    - **Example:**
        - If two users try to book the last seat on a flight, the system should not allow both of them to book it at the same time.
## **How Distributed Systems Maintain Consistency**

1. **[[Replication]] with Strong Consistency**
    - Data is stored on multiple nodes, and updates must be synchronized across all nodes **before** confirming a write.
    - **Method:**
        - **Synchronous Replication:** Ensures that all nodes receive the update before responding.
        - **Drawback:** Slower performance due to waiting for all nodes to sync.
2. **Consensus Protocols**
    - Used to maintain a consistent state across nodes.
    - Examples:
        - **Paxos** (Used in Google Spanner)
        - **Raft** (Used in etcd, Consul, CockroachDB)
        - **Zookeeper’s Zab Protocol** (Used in Kafka, HDFS)
3. **Quorum-Based Approaches**
    - The system ensures that a majority (`N/2 + 1` nodes) agree before confirming a write.
    - Example: **Apache Cassandra** allows configuring read/write consistency levels.
    - Trade-off: Slower than eventual consistency but ensures data integrity.
## **Trade-offs: Why Consistency is Hard in Distributed Systems**

- Enforcing strict consistency requires **synchronization** between nodes, which can **increase latency**.
- In **network partitions**, maintaining strong consistency means **denying requests** until the system recovers (reducing availability).
- Many modern databases choose **eventual consistency** for performance reasons.
## **Final Thoughts: When to Choose Strong vs. Eventual Consistency?**

- **Use Strong Consistency** when **correctness is more important than availability**, such as:
    - Banking & financial transactions.
    - Online booking systems (hotels, airlines).
    - Inventory management (e-commerce with strict stock control).
- **Use Eventual Consistency** when **availability & performance matter more than strict correctness**, such as:
    - Social media feeds (Facebook, Twitter).
    - Content delivery networks (CDN).
    - IoT data collection (sensor logs, analytics).