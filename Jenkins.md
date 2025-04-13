---
tags:
  - CICD
---
Jenkins is one of the most popular open-source automation tools used for **[[Continuous Integration]] (CI) and [[Continuous Deployment]] (CD)**. It enables developers to build, test, and deploy software automatically, reducing manual effort and increasing efficiency.

## **Key Features of Jenkins**

- **Open Source** – Free to use, with a strong community.
- **Extensible** – Over **1,800+ plugins** available for integration.
- **Cross-Platform** – Runs on **Windows, Linux, macOS**.
- **Scalability** – Supports **distributed builds** via master-slave architecture.
- **Integration Support** – Works with **Git, Docker, Kubernetes, AWS, and more**.
- **Pipeline as Code** – Enables **declarative pipelines** using Groovy.

## **How Jenkins Works**

Jenkins automates software delivery by running a **CI/CD pipeline** that includes:

1. **Code Commit** – Developers push code to a repository (**GitHub, GitLab, Bitbucket**).
2. **Build** – Jenkins compiles the code using **Maven, Gradle, or Ant**.
3. **Test** – Runs **unit tests, integration tests, and UI tests**.
4. **Package** – Produces an **artifact** (JAR, WAR, Docker image).
5. **Deploy** – Deploys the application to **staging/production**.
6. **Monitoring** – Jenkins integrates with monitoring tools (e.g., Prometheus, Grafana).

## **Jenkins Architecture**

Jenkins follows a **master-agent** architecture for distributed builds.

- **Jenkins Master** – Controls the pipeline, schedules jobs, and manages plugins.
- **Jenkins Agent** – Executes tasks like building, testing, and deploying.

## **Jenkins Pipeline (Declarative vs. Scripted)**

### **Declarative Pipeline (Recommended)**

A structured, easy-to-read syntax for defining CI/CD steps.

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
        stage('Test') {
            steps {
                sh './mvnw test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'scp target/app.jar user@server:/deploy/'
            }
        }
    }
}
```

### **Scripted Pipeline**

A flexible, Groovy-based pipeline for complex workflows.

```groovy
node {
    stage('Checkout') {
        git 'https://github.com/user/repository.git'
    }
    stage('Build') {
        sh './mvnw clean package'
    }
    stage('Test') {
        sh './mvnw test'
    }
    stage('Deploy') {
        sh 'scp target/app.jar user@server:/deploy/'
    }
}
```

## **Jenkins vs. Other CI/CD Tools**

| Feature           | Jenkins | GitHub Actions | GitLab CI/CD | CircleCI | TravisCI |
| ----------------- | ------- | -------------- | ------------ | -------- | -------- |
| **Open Source**   | ✅ Yes   | ✅ Yes          | ✅ Yes        | ❌ No     | ❌ No     |
| **Self-Hosted**   | ✅ Yes   | ❌ No           | ✅ Yes        | ❌ No     | ❌ No     |
| **Plugin System** | ✅ Yes   | ✅ Limited      | ❌ No         | ❌ No     | ❌ No     |
| **Cloud Support** | ✅ Yes   | ✅ Yes          | ✅ Yes        | ✅ Yes    | ✅ Yes    |
| **Ease of Use**   | Medium  | Easy           | Medium       | Easy     | Easy     |
