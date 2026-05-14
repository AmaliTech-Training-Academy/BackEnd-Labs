# Photo Uploader

---

## Project Description

Design and deploy a highly available, secure, containerized fullstack photo gallery web application within a single AWS Region using Amazon ECS on Fargate.

The application must allow users to upload photos with descriptions. Images must be stored in Amazon S3, metadata (descriptions) must be stored in Amazon RDS PostgreSQL, and CloudFront must be used to securely serve images. The S3 bucket must not be publicly accessible — S3 access must be restricted only to a CloudFront Origin Access Identity (OAI) or Origin Access Control (OAC) via a bucket policy.

The system must support automated blue/green deployments using AWS CodeDeploy triggered when new application container images are pushed to Amazon ECR.

All infrastructure must be provisioned using **AWS CloudFormation with GitSync**. Application code must be stored in a separate repository from infrastructure code. CI/CD authentication to AWS must use **OIDC**, not long-lived credentials.

---

## Functional Requirements

The application must provide a simple web-based photo gallery (no user authentication required) that:

- Displays images with their descriptions in a basic frontend UI
- Allows users to upload new images with descriptions

---

## Technical Requirements

### Infrastructure Automation

All infrastructure must be deployed via CloudFormation and may include:

| Resource | Notes |
|----------|-------|
| Multi-AZ VPC | Public subnets for ALB; private subnets for ECS and RDS |
| Security groups | Following least-privilege principles |
| S3 buckets | For image storage and infrastructure deployment |
| CloudFront distribution | Price Class 200 |
| Amazon RDS PostgreSQL | `db.t3` family |
| ECS and ECR resources | |
| Amazon EventBridge | |
| Amazon CodeDeploy and CodePipeline | |
| VPC endpoints | For CloudWatch, S3, and ECR access |

### Application Deployment Architecture

- ECS tasks must run in private subnets
- ECS service must use auto scaling with:
  - Minimum tasks: **1**
  - Desired tasks: **1**
  - Maximum tasks: **4**
- Scaling policies must be based on **CPU utilization threshold**
- A public ALB must route traffic to ECS tasks
- Images must be cached using a CloudFront distribution

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
| | CloudFront and S3 private bucket with OAI/OAC restriction | 10 |
| | All resources provisioned via CloudFormation GitSync | 10 |
| **CI/CD and image management** | GitHub Actions builds container image successfully | 5 |
| | Image pushed to ECR | 5 |
| | OIDC used for AWS authentication | 10 |
| | EventBridge rule detects new image push and triggers deployment via CodeDeploy | 5 |
| **ECS deployment and operations** | Application accessible via ALB | 5 |
| | ECS tasks pass ALB health checks | 5 |
| | ECS logs visible in CloudWatch Logs | 5 |
| | Auto scaling configured correctly (1–4 tasks) | 5 |
| | Blue/green deployment functions correctly | 5 |
| **Extra marks** | Infrastructure follows security and cost optimization best practices; all resources tagged appropriately; comprehensive architecture diagram; etc. | Up to 10 |
| **Total** | | **100 pts** |
