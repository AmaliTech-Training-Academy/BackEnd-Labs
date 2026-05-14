# Security Baseline Workshop Lab

**Workshop link:** [https://catalog.workshops.aws/startup-security-baseline/en-US](https://catalog.workshops.aws/startup-security-baseline/en-US)

---

## Introduction

In this lab you will undertake various security exercises from the Security Baseline Amazon Workshop. The goal is to understand and implement basic security tasks using AWS security services.

You are encouraged to practice all tutorials in the workshop, but are only required to submit the sections below.

---

## Part II — Level 1

### Use Roles Instead of Users

#### EC2 Role

Follow the steps outlined to create an EC2 role. Take a screenshot of the role with the role name and permissions in focus.

| Requirement | Detail |
|-------------|--------|
| Role name | `my_fullname_ec2_role` |
| Screenshot file name | `my_fullname_ec2_role_1` |

#### Lambda Role

Follow the steps outlined to create a Lambda role. Take a screenshot of the role with the role name and permissions in focus.

| Requirement | Detail |
|-------------|--------|
| Role name | `my_fullname_lambda_role` |
| Screenshot file name | `my_fullname_lambda_role_2` |

#### ECS Role

Follow the steps outlined to create an ECS role. Take a screenshot of the role with the role name and permissions in focus.

| Requirement | Detail |
|-------------|--------|
| Role name | `my_fullname_ecs_role` |
| Screenshot file name | `my_fullname_ecs_role_3` |

---

### Use Ephemeral Secrets or a Secrets Management Service

#### Systems Manager Parameter Store

Follow the steps outlined to create a parameter. Take a screenshot of the parameter with the name in focus.

| Requirement | Detail |
|-------------|--------|
| Parameter name | `/fullname/week2lab/parameter_name/` |
| Screenshot file name | `my_fullname_week2lab_parameter_name_4` |

#### Secrets Manager

Follow the steps outlined to create a secret. Take a screenshot of the secret with the name in focus.

| Requirement | Detail |
|-------------|--------|
| Secret name | `/fullname/week2lab/secret_name` |
| Screenshot file name | `my_fullname_week2lab_secret_name_5` |

---

## Part II — Level 4

### Restrict Credential Usage Scope with Resource-Based Policies

**Setup:**

- Create an S3 bucket named `fullname_week2bucket`
- Create a new IAM user named `fullname_week2_iamuser`
- Follow the steps outlined to create a resource-based policy that restricts `PutObject` to the newly created IAM user only, and assign the policy to the S3 bucket

**Test with your current IAM user:** Try uploading an object to the S3 bucket using your current IAM user and take a screenshot of the response.

| Requirement | Detail |
|-------------|--------|
| Expected result | Access denied (unauthorized) |
| Screenshot file name | `my_fullname_s3_unauthorized_putobjectresponse_6` |

**Test with the new IAM user:** Log into the AWS account as the new user and upload an object to the S3 bucket. Take a screenshot of the response.

| Requirement | Detail |
|-------------|--------|
| Expected result | Upload succeeds (authorized) |
| Screenshot file name | `my_fullname_s3_authorized_putobjectresponse_7` |

---

### Use VPC Endpoints to Access Supported AWS and External Services

Follow the steps outlined to create the required resources: VPC, subnet, S3 buckets, EC2 instances, and endpoints.

#### Testing Gateway Endpoints

| Test | Screenshot File Name |
|------|---------------------|
| Output of accessing the unrestricted bucket using the gateway endpoint | `my_fullname_gw_unrestricted_s3_8` |
| Output of accessing the restricted bucket using the gateway endpoint | `my_fullname_gw_restricted_s3_9` |

#### Testing Interface Endpoints

Take **one screenshot** showing the output of both commands below:

- Output of accessing the unrestricted bucket using the interface endpoint
- Output of accessing the restricted bucket using the interface endpoint

| Requirement | Screenshot File Name |
|-------------|---------------------|
| Both outputs in one screenshot | `my_fullname_int_restricted_unrestricted_s3_10_11` |

---

## Deliverables

- Upload all screenshots following the naming conventions specified in each task
- Demonstrate the ability to complete all tasks in a Lab Review Call

---

## Rubrics

| Criteria | Weight |
|----------|--------|
| Successful creation of EC2, ECS, and Lambda IAM roles | 30% |
| Successful creation of parameter resource and secrets | 20% |
| Demonstrate restricting S3 bucket access using a resource-based policy | 15% |
| Demonstrate restricting access via VPC gateway endpoint policy | 15% |
| Demonstrate restricting access via VPC interface endpoint policy | 15% |
| Extra marks | 5% |
