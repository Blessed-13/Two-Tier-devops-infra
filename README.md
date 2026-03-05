# Two-Tier Application – DevOps Infrastructure Automation

This repository provisions the **CI/CD infrastructure** for the Two-Tier Flask Application using **Infrastructure-as-Code (IaC)** with Ansible.

It sets up a complete DevOps environment including Jenkins, Docker, and Trivy to support automated build, security scanning, and deployment workflows.

---

## 🏗 Provisioned Components

This infrastructure automatically installs and configures:

- **Docker (Official Docker CE repository)**
- **Docker Compose v2**
- **Jenkins (CI/CD Server)**
- **Trivy (Container Vulnerability Scanner)**

The infrastructure is deployed on a **dedicated Jenkins EC2 instance**, while the application runs on a **separate EC2 server**, ensuring proper separation of CI and runtime environments.

---

## 🛠 Automation Approach

Infrastructure is provisioned using:

- Role-based **Ansible architecture**
- **Inventory-driven provisioning**
- **Idempotent playbook execution**
- Secure package installation methods
- Modular infrastructure roles for maintainability

---

## 📂 Project Structure

```
two-tier-devops-infra/
├── inventory/
│   └── inventory
├── playbooks/
│   ├── setup-playbook.yml
│   └── deploy.yml
├── roles/
│   ├── docker/
│   ├── jenkins/
│   └── trivy/
├── ansible.cfg
└── Jenkinsfile
```

---

## 🚀 Provision Infrastructure

Run the following command to configure the Jenkins server:

```bash
ansible-playbook -i inventory playbooks/setup-playbook.yml
```

This will automatically install:

- Docker
- Docker Compose
- Jenkins
- Trivy

---

## ⚙ CI/CD Pipeline Architecture

A complete **automated CI/CD pipeline** has been implemented using Jenkins.

### Pipeline Stages

1. **Code Checkout** – Pulls application source from GitHub  
2. **Docker Build** – Builds application Docker image  
3. **Trivy Security Scan** – Scans image for vulnerabilities  
4. **DockerHub Push** – Pushes image to container registry  
5. **Infrastructure Repo Checkout** – Retrieves deployment automation  
6. **Ansible Deployment** – Updates containers on the application server  

---

## 🔄 CI/CD Workflow

```
GitHub Push
      ↓
GitHub Webhook
      ↓
Jenkins Pipeline
      ↓
Docker Image Build
      ↓
Trivy Security Scan
      ↓
DockerHub Image Push
      ↓
Ansible Deployment
      ↓
Application EC2 Updates Containers
```

This pipeline enables **fully automated deployment without manual SSH access**.

---

## 🏗 Infrastructure Architecture

```
           GitHub
              │
              ▼
         Jenkins EC2
     (CI/CD + Security Scan)
              │
              ▼
        DockerHub Registry
              │
              ▼
       Application EC2
   (Docker Compose Deployment)
```

- **Jenkins Server** → Builds, scans, and pushes images  
- **Application Server** → Pulls latest image and restarts containers  
- **Ansible** → Automates infrastructure configuration and deployment  

---

## 🔐 Security Integration

Security is integrated into the pipeline using **Trivy** to perform container image vulnerability scanning before deployment.

This helps identify:

- Critical vulnerabilities
- High-risk dependencies
- Security misconfigurations

---

## 📌 Key DevOps Concepts Implemented

- Infrastructure as Code (Ansible)
- CI/CD Pipeline Automation (Jenkins)
- Containerization (Docker)
- Container Security (Trivy)
- Multi-repository DevOps workflow
- Automated deployment pipelines
- GitHub Webhook integration
- Separation of CI and runtime environments

---

## 🔄 Future Improvements

Next enhancements planned:

- Kubernetes-based deployment
- Helm chart packaging
- GitOps deployment using **ArgoCD**
- Code quality analysis using **SonarQube**
- Versioned image tagging strategy
- Production monitoring (Prometheus + Grafana)
