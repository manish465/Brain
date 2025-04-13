---
tags:
  - HLD
  - Distributed-locks
aliases:
  - Distributed Locking
---
Distributed locks are a very useful primitive in many environments where different processes must operate with shared resources in a mutually exclusive way.

There are a number of libraries and blog posts describing how to implement a DLM ([[Distributed Lock Manager]]) with Redis, but every library uses a different approach, and many use a simple approach with lower guarantees compared to what can be achieved with slightly more complex designs.