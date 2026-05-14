# Serverless To-Do App with Event-Driven Expiry Processing

---

## Project Description

A customer requires a fully serverless task management application that allows authenticated users to manage personal tasks and receive automated email notifications when tasks expire. The system must scale automatically, require minimal operational overhead, and support event-driven workflows.

Your task is to design and deploy a serverless to-do application using managed AWS services. The backend must be exposed through secure APIs, persist data in a highly available datastore, and process task expiry events asynchronously. The frontend must provide a simple, authenticated user experience.

---

## Functional Requirements

### User Authentication

- Users must be able to sign up and sign in using email and password
- Authentication must be handled by **Amazon Cognito User Pool**
- User sign-up must be auto-confirmed (no manual verification)
- After successful authentication, a **PostAuthentication Lambda** must subscribe the user's email address to an SNS topic for task notifications

### Task Management

Authenticated users must be able to create, view, update, and delete tasks. Tasks must be stored in a DynamoDB table and include the following attributes:

| Attribute | Description |
|-----------|-------------|
| `TaskId` | UUID |
| `UserId` | From Cognito identity |
| `Description` | Task description |
| `Date` | Task date |
| `Status` | Pending, Completed, or Expired |
| `Deadline` | Timestamp — defaults to 5 minutes after task creation; must trigger a scheduled expiry event |

Additional attributes may be added as needed.

### Task Expiry Processing (Event-Driven)

**Expiry workflow** — when a task reaches its deadline and status is still `Pending`, the system must:

- Update the task status in DynamoDB to `Expired`
- Send an email notification to the task owner via SNS

**Cancellation workflow** — if a task is `Completed` or `Deleted` before its deadline:

- The scheduled expiry event must be cancelled
- This must be implemented using **DynamoDB Streams**, **SQS FIFO Queue**, and **Lambda**
- The workflow must be decoupled and idempotent

### Frontend Requirements

- Frontend must be hosted using **AWS Amplify**
- The UI must allow users to:
  - View Pending, Completed, and Expired tasks
  - Create new tasks
  - Update and delete tasks
- Frontend must authenticate users via Cognito User Pool
- Frontend must communicate with the backend via API Gateway → Lambda → DynamoDB

---

## Technical Requirements

### Infrastructure as Code

All backend infrastructure including the Amplify frontend must be defined using **AWS SAM**.

### AWS Services to Use

| Service | Usage |
|---------|-------|
| **AWS Lambda** | CRUD operations, PostAuthentication trigger, expiry and cancellation handlers |
| **Amazon API Gateway (REST API)** | Exposes CRUD endpoints |
| **Amazon DynamoDB** | Stores tasks — on-demand capacity, single-table design |
| **Amazon Cognito User Pool** | User authentication |
| **Amazon SNS** | Email notifications |
| **Amazon SQS FIFO** | Reliable task expiry event processing |
| **Amazon CloudWatch** | Logs and metrics |
| **Amazon EventBridge** | Managing scheduled expiry events |

---

## Validation and Demonstration (Live Review)

During the live review session you must demonstrate:

- Successful user sign-up and sign-in
- Task CRUD actions
- Automatic task expiry after deadline
- Email notification sent on task expiry
- Cancellation of expiry when a task is completed or deleted
- Frontend interaction with authenticated backend APIs
- Automated deployment via AWS SAM pipeline

---

## Deliverables

- Public GitHub repository URL containing the AWS SAM template
- Link to the GitHub repo containing frontend application code
- Amplify frontend URL
- Network architecture diagram (created via diagram-as-code or draw.io)
- Live demonstration during the one-on-one lab review session

---

## Rubrics

| Category | Criteria | Points |
|----------|----------|--------|
| **Authentication and security** | Cognito User Pool configured correctly | 10 |
| | PostAuthentication Lambda subscribes users to SNS | 10 |
| **Task management and data modeling** | CRUD operations function correctly | 15 |
| | Proper DynamoDB schema and status handling | 10 |
| **Event-driven expiry workflow** | Expiry event triggers correctly at deadline | 15 |
| | SNS email notification sent on expiry | 10 |
| | Expiry cancellation handled via Streams and SQS FIFO | 10 |
| **Frontend integration** | Amplify frontend properly configured with backend via environment variables and API/Cognito registration in frontend code | 5 |
| | Frontend interacts successfully with backend APIs | 5 |
| **Infrastructure as code and observability** | Backend fully defined using AWS SAM | 5 |
| | Proper logging and monitoring via CloudWatch | 5 |
| **Extra credit** | Clean DynamoDB table design; proper IAM least-privilege policies; comprehensive and well-documented architecture diagram | Up to 10 |
| **Total** | | **100 pts** |
