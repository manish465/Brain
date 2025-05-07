---
tags:
  - JPA
  - Java
---
JPA (**Java Persistence API**) is a **Java specification** for managing relational data in Java applications. It provides an **abstraction layer** on top of JDBC ([[Java Database Connectivity]]) and ORM ([[Object-Relational Mapping]]) frameworks like **[[Hibernate]]**, **[[EclipseLink]]**, and **OpenJPA**.

JPA allows developers to work with **Java objects** instead of writing raw SQL queries, making database interactions more manageable and maintainable.

## **Why Use JPA?**

1. **Object-Relational Mapping (ORM)** - Maps Java objects (entities) to database tables, reducing the need for manual SQL.
2. **Portability** - Works with different databases without changing code.
3. **Reduces Boilerplate Code** - No need to write explicit `ResultSet` handling like in JDBC.
4. **Supports Transactions & Caching** - Improves performance and ensures data integrity.
5. **Standardized API** - Works across different ORM providers (Hibernate, EclipseLink, etc.).

## **Core JPA Concepts**

### **1. Entity (Database Table Representation)**

An entity is a Java class that represents a table in the database.  
Each instance of the class corresponds to a row in the table.
#### **Example:**
```Java
import jakarta.persistence.*;

@Entity  // Marks this class as a JPA entity
@Table(name = "users")  // Maps to the "users" table
public class User {
    
    @Id  // Primary Key
    @GeneratedValue(strategy = GenerationType.IDENTITY) // Auto-increment
    private Long id;

    @Column(nullable = false, unique = true) // Maps to a column
    private String username;

    @Column(nullable = false)
    private String email;

    // Getters and Setters
}
```

- `@Entity` → Marks the class as a JPA entity.
- `@Table(name = "users")` → Maps the entity to a database table.
- `@Id` → Marks `id` as the primary key.
- `@GeneratedValue(strategy = GenerationType.IDENTITY)` → Auto-generates the ID (database-dependent).
- `@Column(nullable = false, unique = true)` → Defines column constraints.

### **2. Entity Manager (Managing Persistence)**

The **EntityManager** is responsible for managing entities and their persistence lifecycle (CRUD operations).
#### **Example of Using EntityManager:**

```Java
import jakarta.persistence.*;

public class UserDAO {
    private EntityManagerFactory emf = Persistence.createEntityManagerFactory("my-persistence-unit");
    private EntityManager em = emf.createEntityManager();

    public void createUser(String username, String email) {
        User user = new User();
        user.setUsername(username);
        user.setEmail(email);

        em.getTransaction().begin();
        em.persist(user); // Saves user to the database
        em.getTransaction().commit();
    }
}
```

- `EntityManagerFactory` → Creates an `EntityManager` instance.
- `EntityManager` → Manages entity lifecycle (persist, update, remove, find).
- `em.persist(user)` → Saves a new entity to the database.

### **3. JPA Annotations**

| Annotation                                                                                                                 | Description                             |
| -------------------------------------------------------------------------------------------------------------------------- | --------------------------------------- |
| `@Entity`                                                                                                                  | Marks a class as a JPA entity (table).  |
| `@Table(name = "table_name")`                                                                                              | Maps an entity to a specific table.     |
| `@Id`                                                                                                                      | Defines the primary key.                |
| `@GeneratedValue(strategy = GenerationType.IDENTITY)`                                                                      | Auto-generates primary key values.      |
| `@Column(name = "column_name", nullable = false)`                                                                          | Maps a field to a database column.      |
| `@OneToOne`, `@OneToMany`, `@ManyToOne`, `@ManyToMany`                                                                     | Defines relationships between entities. |
| [[PrePersist\|`@PrePersist`]], [[PreUpdate\|`@PreUpdate`]], [[@PostLoad\|`@PostLoad`]], [[@PostPersist\|`@PostPersist`]] | Lifecycle hooks for entity changes.     |
### **4. CRUD Operations with JPA**

Using **Spring Data JPA**, we can simplify CRUD operations using **JpaRepository**.

#### **Example: UserRepository**

```Java
import org.springframework.data.jpa.repository.JpaRepository;

public interface UserRepository extends JpaRepository<User, Long> {
    User findByUsername(String username);
}
```

### **5. Querying Data (JPQL vs. Native SQL)**

JPA provides two ways to query the database:

1. **JPQL (Java Persistence Query Language)** → Object-oriented queries (based on entity class names, not tables).
2. **Native SQL** → Direct SQL queries.
#### **JPQL Example:**

```Java
@Query("SELECT u FROM User u WHERE u.username = :username")
User findByUsername(@Param("username") String username);
```

#### **Native SQL Example:**

```Java
@Query(value = "SELECT * FROM users WHERE username = ?1", nativeQuery = true)
User findByUsername(String username);
```

## **JPA vs Hibernate**

|Feature|JPA (Specification)|Hibernate (Implementation)|
|---|---|---|
|Type|API Specification|ORM Framework|
|Defines|Interfaces and Annotations|Actual implementation|
|Portability|Can work with different ORM providers|Hibernate-specific features|
|Flexibility|Allows switching ORM providers|Tied to Hibernate|

**Example:** JPA is like a "set of rules" for ORM, and Hibernate is an "actual tool" that implements those rules.