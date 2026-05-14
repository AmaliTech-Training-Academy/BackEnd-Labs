# Testing IAM User Permissions

---

## Introduction

In this lab, you will learn how to create IAM users via the AWS Management Console Cloud Shell, assign and test permissions using inline policies and group policies.

---

## Task 1 — 50%

Using the **AWS Cloud Shell**:

- Create an IAM user
- Create access keys for this user
- Attach an AWS Managed IAM Policy to allow the user to create and view S3 buckets

Take **2 screenshots** to capture the processes above and their relevant outputs.

| Screenshot | File Name |
|------------|-----------|
| Screenshot 1 | `Full_Name_Image_1` |
| Screenshot 2 | `Full_Name_Image_2` |

---

## Task 2 — 25%

Using your **local Linux machine with AWS CLI installed**:

- Create a login profile using the credentials of the user created in Task 1 — screenshot the command and output as `Full_Name_Image_3`
- Log the new user into your AWS account using the profile created
- Run `sts get-caller-identity` to output details of the logged-in user — screenshot the output as `Full_Name_Image_4`
- List all S3 buckets in the AWS account — screenshot the output as `Full_Name_Image_5`
- Create 2 new S3 buckets — screenshot the output as `Full_Name_Image_6`
- List all EC2 instances in the AWS account — screenshot the output as `Full_Name_Image_7`

| Step | File Name |
|------|-----------|
| Create login profile | `Full_Name_Image_3` |
| STS get-caller-identity output | `Full_Name_Image_4` |
| List S3 buckets | `Full_Name_Image_5` |
| Create 2 S3 buckets | `Full_Name_Image_6` |
| List EC2 instances | `Full_Name_Image_7` |

---

## Task 3 — Challenge — 25%

- Modify the user's permissions to allow viewing of EC2 instances
- Screenshot the command output as `Full_Name_Image_8`

---

## Deliverables

- Upload screenshots of task outcomes following the naming conventions specified above
- Demonstrate the ability to complete all tasks in a Lab Review Call

---

## Rubrics

| Criteria | Weight |
|----------|--------|
| Screenshots demonstrating creation of IAM resources in Cloud Shell | 50% |
| Screenshots demonstrating navigation within the AWS CLI | |
