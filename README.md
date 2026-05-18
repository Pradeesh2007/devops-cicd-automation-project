# 🚀 End-to-End DevOps CI/CD Automation Pipeline

## 📌 Project Overview

This project demonstrates a complete real-world DevOps CI/CD automation pipeline built using multiple Linux servers and industry-standard DevOps tools.

The pipeline automatically builds, tests, containerizes, and deploys a Java Maven application whenever code changes are pushed to GitHub using GitHub Webhooks and Jenkins Pipelines.

The project focuses on:
- Infrastructure Automation
- Continuous Integration & Continuous Deployment (CI/CD)
- Docker Containerization
- Remote Deployment Automation
- DevOps Best Practices

---

# 🏗️ Infrastructure Architecture

```text
                 Developer
                     │
                     ▼
              GitHub Repository
                     │
              (Webhook Trigger)
                     │
                     ▼
               Jenkins Master
                     │
             Trigger Build Job
                     │
                     ▼
               Jenkins Slave
          ┌───────────────────┐
          │ Maven Build       │
          │ Docker Build      │
          │ Docker Run        │
          └───────────────────┘
                     │
                     ▼
              Remote Tomcat
               Deployment
                     │
                     ▼
             Email Notification
```

---

# 🖥️ Infrastructure Setup

| Server | Purpose |
|--------|---------|
| VM1 | Ansible Controller |
| VM2 | Jenkins Master |
| VM3 | Jenkins Slave/Agent |
| VM4 | Apache Tomcat Server |

---

# ⚙️ Technologies Used

## DevOps Tools
- Jenkins
- Ansible
- Docker
- Apache Tomcat
- Maven
- GitHub Webhooks

## Cloud & Infrastructure
- Linux
- SSH
- Bash Scripting

## CI/CD & Automation
- Jenkins Declarative Pipeline
- Infrastructure as Code (IaC)
- Automated Deployment

---

# 🔄 CI/CD Workflow

1. Developer pushes code changes to GitHub
2. GitHub Webhook automatically triggers Jenkins Pipeline
3. Jenkins pulls latest source code
4. Maven builds and packages the application
5. Docker image is built
6. Existing container is stopped and removed
7. New Docker container is deployed
8. WAR file is copied to remote Tomcat server
9. Jenkins sends success/failure email notification

---

# 📂 Project Structure

```bash
devops-cicd-automation-project/
│
├── ansible/
│   ├── install_jenkins.yml
│   ├── install_tomcat.yml
│   ├── install_docker.yml
│   └── inventory
│
├── jenkins/
│   └── Jenkinsfile
│
├── docker/
│   └── Dockerfile
│
├── application/
│   ├── pom.xml
│   └── src/
│
├── screenshots/
│   ├── jenkins-success.png
│   ├── docker-container.png
│   ├── tomcat-deployment.png
│   └── webhook-trigger.png
│
└── README.md
```

---

# 🔧 Jenkins Pipeline Stages

## ✅ Checkout Source Code
Pulls latest source code from GitHub repository.

## ✅ Maven Build
Builds the Java application using Maven.

```bash
mvn clean package -DskipTests
```

## ✅ Verify Artifact
Verifies generated WAR artifact.

## ✅ Docker Build
Builds Docker image for application deployment.

```bash
docker build -t fortask-app:latest .
```

## ✅ Stop Existing Container
Stops and removes old running container.

## ✅ Run Docker Container
Deploys updated Docker container.

```bash
docker run -d -p 8090:8080 fortask-app:latest
```

## ✅ Deploy to Remote Tomcat
Copies WAR artifact to remote Tomcat server using SCP.

## ✅ Email Notification
Sends pipeline success/failure notifications automatically.

---

# 📜 Sample Jenkins Pipeline

```groovy
pipeline {

    agent {
        label 'slave'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Pradeesh2007/fortask.git'
            }
        }

        stage('Build Maven') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t fortask-app:latest .'
            }
        }
    }
}
```

---

# 📸 Screenshots

## Jenkins Pipeline
_Add screenshot here_

## Docker Container Running
_Add screenshot here_

## GitHub Webhook Trigger
_Add screenshot here_

## Tomcat Deployment
_Add screenshot here_

---

# 🚀 How to Run the Project

## Clone Repository

```bash
git clone https://github.com/Pradeesh2007/fortask.git
```

## Build Application

```bash
mvn clean package
```

## Build Docker Image

```bash
docker build -t fortask-app .
```

## Run Docker Container

```bash
docker run -d -p 8090:8080 fortask-app
```

---

# 🔐 Security & Best Practices

- SSH-based remote deployment
- Automated deployment pipeline
- Multi-server architecture
- Infrastructure automation using Ansible
- Environment variable usage inside Jenkins
- Email alert system for monitoring build status

---

# 📈 Future Improvements

- Kubernetes Deployment
- Helm Charts
- SonarQube Integration
- Trivy Security Scanning
- Nexus Artifact Repository
- Prometheus Monitoring
- Grafana Dashboards
- ArgoCD GitOps Deployment

---

# 🎯 Project Outcome

Successfully implemented a fully automated end-to-end DevOps CI/CD pipeline capable of:
- Continuous Integration
- Automated Build & Deployment
- Containerized Application Deployment
- Remote Server Automation
- Infrastructure Provisioning
- Deployment Monitoring & Notifications

---

# 👨‍💻 Author

## PRADEESH KUMAR

### Cloud | DevOps | Cloud Security Enthusiast

- GitHub: https://github.com/Pradeesh2007
- LinkedIn: https://www.linkedin.com/in/pradeesh-the-clouder

---

# ⭐ If you found this project useful, give it a star!
