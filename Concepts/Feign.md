---
tags:
  - Spring-Boot
  - Spring-Cloud
---
A declarative HTTP client from Netflix that is now part of the **[[Spring Cloud]]** ecosystem. **Feign simplifies API calls** by allowing you to define interfaces that automatically generate REST clients, reducing boilerplate code.

### Maven Dependency

```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-openfeign</artifactId>
    <version>4.1.0</version> <!-- Check for the latest version -->
</dependency>
```

### Enable Feign in Spring Boot
Add @EnableFeignClients to your main class:

```Java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.openfeign.EnableFeignClients;

@SpringBootApplication
@EnableFeignClients // Enables Feign Clients
public class FeignExampleApplication {
    public static void main(String[] args) {
        SpringApplication.run(FeignExampleApplication.class, args);
    }
}
```

### Example: Making a GET Request
Instead of using `RestTemplate` or `WebClient`, Feign allows you to **define an interface** for API calls.

```Java
import org.springframework.cloud.openfeign.FeignClient;
import org.springframework.web.bind.annotation.GetMapping;

@FeignClient(name = "jsonPlaceholderClient", url = "https://jsonplaceholder.typicode.com")
public interface JsonPlaceholderClient {
    
    @GetMapping("/todos/1")
    String getTodo();
}
```

Feign will automatically create the implementation for this interface

### Calling the Feign Client

```Java
import org.springframework.stereotype.Service;

@Service
public class ApiService {
    private final JsonPlaceholderClient jsonPlaceholderClient;

    public ApiService(JsonPlaceholderClient jsonPlaceholderClient) {
        this.jsonPlaceholderClient = jsonPlaceholderClient;
    }

    public String fetchTodo() {
        return jsonPlaceholderClient.getTodo();
    }
}
```

### Feign Client for POST Request

```Java
public class PostRequest {
    private String title;
    private String body;
    private int userId;

    // Constructors, Getters, and Setters
}
```

```Java
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.cloud.openfeign.FeignClient;

@FeignClient(name = "jsonPlaceholderClient", url = "https://jsonplaceholder.typicode.com")
public interface JsonPlaceholderClient {

    @PostMapping("/posts")
    String createPost(@RequestBody PostRequest request);
}
```

```Java
import org.springframework.stereotype.Service;

@Service
public class ApiService {
    private final JsonPlaceholderClient jsonPlaceholderClient;

    public ApiService(JsonPlaceholderClient jsonPlaceholderClient) {
        this.jsonPlaceholderClient = jsonPlaceholderClient;
    }

    public String createPost() {
        PostRequest request = new PostRequest();
        request.setTitle("New Post");
        request.setBody("This is a test post");
        request.setUserId(1);

        return jsonPlaceholderClient.createPost(request);
    }
}
```

### Handling Headers & Authentication in Feign

```Java
import org.springframework.web.bind.annotation.RequestHeader;

@FeignClient(name = "apiClient", url = "https://example.com")
public interface ApiClient {

    @GetMapping("/data")
    String getData(@RequestHeader("Authorization") String token);
}
```

```Java
public String fetchData() {
    return apiClient.getData("Bearer my-jwt-token");
}
```

### Handling Feign Exceptions (Resilience4j / Retry)
Feign doesn't handle failures by default, so you should configure **error handling**.

```Java
import feign.Response;
import feign.codec.ErrorDecoder;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class FeignConfig {
    @Bean
    public ErrorDecoder errorDecoder() {
        return new CustomErrorDecoder();
    }
}

class CustomErrorDecoder implements ErrorDecoder {
    @Override
    public Exception decode(String methodKey, Response response) {
        switch (response.status()) {
            case 400:
                return new RuntimeException("Bad Request");
            case 404:
                return new RuntimeException("Not Found");
            default:
                return new RuntimeException("Server Error");
        }
    }
}
```

Then, apply the config in the Feign client:

```Java
@FeignClient(name = "apiClient", url = "https://example.com", configuration = FeignConfig.class)
public interface ApiClient {
    @GetMapping("/data")
    String getData();
}
```

## **Why Use Feign?**

|Feature|Feign|RestTemplate|WebClient|
|---|---|---|---|
|Simplicity|✅ Easy|❌ More boilerplate|❌ Requires manual setup|
|Declarative API|✅ Yes|❌ No|❌ No|
|Load Balancing|✅ Yes (with Ribbon)|❌ No|❌ No|
|Async Support|❌ No|❌ No|✅ Yes (when non-blocking)|

### **When to Use Feign?**

- ✅ When working with **microservices** (Spring Cloud Netflix).
- ✅ When you need **simple and declarative HTTP calls**.
- ✅ When you want **automatic retries and resilience**.