---
tags:
  - Database
  - NoSQL
---
**MongoDB** is a **[[NoSQL]] database** that stores data in a **flexible, [[JSON]]-like format** called **BSON ([[Binary JSON]])**. Unlike relational databases (like PostgreSQL or MySQL), MongoDB does **not use tables and rows**—instead, it uses **collections and documents**, making it highly scalable and efficient for modern applications.
## **Key Features of MongoDB**

### **1. NoSQL & Schema Flexibility**

- **Document-oriented**: Stores data as **key-value pairs** in BSON format.
- **Schema-less**: No fixed structure—each document can have different fields.

### **2. High Performance & Scalability**

- **[[Sharding]]:** Distributes large datasets across multiple servers.
- **[[Replication]]:** Ensures **high availability** by replicating data across nodes.
- **[[Indexing]]:** Supports various index types (single-field, compound, text, geospatial).

### **3. Powerful Query Language**

- Supports **[[CRUD operations]] (Create, Read, Update, Delete)**.
- Has **[[aggregation framework]]** (like SQL GROUP BY but more powerful).
- Allows **geospatial queries** (useful for location-based applications).

### **4. Horizontal Scaling**

- Uses **[[Sharding]]** to split large datasets across multiple servers.
- Ideal for handling **big data** and high-traffic applications.

### **5. Replication & High [[Availability]]**

- **Replica Sets** keep copies of data across multiple servers.
- Automatic **failover** ensures uptime.

### **6. JSON-like Storage (BSON)**

- Similar to JSON, but supports additional data types like **date, binary, and decimal128**.
## **Use Cases of MongoDB**

- **Real-time Applications:** Chat apps, streaming platforms.
- **Big Data & Analytics:** IoT, logging, machine learning data storage.
- **E-Commerce & Catalogs:** Stores dynamic product information.
- **Content Management Systems (CMS):** Handles unstructured data efficiently.
## **MongoDB vs. [[PostgreSQL]] vs. [[MySQL]]**

|Feature|MongoDB (NoSQL)|PostgreSQL (SQL)|MySQL (SQL)|
|---|---|---|---|
|Data Model|Document (BSON)|Relational (Tables)|Relational (Tables)|
|Schema|Flexible (No Schema)|Fixed Schema|Fixed Schema|
|Query Language|JSON-based Queries|SQL|SQL|
|Transactions|**BASE** (Eventual Consistency)|**ACID**|**ACID**|
|Scalability|Horizontal (Sharding)|Vertical & Horizontal|Vertical Scaling|
|Best For|Unstructured Data, Real-time Apps|Complex Queries, Analytics|Simple Web Apps|
