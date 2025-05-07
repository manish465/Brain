---
tags:
  - JPA
  - Java
  - Spring-Boot
---
Spring Data JPA is a part of the **Spring Data** project that simplifies **database interactions** in Java applications using **JPA ([[Java Persistence API]])**.

### **Key Features of Spring Data JPA**

- **Eliminates boilerplate code** for common database operations (e.g., `findById`, `save`, `delete`).
- Uses **JpaRepository** to abstract SQL queries.
- Supports **JPQL (Java Persistence Query Language)** and **native queries**.
- Provides **pagination and sorting** out-of-the-box.
- Works with **Hibernate** as the default JPA provider.

### **Example: Using Spring Data JPA**

#### **Step 1: Add Dependencies (Maven)**

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
    <groupId>com.h2database</groupId>  <!-- Replace with MySQL or PostgreSQL if needed -->
    <artifactId>h2</artifactId>
    <scope>runtime</scope>
</dependency>
```

#### **Step 2: Define the Entity**

```Java
import jakarta.persistence.*;

@Entity
@Table(name = "users")
public class User {
    
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false, unique = true)
    private String username;

    @Column(nullable = false)
    private String email;

    // Getters and Setters
}
```

#### **Step 3: Create a Repository Interface**

```Java
import org.springframework.data.jpa.repository.JpaRepository;

public interface UserRepository extends JpaRepository<User, Long> {
    User findByUsername(String username);
}
```

- This **automatically** generates CRUD methods (no need to write SQL queries!).
- The method `findByUsername(String username)` will be converted into a SQL query by Spring.

```Java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class UserService {
    
    @Autowired
    private UserRepository userRepository;

    public User saveUser(User user) {
        return userRepository.save(user); // Save user to DB
    }

    public User getUserByUsername(String username) {
        return userRepository.findByUsername(username); // Fetch user by username
    }
}
```