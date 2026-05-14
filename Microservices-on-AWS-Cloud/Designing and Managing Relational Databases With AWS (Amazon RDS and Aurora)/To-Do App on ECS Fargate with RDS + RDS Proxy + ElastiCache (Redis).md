# To-Do App on ECS Fargate with RDS + RDS Proxy + ElastiCache (Redis)

---

## Project Description

Design and deploy a highly available, secure containerized Java To-Do fullstack application within a single AWS Region using Amazon ECS on Fargate.

The application must store data in an Amazon RDS database accessed through RDS Proxy, and use Amazon ElastiCache for Redis to improve read performance through caching.

The application must run inside a custom multi-AZ VPC, expose traffic via a public Application Load Balancer (ALB), and support automated blue/green deployments triggered by container image updates.

All infrastructure must be provisioned using **AWS CloudFormation**, and all CI/CD interactions with AWS must use **OIDC-based authentication** from GitHub Actions.

---

## Functional Requirements

The application must provide a simple UI allowing users to create, view, update, and delete tasks.

The application must demonstrate:

- Reads accelerated via **Redis cache**
- Writes persisted to **RDS through RDS Proxy**

---

## Technical Requirements

### Infrastructure Automation

All infrastructure must be deployed via CloudFormation and may include:

| Resource | Notes |
|----------|-------|
| Multi-AZ VPC | Public subnets for ALB; private subnets for ECS and RDS |
| Security groups | Following least-privilege principles |
| Amazon RDS PostgreSQL | `db.t3` family |
| ECS and ECR resources | |
| Amazon EventBridge | |
| Amazon CodeDeploy and CodePipeline | |
| VPC endpoints | For CloudWatch, S3, and ECR access |

### Application Deployment Architecture

- ECS tasks must run in a dedicated private subnet
- RDS cluster and related proxies must run in different dedicated private subnets
- ElastiCache (Redis) cluster nodes must also run in dedicated subnets
- Separate security groups must be provisioned for each distinct resource type
- ECS service must use auto scaling with:
  - Minimum tasks: **1**
  - Desired tasks: **1**
  - Maximum tasks: **4**
- Scaling policies must be based on **CPU utilization threshold**
- A public ALB must route traffic to ECS tasks

### Application Build and Image Management

- Application code must be separated from infrastructure code
- When application code is pushed, a GitHub Actions workflow must build the application into a container image and push it to **Amazon ECR**
- **OIDC authentication** must be used — no long-lived credentials

### Deployment Pipeline

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
| | RDS, RDS Proxy, and ElastiCache provisioned into segregated subnets with distinct security groups per security best practice | 10 |
| | All resources provisioned and deployed via CloudFormation GitSync | 10 |
| **CI/CD and image management** | GitHub Actions builds container image successfully | 5 |
| | Image pushed to ECR | 5 |
| | OIDC used for AWS authentication | 10 |
| | EventBridge rule detects new image push and triggers deployment via CodeDeploy | 5 |
| **ECS deployment and operations** | Application accessible via ALB | 5 |
| | ECS tasks pass ALB health checks | 5 |
| | ECS logs visible in CloudWatch Logs | 5 |
| | Auto scaling configured correctly (1–4 tasks) | 5 |
| | Blue/green deployment functions correctly | 5 |
| **Extra marks** | Infrastructure follows security and cost optimization best practices; all resources tagged appropriately; comprehensive architecture diagram; application code uses correct SDKs to connect to backend | Up to 10 |
| **Total** | | **100 pts** |
