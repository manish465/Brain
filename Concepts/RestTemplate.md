---
tags:
  - Spring-Boot
---
`RestTemplate` is a synchronous client that waits for the API response before proceeding.
### Example: Making a GET request

```Java
import org.springframework.stereotype.Service;
import org.springframework.web.client.RestTemplate;
import org.springframework.http.ResponseEntity;

@Service
public class ApiService {
    private final RestTemplate restTemplate = new RestTemplate();

    public String getDataFromApi() {
        String url = "https://jsonplaceholder.typicode.com/todos/1";
        ResponseEntity<String> response = restTemplate.getForEntity(url, String.class);
        return response.getBody();
    }
}
```

### Making a POST Request

```Java
import org.springframework.http.HttpEntity;
import org.springframework.http.HttpHeaders;
import org.springframework.http.MediaType;
import org.springframework.web.client.RestTemplate;

@Service
public class ApiService {
    private final RestTemplate restTemplate = new RestTemplate();

    public String postDataToApi(Object requestBody) {
        String url = "https://example.com/api";
        HttpHeaders headers = new HttpHeaders();
        headers.setContentType(MediaType.APPLICATION_JSON);
        
        HttpEntity<Object> request = new HttpEntity<>(requestBody, headers);
        ResponseEntity<String> response = restTemplate.postForEntity(url, request, String.class);
        
        return response.getBody();
    }
}
```

**Spring Boot 2.4+ discourages using `RestTemplate` and recommends [[WebClient]] instead.**