# Two-Tier Application – DevOps Infrastructure Automation

This repository provisions the CI/CD infrastructure for the Two-Tier Flask Application using Infrastructure-as-Code.

---

## 🏗 Provisioned Components

- Docker (Official Docker CE repository)
- Docker Compose v2
- Jenkins (Automated installation)
- Trivy (Container vulnerability scanner)

---

## 🛠 Automation Approach

- Role-based Ansible structure
- Inventory-driven provisioning
- Idempotent playbook execution
- Secure package installation methods

---

## 📂 Project Structure
two-tier-devops-infra/
├── inventory/
├── playbooks/
├── roles/
│ ├── docker/
│ ├── jenkins/
│ └── trivy/
└── ansible.cfg

---

## 🚀 Provision Server
ansible-playbook playbooks/setup-playbook.yml

---

## 🔄 Next Phase

- Jenkins pipeline for Docker build
- Trivy vulnerability scan integration
- Docker Hub image push automation
- Deployment automation
