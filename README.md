# 🚀 CI/CD Pipeline for a Containerized Web Application on AWS

---

# 📌 Project Overview

This project demonstrates a complete **CI/CD pipeline** for deploying a containerized web application on AWS using modern DevOps tools and cloud services.

The application is containerized using Docker, hosted on an AWS EC2 instance, and automatically deployed through GitHub Actions whenever changes are pushed to the main branch.

This project showcases:

* Docker containerization
* Continuous Integration & Continuous Deployment (CI/CD)
* AWS cloud deployment
* Infrastructure automation
* Monitoring and cloud security basics

---

# 🛠️ Technologies Used

## 🔹 DevOps Tools

* GitHub
* Docker
* GitHub Actions

## 🔹 AWS Services

* Amazon EC2
* Elastic Load Balancer (ELB)
* Amazon S3
* AWS IAM
* Amazon CloudWatch

---

# 🏗️ Architecture Diagram

```text
Developer
   │
   ▼
GitHub Repository
   │
   ▼
GitHub Actions CI/CD Pipeline
   │
   ▼
AWS EC2 Instance (Docker Container)
   │
   ▼
Elastic Load Balancer
   │
   ▼
End Users
```

---

# ✨ Features

✅ Dockerized web application

✅ Automated deployment using GitHub Actions

✅ AWS EC2 hosting

✅ CI/CD pipeline implementation

✅ Load balancing support

✅ CloudWatch monitoring integration

✅ IAM role-based permissions

✅ Production-style DevOps workflow

---

# 📂 Project Structure

```text
aws-devops-project/
│
├── .github/
│   └── workflows/
│       └── deploy.yml
│
├── Dockerfile
├── index.html
├── README.md
└── assets/
```

---

# ⚙️ Setup Instructions

## 1️⃣ Clone the Repository

```bash
git clone https://github.com/your-username/aws-devops-project.git
cd aws-devops-project
```

---

## 2️⃣ Build Docker Image

```bash
docker build -t myapp .
```

---

## 3️⃣ Run Docker Container

```bash
docker run -d -p 8080:80 myapp
```

Open in browser:

```text
http://localhost:8080
```

---

# ☁️ AWS Deployment

## EC2 Configuration

* Ubuntu 22.04
* t2.micro (Free Tier)
* Docker installed
* Security Group:

  * Port 22 (SSH)
  * Port 80 (HTTP)

---

# 🔄 CI/CD Workflow

The GitHub Actions pipeline automatically:

1. Detects code changes pushed to `main`
2. Connects to EC2 using SSH
3. Stops old Docker container
4. Builds a new Docker image
5. Deploys updated container

---

# 📜 GitHub Actions Workflow

File Location:

```text
.github/workflows/deploy.yml
```

Example:

```yaml
name: Deploy to EC2

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Deploy to EC2
      uses: appleboy/ssh-action@master
      with:
        host: ${{ secrets.EC2_HOST }}
        username: ubuntu
        key: ${{ secrets.EC2_SSH_KEY }}
        script: |
          docker stop myapp || true
          docker rm myapp || true
          docker build -t myapp .
          docker run -d -p 80:80 --name myapp myapp
```

---

# 🔐 GitHub Secrets

| Secret Name | Description                    |
| ----------- | ------------------------------ |
| EC2_HOST    | Public IP of EC2 instance      |
| EC2_SSH_KEY | Private SSH key (.pem content) |

---

# 📊 Monitoring

Monitoring is implemented using:

* Amazon CloudWatch
* EC2 Metrics
* CPU Utilization Alerts

---

# 📸 Screenshots

## 🔹 GitHub Actions Pipeline

<img width="1416" height="400" alt="image" src="https://github.com/user-attachments/assets/fdf330bf-cb5b-453a-bdbb-76d382255cbc" />


---

## 🔹 AWS CloudWatch

<img width="1920" height="886" alt="Screenshot 2026-05-06 155948" src="https://github.com/user-attachments/assets/b9471b54-c4f4-4687-bda2-a81ddb3be8f2" />


---

## 🔹 Running Web Application

<img width="1917" height="965" alt="Screenshot 2026-05-06 160041" src="https://github.com/user-attachments/assets/9c8c3216-52e7-4df8-ba40-c0ac3c9269de" />



---


# 🚀 Future Improvements

* HTTPS with SSL/TLS
* Docker Compose support
* Kubernetes deployment
* Terraform Infrastructure as Code
* Blue/Green deployment strategy
* Auto Scaling Group integration


# ⭐ Key Learning Outcomes

Through this project, I gained hands-on experience with:

* CI/CD pipeline implementation
* Docker containerization
* AWS cloud deployment
* Infrastructure management
* GitHub Actions automation
* Linux server administration
* Monitoring and logging

---

# 📄 License

This project is licensed under the MIT License.
