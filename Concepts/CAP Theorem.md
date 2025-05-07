---
tags:
  - HLD
  - interview-prep
---
The **CAP Theorem**, proposed by **Eric Brewer**, states that a distributed database **can only guarantee two out of three properties** at any given time:

1. **[[Consistency]] (C)** – Every read receives the most recent write or an error.
2. **[[Availability]] (A)** – Every request receives a response (it may not be the latest data).
3. **[[Partition Tolerance]] (P)** – The system continues operating despite network failures.

Since network failures **always** happen in a distributed system, partition tolerance (**P**) is mandatory. This means **a system must choose between Consistency (C) and Availability (A)** when a network partition occurs.

## **CAP Theorem in Action**

|Type|Ensures|Sacrifices|Example Databases|
|---|---|---|---|
|**CP (Consistency + Partition Tolerance)**|Ensures strong consistency across nodes|Availability is reduced during network failures|**MongoDB (single-node), HBase, Redis (as a cache)**|
|**AP (Availability + Partition Tolerance)**|Ensures the system remains available|Some nodes may return stale data (eventual consistency)|**Cassandra, DynamoDB, CouchDB**|
|**CA (Consistency + Availability) [Theoretical]**|Ensures consistent and available data|Cannot tolerate network partitions (not possible in distributed systems)|**Traditional RDBMS like PostgreSQL, MySQL (single-node only)**
## **CAP Theorem Takeaway**

- You **CANNOT** have **Consistency, Availability, and Partition Tolerance** **all at once** in a distributed system.
- The choice between **CP vs. AP** depends on your use case.