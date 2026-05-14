# ECS CI/CD

---

## Project Description

Design and deploy a highly available, secure, containerized fullstack Java web application within a single AWS Region using Amazon ECS on Fargate.

The application must run inside a custom multi-AZ VPC, expose traffic via a public Application Load Balancer (ALB), and support automated blue/green deployments triggered by container image updates.

All infrastructure must be provisioned using **AWS CloudFormation with GitSync**, and all CI/CD interactions with AWS must use **OIDC-based authentication**.

---

## Functional Requirements

The application frontend must present a minimal static UI displaying:

- Your full name
- The lab name

---

## Technical Requirements

### 1. Infrastructure Automation

- All infrastructure resources (VPC, subnets, security groups, container image repository, pipelines, artifact storage, etc.) must be provisioned via **CloudFormation with GitSync enabled**
- Use **VPC endpoints** to provide connectivity between ECS Fargate tasks and the ECR repository

### 2. Application Deployment Architecture

- ECS tasks must run in **private subnets**
- ECS service must use auto scaling with:
  - Minimum tasks: **1**
  - Desired tasks: **1**
  - Maximum tasks: **4**
- Scaling policies must be based on **CPU utilization threshold**
- A public Application Load Balancer must route traffic to ECS tasks

### 3. Application Build and Image Management

- Application code must be separated from infrastructure code
- When application code is pushed, a GitHub Actions workflow must:
  - Build the application code into a container image
  - Push the image to Amazon ECR
  - Use **OIDC authentication** (not long-lived GitHub secrets) for secure image pushes

### 4. Deployment Pipeline

- Amazon EventBridge must detect new image pushes to ECR and trigger CodePipeline
- CodePipeline must deploy the newest version of the application to ECS using CodeDeploy with **blue/green deployment** type

---

## Deliverables

- Link to the GitHub repo containing CloudFormation infrastructure templates
- Link to the GitHub repo containing application code, Dockerfile, and related build and deploy files
- ALB endpoint for accessing the running application
- Network architecture diagram (created via diagram-as-code or draw.io)

---

## Rubrics

| Category | Criteria | Points |
|----------|----------|--------|
| **Infrastructure provisioning and pipeline** | Multi-AZ VPC with correct subnet design | 10 |
| | Private ECS tasks with VPC endpoint connectivity and public ALB architecture | 10 |
| | Security groups follow least-privilege principles | 10 |
| | All resources provisioned via CloudFormation GitSync | 10 |
| **CI/CD and image management** | GitHub Actions builds container image successfully | 5 |
| | Image pushed to ECR | 5 |
| | OIDC used for AWS authentication | 10 |
| | Image tagging strategy is consistent and immutable | 5 |
| **ECS deployment and operations** | Application accessible via ALB | 5 |
| | ECS tasks pass ALB health checks | 5 |
| | ECS logs visible in CloudWatch Logs | 5 |
| | Auto scaling configured correctly (1–4 tasks) | 5 |
| | Blue/green deployment functions correctly | 5 |
| **Extra marks** | Infrastructure follows security and cost optimization best practices; all resources tagged appropriately; comprehensive architecture diagram; etc. | Up to 10 |
| **Total** | | **100 pts** |
