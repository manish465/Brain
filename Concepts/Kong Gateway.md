---
tags:
  - Gateway
  - backend
---
Kong Gateway is an API gateway and service mesh designed to manage, secure, and optimize API traffic. It's built on **NGINX and Lua**, making it lightweight and highly performant. It supports **plugins for [[Authentication]], [[rate limiting]], [[logging]], and [[monitoring]]**, and can be deployed in **hybrid, multi-cloud, and [[Kubernetes]] environments**.

### **Key Features**

1. **API Gateway** – Routes and processes API traffic efficiently.
2. **Security** – Supports authentication (JWT, OAuth2), request validation, and traffic encryption.
3. **Rate Limiting** – Controls request rates to prevent abuse.
4. **Load Balancing** – Distributes traffic across backend services.
5. **Logging & Monitoring** – Integrates with Prometheus, Grafana, ELK stack, etc.
6. **Extensibility** – Plugins allow customization for different needs.
7. **Kubernetes & Service Mesh** – Can act as a control plane in a microservices environment.

### **Deployment Options**

- **Self-Hosted** – Can be installed using Docker, Kubernetes, or bare metal.
- **Kong Konnect** – Cloud-based API management.
- **Enterprise Edition** – Offers additional security, analytics, and governance features.

### **Use Cases**

- API management in microservices.
- Secure API traffic with authentication and authorization.
- Implement rate limiting and load balancing.
- Monitor API usage and performance.