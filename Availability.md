---
tags:
  - HLD
  - interview-prep
aliases:
  - availability
---
**Availability (A) in the CAP theorem** means that every request to the system receives a response, even if some nodes are down or experiencing network issues.

In simple terms:
- The system **must not reject or delay requests** unnecessarily.
- Even if some parts of the system fail, it **must still serve requests with the available data**.
- The system may **return stale (old) or incomplete data** but will **never fail to respond**.

## **How Availability Works in Distributed Databases**

1. **High Availability (HA)**
    - Ensures that the system **remains operational at all times**.
    - Even if some nodes fail, others should continue to handle requests.
    - Uses **replication and failover mechanisms**.
2. **Eventual vs. Immediate Availability**
    - **Immediate Availability:** The system responds instantly with whatever data it has.
    - **Eventual Availability:** The system might temporarily delay responses if it’s trying to recover from failures.
3. **Availability During Network Partitions**
    - When a network failure occurs, available nodes must **continue serving requests**.
    - This may lead to **temporary inconsistencies** until the network recovers.
## **How Distributed Systems Achieve Availability**

1. **[[Replication]] (Multiple Copies of Data)**
    - Data is stored across **multiple nodes**, so if one fails, another can handle requests.
    - **Example:**
        - Apache Cassandra and DynamoDB store **multiple copies** of data across nodes to ensure availability.
2. **[[Load Balancing]]**
    - Distributes requests among multiple servers to **prevent overloading**.
    - **Example:**
        - Web applications use **NGINX, HAProxy, or AWS Load Balancer** to route traffic efficiently.
3. **Automatic Failover**
    - If a database node fails, another node **takes over automatically**.
    - **Example:**
        - PostgreSQL supports **Patroni-based failover**, where if a primary node crashes, a replica takes its place.
4. **[[Sharding]] (Data Distribution Across Nodes)**
    - Large datasets are divided into smaller **shards** to distribute the load.
    - If one shard is unavailable, others **can still serve requests**.
    - **Example:**
        - **MongoDB sharding** allows horizontal scaling to maintain availability.
5. **Eventually Consistent Reads**
    - In AP systems (Availability + Partition Tolerance), if the latest data isn’t available, the system may return an older version.
    - **Example:**
        - **Cassandra** allows “read repair,” where nodes sync data asynchronously after serving older data.
## **Trade-offs: Why is Availability Hard in Distributed Systems?**

- To **maximize availability**, systems may return **stale or inconsistent data**.
- **High availability** often requires **relaxing consistency** (leading to eventual consistency).
- Maintaining **100% uptime** is expensive and complex.
## **Final Thoughts: When to Choose Availability Over Consistency?**

- **Use High Availability (AP systems)** when **uptime matters more than strict consistency**, such as:
    - Social media feeds (Facebook, Twitter).
    - E-commerce product listings (Amazon, Flipkart).
    - Streaming services (Netflix, YouTube).
    - IoT data collection (temperature sensors, fleet tracking).
- **Use Strong Consistency (CP systems) if correctness is more important than availability**, such as:
    - Banking transactions.
    - Online ticket booking.
    - Inventory management.