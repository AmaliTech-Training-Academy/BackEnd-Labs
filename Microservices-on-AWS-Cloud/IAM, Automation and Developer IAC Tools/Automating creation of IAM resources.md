# Automating Creation of IAM Resources

---

## Introduction

In this lab, you will learn how to create IAM users and other resources via AWS CloudFormation with GitSync, and assign relevant permissions using IAM User Group permissions.

---

## Task 1

Create a GitSync-enabled CloudFormation template that generates the following resources:

- **One-time password** — auto-generated and stored in Secrets Manager, to be used for all users
- **S3 User Group permissions** — list S3 buckets
- **EC2 Group permissions** — list EC2 instances, create EC2 instances
- **Three IAM users** with console access:
  - `ec2-user1` and `ec2-user2` assigned to the EC2 Group
  - `s3-user` assigned to the S3 Group
  - IAM users must be assigned the temporary password created above
  - IAM users must have AWS Console access and must be prompted to change their password on initial login
  - `ec2-user2` should be **prevented** from creating EC2 instances

---

## Task 2

Log into the AWS Console with each of the newly created IAM users and attempt to access Amazon S3 buckets and EC2 instances in your AWS account.

For each IAM user, take **2 screenshots** — one each showing either failure or success when accessing EC2 and S3 resources.

---

## Deliverables

Provide a link to the GitHub repo containing your CloudFormation template.

---

## Rubrics

| Criteria | Weight |
|----------|--------|
| CloudFormation template clearly defined per lab requirements and best practice | 60% |
| Successful implementation of GitSync per security best practice | 20% |
| Clear demonstration of IAM concepts during review | |
