---
tags:
  - CICD
aliases:
  - Continuous Deployment
---
CD ensures that every code change that passes through CI can be **automatically** deployed to a testing or production environment.

### **Continuous Delivery vs. Continuous Deployment**

|**Aspect**|**Continuous Delivery**|**Continuous Deployment**|
|---|---|---|
|**Definition**|The application is **ready** for deployment but requires manual approval.|Every change that passes tests is **automatically deployed** to production.|
|**Human Intervention**|Manual approval before deployment.|No manual intervention, fully automated.|
|**Use Case**|Suitable for businesses requiring control over releases (e.g., finance, healthcare).|Best for fast-moving applications (e.g., SaaS, startups).|
### **CD Workflow**

1. Code passes CI (build + tests).
2. Code is **packaged** (e.g., Docker container).
3. Code is deployed to **staging** (pre-production).
4. **Manual approval** (in Continuous Delivery) OR direct deployment (in Continuous Deployment).
5. Code is deployed to **production** (live environment).
6. Monitoring and rollback mechanisms are in place.

### **Popular CD Tools**

- ArgoCD
- Spinnaker
- AWS CodeDeploy
- Jenkins X
- Kubernetes + Helm