---
tags:
  - HLD
  - interview-prep
---
**Partition Tolerance (P) in the CAP theorem** means that the system continues to function **even if network failures (partitions) occur**

In simple terms:
- A **network partition** occurs when nodes in a distributed system **cannot communicate** with each other due to network failures.
- A **partition-tolerant system** ensures that **even if some nodes cannot talk to others, the system keeps working** (possibly with degraded performance).
- Since network failures **are inevitable**, distributed databases **must** choose partition tolerance **(P) along with either [[Consistency]] (C) or [[Availability]] (A)**.
## **How Do Network Partitions Happen?**

Network partitions can happen due to:
1. **Hardware Failures** – A server goes offline due to power loss.
2. **Network Congestion** – High traffic causes delays or message loss.
3. **Geo-distributed Systems** – Data centers in different locations lose connectivity.
4. **Cloud Network Issues** – AWS, Google Cloud, or Azure may experience regional outages.
5. **Load Balancer Failures** – A misconfigured load balancer may drop requests between nodes.

When a network partition occurs, nodes **cannot synchronize** properly, causing a split-brain situation where different parts of the system **see different data versions**.

## **How Distributed Systems Handle Partition Tolerance**

Partition Tolerance means that when a network partition happens, the system must **make a trade-off** between **Consistency (CP) and Availability (AP)**.

### **1. CP Systems (Consistency + Partition Tolerance)**

- **Ensures data correctness but sacrifices availability** during a partition.
- If nodes cannot synchronize, some requests may be **rejected or delayed** until the network is restored.
- **Example:**
    - A **banking system** must prevent duplicate transactions. If a partition occurs, it may **pause transactions** instead of allowing inconsistent data.

#### **How CP Systems Work:**

- **Data Locking** – The system prevents conflicting writes.
- **Leader Election** – Only one node processes writes, while others wait.
- **Consensus Algorithms** – Uses **Paxos** or **Raft** to synchronize nodes after a failure.

**Examples of CP Databases:**

|Database|How It Handles Partitions|
|---|---|
|**MongoDB (single-node mode)**|Waits for nodes to sync, rejecting requests if needed.|
|**HBase**|Uses strong consistency but may refuse writes during failures.|
|**Zookeeper**|Uses leader-based consensus (Paxos/Raft) to ensure correctness.|

---

### **2. AP Systems (Availability + Partition Tolerance)**

- **Prioritizes uptime over strict consistency** during a partition.
- Nodes continue serving requests even if they have **different versions of data** (eventual consistency).
- **Example:**
    - A **social media feed** like Twitter keeps showing tweets even if the latest likes/comments aren't synced across all nodes.

#### **How AP Systems Work:**

- **Eventually Consistent Reads** – Nodes sync later using **background processes**.
- **Conflict Resolution** – Uses **timestamps** or **vector clocks** to merge data.
- **Multiple Leaders** – Any node can accept writes, even during partitions.

**Examples of AP Databases:**

|Database|How It Handles Partitions|
|---|---|
|**Apache Cassandra**|Allows writes to any node, resolving conflicts later.|
|**DynamoDB**|Uses vector clocks to merge updates.|
|**CouchDB**|Uses multi-version concurrency control (MVCC) for updates.|

---

## **Trade-offs: Why Partition Tolerance is Unavoidable?**

- **Distributed databases span multiple locations**, making network failures inevitable.
- **Global applications (Netflix, Amazon, Google)** must stay online, even if some nodes go down.
- **Choosing CP or AP depends on the business need** (financial systems prioritize CP, while real-time apps favor AP).