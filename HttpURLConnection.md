---
tags:
  - Spring-Boot
---
Java's built-in `HttpURLConnection` is available without any external dependencies but lacks modern features like connection pooling and compression.

```Java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.net.HttpURLConnection;
import java.net.URL;

public class HttpURLConnectionExample {
    public static String getDataFromApi() throws Exception {
        URL url = new URL("https://jsonplaceholder.typicode.com/todos/1");
        HttpURLConnection con = (HttpURLConnection) url.openConnection();
        con.setRequestMethod("GET");

        BufferedReader in = new BufferedReader(new InputStreamReader(con.getInputStream()));
        String inputLine;
        StringBuilder content = new StringBuilder();
        while ((inputLine = in.readLine()) != null) {
            content.append(inputLine);
        }
        in.close();
        con.disconnect();
        return content.toString();
    }
}
```

- **Pros**: No external dependencies, built-in in Java.
- **Cons**: Lacks features like automatic retries, connection pooling, and async handling.