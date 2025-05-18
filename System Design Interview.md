---
tags:
  - interview-prep
---
A **System Design Interview** is a critical part of many technical job interviews, especially for roles like **backend engineer, software architect, or senior developer**. It evaluates your ability to **design large-scale systems**—like a social media platform, a URL shortener, or an e-commerce website. The focus is less on coding and more on architecture, scalability, and trade-offs.

### What is System Design ?
System design is the **process of defining the architecture, components, modules, interfaces, and data for a system** to satisfy specified requirements. It's about creating the **blueprint** of a software system that is scalable, efficient, and robust.

### What Does the Interview Test ?
The interviewer is evaluating:
- **Scalability**: Can the system handle millions of users?
- **Availability**: Is the system always accessible?
- **Reliability**: Will the system perform correctly under stress or failure?
- **Performance**: Are response times fast? Is latency low?
- **Maintainability**: Is the design modular and easy to update?

### Common Topics Covered
1. **Requirements gathering**
    - Clarify functional (what it should do) and non-functional (scalability, performance) requirements.
2. **High-level design**
    - Draw the system’s architecture: clients, APIs, services, databases, etc.
3. **Detailed component design**
    - Design subsystems like:
        - Load balancers
        - Caching systems
        - Databases (SQL/NoSQL)
        - Messaging queues
        - Authentication/Authorization modules
4. **Database design**
    - Schema design, choosing between SQL vs NoSQL, partitioning, indexing.
5. **Scaling strategies**
    - Vertical vs horizontal scaling
    - Caching (Redis, CDN)
    - Sharding and replication
6. **Trade-offs**
    - Consistency vs availability (CAP theorem)
    - Latency vs throughput
    - SQL vs NoSQL
7. **Bottlenecks and failover**
    - How the system handles failures
    - Disaster recovery plans

### Interview Format
It’s often **45-60 minutes** long, and might look like this:

| Time       | Activity                                        |
| ---------- | ----------------------------------------------- |
| 0-5 mins   | Understand the problem and clarify requirements |
| 5-15 mins  | Define high-level architecture                  |
| 15-30 mins | Dive into individual components                 |
| 30-45 mins | Handle edge cases, scaling, and trade-offs      |
| 45-60 mins | Q&A, bottlenecks, final touches                 |

### Common System Design Interview Questions
- Design **YouTube**
- Design **Twitter**
- Design **Instagram**
- Design a **URL shortener** like bit.ly
- Design a **cache system** like Redis or Memcached
- Design a **chat app** like WhatsApp
- Design **Uber or Lyft** (location tracking + dispatch)
- Design **Google Docs** (real-time collaboration)

### Tips to Ace the Interview
1. **Clarify Requirements**  
    Don’t assume anything. Ask what features to prioritize.
2. **Think Out Loud**  
    Walk through your thought process. Interviewers want to see your reasoning.
3. **Draw Diagrams**  
    Whiteboard or virtual diagrams help visualize the architecture.
4. **Know Your Tools**  
    Be familiar with technologies like:
    - Load balancers (Nginx, HAProxy)
    - Caches (Redis, Memcached)
    - Databases (PostgreSQL, MongoDB)
    - Message queues (Kafka, RabbitMQ)
    - Cloud providers (AWS/GCP/Azure)
5. **Discuss Trade-offs**  
    There’s no perfect design—only well-justified decisions.
6. **Practice**  
    Use platforms like **Excalidraw** for diagrams and sites like **Grokking the System Design Interview**, **System Design Primer (GitHub)** to study.

### Bonus Concepts Worth Knowing
- [[CAP Theorem]] ([[Consistency]], [[Availability]], [[Partition Tolerance]])
- **Latency vs Throughput**
- **Eventual consistency**
- **Distributed systems principles**
- **CDN, DNS, SSL, firewalls**
- **Rate limiting and throttling**
- **Database indexing and denormalization**