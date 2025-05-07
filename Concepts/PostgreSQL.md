---
tags:
  - SQL
  - Database
aliases:
  - Postgre
  - Postgre SQL
  - Postgres
---
**PostgreSQL** (often called **Postgres**) is an **open-source, object-relational database management system (ORDBMS)**. It is known for being **feature-rich, extensible, and highly reliable**. It follows the **[[ACID]] (Atomicity, [[Consistency]], Isolation, Durability)** principles, making it a great choice for enterprise-level applications.
## **Key Features of PostgreSQL**

### **1. [[SQL]] Compliance**

- PostgreSQL supports **SQL:2011 standard** with advanced features like **Common Table Expressions (CTEs), Window Functions, and JSONB** for semi-structured data.

### **2. Extensibility**

- You can create **custom data types, operators, functions, and even procedural languages** (PL/pgSQL, PL/Python, PL/Perl, etc.).
- Supports **extensions** like:
    - **PostGIS** (for geospatial data)
    - **pg_partman** (for table partitioning)
    - **TimescaleDB** (for time-series data)

### **3. Performance & Optimization**

- Uses **MVCC (Multi-Version Concurrency Control)** for high-performance transactions.
- Supports **Indexing** (B-tree, Hash, GIN, GiST, and BRIN indexes).
- Has **Parallel Queries** and **Table Partitioning** for handling large datasets.

### **4. JSON & NoSQL Capabilities**

- Supports **JSONB** (binary JSON) and **HStore** (key-value storage).
- Allows hybrid relational and NoSQL-like queries.

### **5. Security**

- **Role-based access control (RBAC)**
- Supports **SSL encryption** for secure data transmission.
- Has advanced **authentication methods** (LDAP, Kerberos, SCRAM-SHA-256, etc.).

### **6. Replication & High Availability**

- Supports **Streaming Replication** and **Logical Replication**.
- Can be set up in **high [[Availability]]** configurations using **Patroni, Pgpool-II, or Bucardo**.

### **7. [[Scalability]]**

- Supports **horizontal and vertical scaling**.
- Works well in **distributed databases** like **Citus**.

## **Use Cases of PostgreSQL**

- **Web Applications:** Used in many large-scale web apps like Instagram, Reddit, and Discord.
- **Enterprise Systems:** Handles transactional workloads in banking, e-commerce, and ERP systems.
- **Data Warehousing:** Supports **OLAP (Online Analytical Processing)** for business intelligence.
- **Geospatial Applications:** Used in GIS applications with **PostGIS**.
- **Machine Learning & AI:** Can store and process large datasets for ML models.

---

## **PostgreSQL vs. [[MySQL]] vs. [[MongoDB]]**

| Feature       | PostgreSQL                     | MySQL                            | MongoDB (NoSQL)                     |
| ------------- | ------------------------------ | -------------------------------- | ----------------------------------- |
| Data Model    | Relational (SQL)               | Relational (SQL)                 | Document-based (NoSQL)              |
| JSON Support  | Yes (JSONB)                    | Limited                          | Native JSON                         |
| Transactions  | Full ACID                      | Full ACID                        | BASE (Eventual Consistency)         |
| Performance   | Optimized for complex queries  | Faster reads, but fewer features | Faster writes, but lacks joins      |
| Extensibility | High (custom types, functions) | Low                              | Medium (plugins)                    |
| Best For      | Complex queries, analytics     | Simple web apps, CMS             | Flexible schemas, high-speed writes |