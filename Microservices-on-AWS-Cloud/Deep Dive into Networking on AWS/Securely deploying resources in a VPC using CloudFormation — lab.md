# Securely Deploying Resources in a VPC Using CloudFormation — Lab

---

## Project Description

Design and deploy a highly available, secure, multi-AZ Virtual Private Cloud (VPC) using AWS CloudFormation that demonstrates fault-tolerant network design, controlled internet access, and secure EC2 instance management.

The architecture must span multiple Availability Zones, include redundant public and private subnets, deploy multiple EC2 instances per tier, and use highly available NAT Gateways for outbound internet access from private resources.

All EC2 access must be performed using **AWS Systems Manager Session Manager**, and all infrastructure must be provisioned using Infrastructure as Code (IaC) submitted via a public GitHub repository.

---

## Functional Requirements

**Public web tier must:**

- Consist of two EC2 instances, each in a different AZ
- Run Apache HTTP Server (installed via User Data)
- Display a webpage containing your full name and the lab name

**Private application tier must:**

- Consist of two EC2 instances, each in a different AZ
- Reside in private subnets only

**All EC2 instances must:**

- Use Amazon Linux AMIs
- Be managed exclusively via AWS Systems Manager Session Manager

---

## Technical Requirements

### Highly Available VPC and Networking Architecture

- Create a custom VPC spanning two Availability Zones
- Provision two public subnets (one per AZ) and two private subnets (one per AZ)
- Configure an Internet Gateway (IGW), two NAT Gateways (one per AZ), and separate route tables for public and private subnets
- Ensure public subnets have direct internet access
- Ensure private subnets have egress-only internet access through the NAT Gateway in their **own AZ** — no cross-AZ NAT dependency

### Compute, Security, and Access Control

- Deploy four EC2 instances total: 2 public (one per AZ) and 2 private (one per AZ)
- Apache must be installed on public instances via User Data defined in CloudFormation
- Security groups must follow **least-privilege** principles:
  - Allow HTTP access to public instances
  - Allow required ICMP (ping) traffic for validation
  - No inbound SSH access permitted

### Systems Manager Integration

All EC2 instances must:

- Have an IAM role with the `AmazonSSMManagedInstanceCore` policy attached
- Be accessible using Session Manager only
- All validation and troubleshooting must be performed through Session Manager sessions

---

## Validation and Demonstration (Live Review)

During the live review session you must demonstrate:

- Access to both public web servers via browser
- Network reachability tests using Session Manager:
  - Public to private instance connectivity via ping
  - Outbound internet access from private instances via NAT Gateways (verifiable by traceroute, ping, or installing a package)

---

## Deliverables

- Public GitHub repository URL containing:
  - CloudFormation templates
  - EC2 User Data configuration
  - Any supporting documentation or notes
- Live demonstration during the lab review session

---

## Rubrics

| Category | Criteria | Points |
|----------|----------|--------|
| **High availability VPC design** | Multi-AZ VPC with correct public and private subnet design | 20 |
| | Proper routing, IGW, and AZ-aligned NAT Gateway configuration | 20 |
| **EC2 deployment and application functionality** | Correct deployment of 2 public and 2 private EC2 instances across AZs | 10 |
| | Apache installed via User Data and reachable on both public instances | 10 |
| | Private instances have outbound-only internet access | 5 |
| **Security and access management** | Session Manager access correctly configured for all instances | 10 |
| | Security groups correctly allow only required HTTP and ICMP traffic | 5 |
| **Architectural knowledge and reasoning** | Correctly explain what the AWS Regional NAT Gateway is, how it differs from AZ-scoped NAT Gateways, and how it could replace the two NAT Gateways in this architecture | 10 |
| **Extra credit** | Clean, modular, well-commented CloudFormation template; consistent tagging and naming; clear explanation of design decisions | Up to 10 |
| **Total** | | **100 pts** |
