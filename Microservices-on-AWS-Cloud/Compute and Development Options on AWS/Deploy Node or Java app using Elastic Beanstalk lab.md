# Deploy Node or Java App Using Elastic Beanstalk — Lab

---

## Project Description

A customer wants to rapidly deploy a managed web application without directly managing servers, load balancers, or scaling policies. The solution must support automated deployments, integrate with a source control system, and allow the application to evolve through continuous delivery.

Your task is to deploy a Node.js or Java web application using AWS Elastic Beanstalk, where application versions are built from source, packaged, stored in Amazon S3, and deployed automatically whenever new code is pushed to GitHub.

> **Optional challenge:** The customer also requires the application to integrate with an external data service to simulate real-world backend dependencies.

---

## Functional Requirements

- The application must be accessible through a public Elastic Beanstalk endpoint and respond successfully to user requests
- Application updates must be delivered through an automated deployment process, eliminating manual uploads or console-based deployments
- The deployment process must support versioned application releases, allowing the customer to track and manage multiple versions over time
- The application must demonstrate real-world integration by connecting to an external data service (e.g., a database or managed AWS service)
- The solution must allow the customer to release new versions safely, validate deployments quickly, and roll forward with minimal operational effort

---

## Technical Requirements

### Application Development

- The application must be written in **Node.js** or **Java**
- The GitHub repository must include all required build and runtime files:
  - **Node.js:** `package.json`
  - **Java:** build files (e.g., Maven or Gradle)
- Application must return a simple response confirming successful deployment

### Elastic Beanstalk Deployment

- Create an Elastic Beanstalk application and environment
- The initial deployment must use a source bundle stored in **Amazon S3** and be deployed via Elastic Beanstalk (not directly from GitHub)
- The Elastic Beanstalk environment must be publicly accessible and managed entirely by Elastic Beanstalk (no custom EC2 management)

### CI/CD Automation

Configure a **GitHub Actions workflow** that:

- Packages the application into a source bundle (ZIP)
- Uploads the bundle to an Amazon S3 bucket
- Triggers a new Elastic Beanstalk application version
- Deploys the new version automatically when code is pushed

Deployments must occur **without manual intervention** after the initial setup.

### External Service Integration (Optional Challenge)

The application must connect to at least one external service, such as **Amazon RDS**, **Amazon DynamoDB**, or **Amazon S3**. Connection details must be managed using Elastic Beanstalk environment variables.

---

## Validation and Demonstration (Live Review)

During the live review session you must demonstrate:

- Application accessibility via the Elastic Beanstalk URL
- A successful redeployment triggered by a GitHub push
- Updated application behaviour or version number after deployment
- Connectivity to the external service (if optional challenge is completed)

---

## Deliverables

- Elastic Beanstalk application URL
- Public GitHub repository URL containing:
  - Application source code
  - GitHub Actions workflow
  - Deployment configuration files
- Live demonstration during the lab review session

---

## Rubrics

| Category | Criteria | Points |
|----------|----------|--------|
| **Application functionality and accessibility** | Application deploys successfully and is accessible via Elastic Beanstalk URL | 20 |
| | Application responds correctly to requests | 10 |
| | *(Optional challenge)* External service integration configured using Beanstalk managed environment variables | 20 |
| **CI/CD automation and deployment** | GitHub Actions workflow correctly packages the application | 10 |
| | Source bundle uploaded to S3 successfully | 10 |
| | Elastic Beanstalk deployment triggered automatically | 10 |
| | Application version updates correctly on code changes | 10 |
| **Extra credit** | Well-defined GitHub Actions workflow per functional and security best practices | Up to 10 |
| **Total** | | **100 pts** |
