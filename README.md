📘 README.md (FINAL VERSION)
🚀 Major Project: End-to-End CI/CD Pipeline using Jenkins, Docker & Terraform
🔧 Tech Stack

AWS EC2

Terraform

Jenkins

Docker

GitHub

Linux (Ubuntu)

📌 Project Overview

This project demonstrates a real-world end-to-end CI/CD pipeline where infrastructure provisioning, application build, and deployment are fully automated using DevOps tools.

The pipeline provisions infrastructure using Terraform, builds Docker images using Jenkins, and deploys the application automatically to an EC2 server.

🏗️ Architecture
GitHub
   ↓
Jenkins (CI)
   ↓
Docker Image Build
   ↓
SSH
   ↓
Application EC2 (Docker Container)


Infrastructure (EC2 instances and Security Group) is provisioned using Terraform.

🛠️ Infrastructure Setup (Terraform)

Using Terraform, the following resources were created:

2 EC2 instances:

Jenkins Server

Application Server

Security Group:

SSH access (22)

Application access (8080)

Terraform Files Used:

main.tf

variables.tf

terraform.tfvars

outputs.tf

Terraform ensures idempotent infrastructure creation.

⚙️ Server Configuration
Jenkins Server:

Java installed (required for Jenkins)

Jenkins installed

Docker installed

Jenkins user added to Docker group

Application Server:

Docker installed

Used only to run the application container

📂 Application & Pipeline Files

The following files are stored in this GitHub repository:

index.html – Sample application

Dockerfile – Builds Docker image using Nginx

Jenkinsfile – Defines CI/CD pipeline stages

🔐 SSH Configuration

SSH key generated on Jenkins server

Public key added to authorized_keys on Application server

Enabled passwordless SSH for automated deployments

🔄 CI/CD Pipeline Flow
Continuous Integration (CI):

Jenkins pulls code from GitHub

Builds Docker image using Dockerfile

Continuous Deployment (CD):

Jenkins connects to Application server via SSH

Stops existing container (if any)

Runs a new Docker container on port 8080

🌐 Application Access

After successful pipeline execution, the application is accessible via browser:

http://<APPLICATION_SERVER_PUBLIC_IP>:8080

🧠 Key DevOps Concepts Demonstrated

Infrastructure as Code (Terraform)

CI/CD automation using Jenkins

Docker image creation and containerization

Secure SSH-based deployment

Idempotency and automation best practices

✅ Outcome

Fully automated CI/CD pipeline

No manual deployment steps

Production-style DevOps workflow implemented

📌 Author

Sabiha Noor
Aspiring DevOps Engineer
