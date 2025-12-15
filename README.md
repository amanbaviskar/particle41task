# Particle41-DevOps-Challange
ECS Fargate Infrastructure on AWS using Terraform
📌 Overview

This project provisions a production-ready containerized infrastructure on AWS using Terraform (Infrastructure as Code).

A Dockerized application runs on Amazon ECS with Fargate inside private subnets and is securely exposed to the internet through an Application Load Balancer (ALB) deployed in public subnets.

The setup follows AWS, security, and DevOps best practices to ensure scalability, isolation, and maintainability.

🏗 Architecture
Internet
   ↓
Application Load Balancer (Public Subnets)
   ↓
ECS Fargate Service
   ↓
Private Subnets (No Public IPs)
   ↓
NAT Gateway (Outbound Internet Access)

⚙️ Tech Stack

AWS

VPC

ECS (Fargate)

Application Load Balancer (ALB)

NAT Gateway

Terraform

Docker

Git & GitHub

📁 Repository Structure
terraform/
├── main.tf
├── variables.tf
├── outputs.tf
├── versions.tf
├── .gitignore
└── README.md

🌐 Infrastructure Details
VPC

CIDR Block: 10.0.0.0/16

2 Public Subnets

2 Private Subnets

Internet Gateway for public subnets

NAT Gateway for outbound traffic from private subnets

ECS (Fargate)

ECS Cluster

ECS Task Definition

ECS Service running in private subnets

Containers do not have public IPs

Load Balancer

Application Load Balancer deployed in public subnets

Listener on port 80

Target Group forwards traffic to port 8080

📦 Application Details

Docker Image: prasad0508/simpletimeservice:latest

Container Port: 8080

🚀 How to Deploy
Prerequisites

AWS CLI configured with valid credentials

Terraform v1.3 or higher

Docker (optional, for local image testing)

Deployment Steps
terraform init
terraform apply


Type yes when prompted to confirm resource creation.

🌍 Access the Application

After successful deployment, Terraform outputs the ALB DNS name.

Open the application in your browser:

http://<alb_dns_name>


Example:

http://ecs-demo-alb-xxxxxxxx.us-east-1.elb.amazonaws.com

🧹 Cleanup

To avoid unnecessary AWS charges, destroy all resources when no longer needed:

terraform destroy

🔐 Security & Best Practices

ECS tasks run in private subnets

No public IPs assigned to containers

ALB handles all inbound traffic

Terraform state and sensitive files excluded via .gitignore

Dynamic Availability Zones used to avoid region-specific issues

Infrastructure managed using Infrastructure as Code (IaC)

👤 Author

Aman Baviskar
DevOps / Cloud Engineer
