Brain Tasks App – DevOps CI/CD Deployment

A complete DevOps CI/CD pipeline that automatically builds, containerizes, and deploys a web application to Kubernetes using AWS services.

This project demonstrates modern cloud-native deployment practices using Docker, Kubernetes, and AWS DevOps tools.

📌 Project Overview

The pipeline automatically performs the following steps:

Source code pushed to GitHub

Pipeline triggered automatically

Application built using Docker

Image pushed to container registry

Application deployed to Kubernetes cluster

This provides a fully automated CI/CD workflow for application delivery.

🏗️ Architecture Diagram
             Developer
                │
                │ Push Code
                ▼
            GitHub Repo
                │
                │ Source Stage
                ▼
        AWS CodePipeline
                │
                ▼
        AWS CodeBuild
                │
        Build Docker Image
                │
                ▼
      Amazon ECR (Image Repo)
                │
                ▼
     Amazon EKS (Kubernetes)
                │
                ▼
           Kubernetes
        Deployment + Service
                │
                ▼
            Web Application
⚙️ Tech Stack
Technology	Purpose
GitHub	Source code repository
AWS CodePipeline	CI/CD pipeline orchestration
AWS CodeBuild	Application build automation
Docker	Containerization
Amazon ECR	Container image registry
Amazon EKS	Kubernetes cluster
kubectl	Kubernetes deployment management
📂 Project Structure
brain-app-project
│
├── Dockerfile
├── buildspec.yml
├── deployment.yaml
├── service.yaml
├── dist/
├── aws/
└── README.md
🚀 CI/CD Pipeline Workflow
1️⃣ Source Stage

Code is stored in GitHub

Pipeline automatically triggers on new commits

2️⃣ Build Stage

AWS CodeBuild performs:

Build Docker image
Login to Amazon ECR
Push image to ECR
3️⃣ Deploy Stage

Application is deployed to Kubernetes using:

kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
🐳 Docker Build

Dockerfile builds the container image.

Example:

FROM node:18
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 3000
CMD ["npm", "start"]
☸️ Kubernetes Deployment

Deployment configuration:

deployment.yaml

Creates pods running the application inside the Kubernetes cluster.

Service configuration:

service.yaml

Exposes the application to external users.

🔐 IAM Permissions Required

The CodeBuild role requires access to:

AmazonEC2ContainerRegistryFullAccess
AmazonEKSClusterPolicy
AmazonEKSWorkerNodePolicy
📦 Buildspec File

The buildspec.yml file defines the build phases.

Example pipeline tasks:

Install dependencies
Login to ECR
Build Docker image
Push image to ECR
Deploy to EKS
🌐 Application Deployment

After successful pipeline execution:

Docker image is pushed to ECR

Kubernetes deployment updates automatically

Application becomes accessible via the Kubernetes service

📊 Key DevOps Concepts Demonstrated

✔ Continuous Integration
✔ Continuous Deployment
✔ Containerization
✔ Kubernetes orchestration
✔ Infrastructure automation
✔ Cloud-native deployment

📈 Future Improvements

Possible enhancements:

Add monitoring with Prometheus & Grafana

Implement Helm charts

Add Terraform for infrastructure automation

Configure auto-scaling in EKS
