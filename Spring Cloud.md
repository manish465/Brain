---
tags:
  - Spring-Cloud
  - Spring-Boot
---
Spring Cloud is a framework that provides tools for building distributed systems and microservices using the Spring Boot ecosystem. It helps developers handle common challenges in microservices architecture, such as service discovery, configuration management, load balancing, and distributed tracing.
### **Key Features of Spring Cloud:**

1. **[[Service Discovery]]** – Uses **[[Eureka]]**, **[[Consul]]**, or **[[Zookeeper]]** to register and locate microservices dynamically.
2. **[[Load Balancing]]** – Uses **[[Spring Cloud LoadBalancer]]** or **[[Ribbon]]** (deprecated) for client-side load balancing.
3. **[[API Gateway]]** – Implements API gateways using **[[Spring Cloud Gateway]]** or **[[Zuul]]** (deprecated).
4. **[[Configuration Management]]** – Uses **[[Spring Cloud Config]]** to store and manage configuration properties centrally.
5. **[[Circuit Breaker & Resilience]]** – Uses **[[Resilience4j]]** (previously Hystrix) to handle failures gracefully.
6. **[[Distributed Tracing & Monitoring]]** – Uses **Spring Cloud Sleuth** and **Zipkin** for logging and tracing requests across services.
7. **[[Event-Driven Communication]]** – Uses **[[Spring Cloud Stream]]** for messaging with [[Apache Kafka|Kafka]] or [[RabbitMQ]].
8. **Security** – Uses **[[Spring Security]]** and **[[OAuth2]]** for [[Authentication]] and [[authorization]] in distributed systems.

### **Why Use Spring Cloud?**

- Simplifies the development of **scalable**, **fault-tolerant**, and **resilient** microservices.
- Reduces boilerplate code by providing **pre-built solutions** for distributed systems.
- Works seamlessly with **Spring Boot**, making it easy to integrate with existing applications.