---
tags:
  - Spring-Boot
---
`WebClient` from **Spring WebFlux** can be used in a **blocking** (synchronous) way.

### **Example: Synchronous GET Request**

```Java
import org.springframework.stereotype.Service;
import org.springframework.web.reactive.function.client.WebClient;

@Service
public class ApiService {
    private final WebClient webClient = WebClient.create();

    public String getDataFromApi() {
        String url = "https://jsonplaceholder.typicode.com/todos/1";
        return webClient.get()
                .uri(url)
                .retrieve()
                .bodyToMono(String.class)
                .block(); // Blocks and waits for the response (synchronous)
    }
}
```

### Making a POST Request

```Java
import org.springframework.http.MediaType;
import org.springframework.stereotype.Service;
import org.springframework.web.reactive.function.client.WebClient;

@Service
public class ApiService {
    private final WebClient webClient = WebClient.create();

    public String postDataToApi(Object requestBody) {
        String url = "https://example.com/api";
        
        return webClient.post()
                .uri(url)
                .contentType(MediaType.APPLICATION_JSON)
                .bodyValue(requestBody)
                .retrieve()
                .bodyToMono(String.class)
                .block(); // Blocks and waits for response
    }
}
```

- **Use `block()` to make the call synchronous.**
- `WebClient` is the better choice for modern Spring Boot applications because it's more efficient and future-proof.
- If you want **non-blocking/reactive calls**, use `WebClient` without `.block()`.