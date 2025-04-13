---
tags:
  - Spring-Boot
---
OkHttp is an efficient HTTP client developed by Square, known for connection pooling, HTTP/2 support, and transparent GZIP compression.

### Maven Dependency

```xml
<dependency>
    <groupId>com.squareup.okhttp3</groupId>
    <artifactId>okhttp</artifactId>
    <version>4.12.0</version>
</dependency>
```

### Example: Synchronous GET Request

```Java
import okhttp3.OkHttpClient;
import okhttp3.Request;
import okhttp3.Response;
import java.io.IOException;

public class OkHttpExample {
    private static final OkHttpClient client = new OkHttpClient();

    public static String getDataFromApi() throws IOException {
        Request request = new Request.Builder()
                .url("https://jsonplaceholder.typicode.com/todos/1")
                .build();

        try (Response response = client.newCall(request).execute()) {
            return response.body() != null ? response.body().string() : null;
        }
    }
}
```

### Example: Synchronous POST Request

```Java
import okhttp3.*;

import java.io.IOException;

public class OkHttpExample {
    private static final OkHttpClient client = new OkHttpClient();

    public static String postDataToApi(String jsonData) throws IOException {
        RequestBody body = RequestBody.create(jsonData, MediaType.get("application/json"));

        Request request = new Request.Builder()
                .url("https://example.com/api")
                .post(body)
                .build();

        try (Response response = client.newCall(request).execute()) {
            return response.body() != null ? response.body().string() : null;
        }
    }
}
```

- **Pros**: Modern, lightweight, and optimized for performance.
- **Cons**: Requires manual configuration for advanced scenarios.