---
tags:
  - Database
---
SQL (**Structured Query Language**) is a standard language used to interact with **relational databases**. It enables users to **store, retrieve, manipulate, and manage** data efficiently.
### **Key Features of SQL**
1. **Declarative Language** – You specify _what_ you want, and the database engine decides _how_ to execute it.
2. **Standardized** – Used by most relational databases like [[MySQL]], [[PostgreSQL|Postgre SQL]], SQL Server, and Oracle.
3. **Powerful Data Handling** – Supports [[CRUD operations]] (Create, Read, Update, Delete).
4. **Supports Transactions** – Ensures **[[ACID]]** (Atomicity, Consistency, Isolation, Durability) compliance.
5. **Security Features** – Includes user [[authentication]], role-based access, and [[encryption]].

### **SQL Commands (Types)**

SQL commands are categorized into different groups:

6. **DDL (Data Definition Language) – Defines Structure**
    - `CREATE` – Creates tables, schemas, indexes, etc.
    - `ALTER` – Modifies database structures.
    - `DROP` – Deletes tables, databases, or schemas.
    - `TRUNCATE` – Deletes all records but keeps the structure.
7. **DML (Data Manipulation Language) – Modifies Data**
    - `INSERT` – Adds records.
    - `UPDATE` – Modifies existing records.
    - `DELETE` – Removes records.
8. **DQL (Data Query Language) – Retrieves Data**
    - `SELECT` – Fetches data from tables.
9. **DCL (Data Control Language) – Controls Access**
    - `GRANT` – Gives user permissions.
    - `REVOKE` – Removes user permissions.
10. **TCL (Transaction Control Language) – Manages Transactions**
    - `COMMIT` – Saves all changes permanently.
    - `ROLLBACK` – Undoes changes before a commit.
    - `SAVEPOINT` – Creates a temporary rollback point.
### **Example SQL Queries**

#### **1. Create a Table**
```SQL
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    salary DECIMAL(10,2),
    department VARCHAR(30)
);
```

#### **2. Insert Data**
```SQL
INSERT INTO employees (id, name, salary, department) 
VALUES (1, 'John Doe', 60000, 'IT');
```

#### **3. Retrieve Data**
```SQL
SELECT * FROM employees WHERE department = 'IT';
```

#### **4. Update Data**
```SQL
UPDATE employees 
SET salary = 65000 
WHERE id = 1;
```

#### **5. Delete Data**
```SQL
DELETE FROM employees WHERE id = 1;
```

### **Why Use SQL?**
- **Efficient Data Management** – Handles large-scale databases.
- **Data Integrity** – Ensures accurate and consistent data storage.
- **Flexibility** – Supports complex queries and joins.
- **Scalability** – Used in small applications to enterprise-level systems.