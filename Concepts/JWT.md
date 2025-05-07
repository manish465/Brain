---
tags:
  - backend
aliases:
  - Jwt Token
---
JSON Web Tokens (JWT) are compact, URL-safe tokens used for securely transmitting information between parties as a JSON object. They are commonly used for [[Authentication]] and information exchange.

The token is mainly composed of header, payload, signature. These three parts are separated by dots(.). JWT defines the structure of information we are sending from one party to the another, and it comes in two forms – Serialized, Deserialized. The Serialized approach is mainly used to transfer the data through the network with each request and response. While the deserialized approach is used to read and write data to the web token.

### Serialized JWT

```
[header].[payload].[signature]
```

```

eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

### ****Deserialized JWT****

```json
header:  
{  
  "alg" : "HS256",  
  "typ" : "JWT"  
}  
  
Payload:  
{  
  "id" : 123456789,  
  "name" : "Joseph"  
}  
  
Secret: GeeksForGeeks
```
