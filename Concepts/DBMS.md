---
tags:
  - Database
---
**DBMS (Database Management System)** is software that **manages databases**.  
It **lets you create, store, retrieve, update, and delete data** without having to manually deal with the messy low-level details like file management.

At its core, a DBMS does **four things**:
- **CRUD** operations (Create, Read, Update, Delete data)
- **Security and access control** (who can do what)
- **Data integrity** (keeping the data consistent and correct)
- **Data concurrency** (letting multiple users access data at the same time without screwing things up)

Examples
- **[[MySQL]]**, **[[PostgreSQL]]**, **OracleDB**, **[[MongoDB]]** (for [[NoSQL]])

Without a DBMS, you'd be basically hacking data into text files and hoping they don't get corrupted.

**Under the hood**, a DBMS handles:
- **Storage engines** (where data physically sits)
- **Query processing** (turning SQL into low-level operations)
- **Transaction management** (making sure operations happen fully or not at all — think bank transfers)
- **Indexing** (speeding up search operations)