# Push Docker Image to ECR

---

## Objective

This lab evaluates your ability to securely containerize a Node.js or Java application and automate the build and deployment of the container image to Amazon ECR using GitHub Actions with OIDC-based authentication and least-privilege IAM design.

---

## Problem Statement

Your organization wants to build and store their application as a Docker image in Amazon ECR. You are required to securely build a pipeline that automates this process.

---

## Technical Requirements

| Area | Requirement |
|------|------------|
| **Application type** | Node.js or Java |
| **CI/CD platform** | GitHub Actions |
| **Container registry** | Amazon ECR (private) |
| **Authentication method** | GitHub OIDC → AWS IAM role |
| **AWS credentials in GitHub secrets** | Not allowed |

---

## Tasks

### 1. Application Containerization

- Containerize an existing or new Node.js or Java application
- Create a Dockerfile that:
  - Uses a minimal, appropriate base image
  - Follows container security best practices
  - Builds successfully
- Include any supporting files required for efficient image builds (e.g., `.dockerignore`)

### 2. Secure AWS Authentication Using OIDC

- Configure AWS IAM to allow GitHub Actions to authenticate using OIDC
- Create an IAM role that:
  - Trusts GitHub's OIDC provider
  - Restricts access to your specific GitHub repository
  - Grants least-privilege permissions required to push images to ECR
- Do **not** store AWS access keys or secrets in GitHub

### 3. CI/CD Pipeline Implementation

Create a GitHub Actions workflow that:

- Triggers on every push to the repository
- Authenticates to AWS using OIDC
- Builds the Docker image
- Tags the image using the format: `yourfullname_appname`
- Pushes the image to a private Amazon ECR repository

---

## Deliverables

- **GitHub repository link** — link to the repository containing your application code, Dockerfile, and GitHub Actions pipeline
- **Private ECR link** — link to your Amazon ECR repository where the Docker image is stored

---

## Rubrics

| Category | Criteria | Points |
|----------|----------|--------|
| **Containerization** | Dockerfile builds successfully | 10 |
| | Uses minimal and appropriate base image | 5 |
| | `.dockerignore` file present | 5 |
| **CI/CD pipeline** | Workflow triggers correctly on push | 10 |
| | Docker image builds successfully | 10 |
| | Image tagged correctly | 5 |
| | Image pushed to ECR | 10 |
| | Uses official AWS GitHub Actions | 5 |
| | Pipeline fails securely on error | 10 |
| **Authentication and security** | GitHub OIDC used for AWS authentication | 10 |
| | IAM role follows least-privilege principles | 5 |
| | No long-lived AWS secrets used | 5 |
| **Bonus — extra effort** | ECR repo defined using IaC with best practices (tags, scanning, repo policy); ECR creation automated by CloudFormation GitSync; comprehensive architecture diagram; etc. | Up to 10 |
| **Total** | | **100 pts** |
