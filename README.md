# AWS 3-Tier Web Architecture Hands-on

This project demonstrates a basic 3-tier web architecture built on AWS using VPC, ALB, EC2, and RDS.  
The goal is to understand how each layer interacts and to compare a simplified learning environment with a production-oriented design.

---

## Architecture Diagrams

The following diagrams illustrate the difference between the actual learning environment and an ideal production-grade architecture.

![AWS Architecture](docs/architecture.png)

---

### 1. Current Architecture (Learning Environment)

This environment was built using a single VPC with minimal subnet segmentation for learning purposes.  
Resources were deployed primarily to verify connectivity and understand service integration.

- All resources are placed within a simplified network structure
- Focus is on functional validation rather than strict security design
- Subnet segmentation is not fully enforced in a production-like manner

---

### 2. Target Architecture (Production Design)

This architecture represents a production-grade 3-tier design with proper network segmentation and security isolation.

- **Public Subnet**
  - Application Load Balancer (ALB)
  - EC2 (Web Server)

- **Private Subnet**
  - Amazon RDS (MySQL Database)

Key design principles:
- No direct public access to the database layer
- Traffic is routed through ALB to EC2 and then to RDS
- Security Groups enforce strict communication rules between tiers

---

## Objectives

- Understand AWS core services (VPC, EC2, ALB, RDS, CloudWatch)
- Learn public/private subnet design and network isolation concepts
- Implement basic load balancing using ALB
- Observe monitoring concepts using CloudWatch metrics
- Compare learning architecture vs production architecture design

---

## Implementation Steps

- **Step 1: VPC Setup**
  - Create VPC, subnets, route tables, and Internet Gateway

- **Step 2: EC2 Deployment**
  - Launch Amazon Linux instance
  - Configure Apache/Nginx
  - Verify SSH access

- **Step 3: S3 Setup**
  - Create bucket and upload static content

- **Step 4: CloudWatch Monitoring**
  - Configure CPU metrics and alarms

- **Step 5: ALB Configuration**
  - Create Application Load Balancer
  - Configure target group and routing

- **Step 6: RDS Deployment**
  - Launch MySQL instance
  - Connect from EC2 and execute queries

---

## Verification Evidence

### ALB Web Access Success
![ALB Access](docs/screenshots/01_alb_access.png)

### EC2 to RDS Connection Success
![RDS Connection](docs/screenshots/02_rds_connect.png)

---

## Key Learnings

- Proper subnet design is essential for secure cloud architecture
- ALB enables scalable traffic distribution across compute resources
- RDS should always be isolated in a private subnet for security
- Security Groups act as a critical layer of network control

---

## Future Improvements

- Automate infrastructure using Terraform (Infrastructure as Code)
- Introduce Auto Scaling for EC2 instances
- Add CloudWatch dashboards for centralized monitoring
- Implement CI/CD pipeline for application deployment
