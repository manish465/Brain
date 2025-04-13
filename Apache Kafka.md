---
tags:
  - HLD
aliases:
  - Kafka
---
Apache Kafka is a **distributed event streaming platform** designed to handle large-scale real-time data feeds. It is used for **publish-subscribe messaging**, **event processing**, and **data streaming** across systems.
### **Key Concepts**
1. **Producers** – Send messages (events) to Kafka topics.
2. **Topics** – Logical channels where messages are published.
3. **Partitions** – Topics are split into multiple partitions for scalability.
4. **Brokers** – Kafka servers that store and serve messages.
5. **Consumers** – Read messages from Kafka topics.
6. **Consumer Groups** – Multiple consumers working together to process messages in parallel.
7. **ZooKeeper** (deprecated) – Previously used for cluster management but is being replaced by KRaft.

### **Why Use Kafka?**
- **High Throughput & Low Latency** – Handles millions of messages per second.
- **Scalability** – Supports horizontal scaling by adding more brokers and partitions.
- **Fault Tolerance** – Replicates data across multiple nodes to prevent data loss.
- **Durability** – Stores messages on disk with configurable retention policies.
- **Decoupling of Services** – Enables microservices to communicate asynchronously.

### **Use Cases**
- **Log Aggregation** – Collecting and analyzing logs in real time.
- **Event-Driven Architectures** – Microservices communication.
- **Real-Time Analytics** – Processing streaming data for insights.
- **Data Pipelines** – Moving data between systems like databases, Hadoop, or data lakes.
- **Monitoring & Metrics** – Tracking application performance with real-time events.

Kafka is widely used by companies like LinkedIn, Uber, Netflix, and Airbnb for handling real-time data streams. Since you've worked with **Kafka for asynchronous processing** in your projects, are you looking to implement a specific use case or optimize performance?
## **Kafka vs Other Messaging Systems**

|Feature|Kafka|RabbitMQ|ActiveMQ|
|---|---|---|---|
|**Model**|Publish-Subscribe (Event Streaming)|Message Queue (Brokered Messaging)|Message Queue|
|**Scalability**|**High (Partitioning, Clustering)**|Moderate|Moderate|
|**Persistence**|**Yes** (Log-based retention)|Yes (Queues)|Yes|
|**Performance**|**Very High Throughput**|Moderate|Moderate|
|**Ordering**|**Guaranteed within partitions**|No strict ordering|No strict ordering|
### [[Spring Boot with Kafka]]