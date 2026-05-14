# Deploy DynamoDB Table with AWS SAM

---

## Project Description

Design and deploy a DynamoDB table using the AWS Serverless Application Model (SAM).

Your solution must provision an Amazon DynamoDB table using AWS SAM, including a primary key, additional attributes, and Global Secondary Indexes (GSIs). All deployments must be automated using SAM Pipelines integrated with GitHub Actions. The deployed table must be verifiable in the AWS Console and capable of accepting manual item inserts and queries for testing.

---

## Functional Requirements

The lab must result in a DynamoDB table that you can:

- View in the AWS Console
- Manually insert data into from the console
- Manually query and view stored items

The DynamoDB table must include:

- One primary key (sort key optional)
- At least two named non-key attributes
- Two Global Secondary Indexes (GSIs) based on attributes of your choice

---

## Technical Requirements

### Table Configuration

- Table must **not** use the default storage class
- Billing mode must be **On-Demand**
- Required schema:
  - Primary key
  - 2 additional attributes
  - 2 Global Secondary Indexes configured on non-primary attributes

### Deployment Requirements

- Deployment must be fully automated using **SAM Pipeline** and **GitHub Actions**
- Deployments must support two environments: **development** and **production**

### Challenge

- Use environment-specific and dedicated S3 buckets to store deployment artifacts for each SAM deployment (buckets can be pre-created manually or via IaC)
- Use environment-specific GitHub Actions deployment pipelines instead of the auto-generated multi-environment pipeline

---

## Deliverables

- Link to the GitHub repo containing the SAM template

---

## Rubrics

| Category | Criteria | Points |
|----------|----------|--------|
| **Infrastructure as code** | DynamoDB table defined in SAM template | 10 |
| | Correct billing mode (On-Demand) | 5 |
| | Correct table storage class (non-Standard) | 5 |
| | Primary key + 2 attributes + 2 GSIs implemented | 20 |
| **Automation and deployment** | SAM pipeline configured successfully | 10 |
| | GitHub Actions workflow functioning | 10 |
| | Multi-environment deployment (dev and prod) | 10 |
| **Verification and usability** | Successful CRUD operations performed via console | 10 |
| **Extra marks** | Environment-scoped artifact buckets — SAM deployments use separate S3 artifact buckets per environment (dev and prod) instead of a single shared bucket | 10 |
| | Separate dev and prod pipelines — auto-generated SAM GitHub Actions workflow split into two custom pipelines, each deploying only its related resources | 10 |
| **Total** | | **100 pts** |
