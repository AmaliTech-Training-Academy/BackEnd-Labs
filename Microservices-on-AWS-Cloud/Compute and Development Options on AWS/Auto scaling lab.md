# Auto Scaling

---

## Project Description

A customer is launching a public-facing web application that must remain available during traffic spikes while minimizing infrastructure costs during normal usage. The application must automatically scale compute capacity based on CPU spikes and distribute traffic evenly across multiple servers without manual intervention.

Your task is to design and deploy a highly available, auto-scaling web tier using Amazon EC2 Auto Scaling and an Application Load Balancer (ALB) that satisfies the business and technical requirements below using AWS best practices.

**Additional customer requirements:**

- The application runs in a secure, private network with no direct inbound access to servers
- All infrastructure is provisioned using Infrastructure as Code (IaC) for repeatability and auditability
- Scaling behaviour can be visually and functionally demonstrated to stakeholders

---

## Functional Requirements

- The web application must automatically adjust the number of backend servers based on demand, providing a consistent user experience regardless of traffic volume
- End users must access the application through a single public endpoint without knowing how many servers are running behind the scenes
- User requests must be distributed evenly across available servers to prevent any single server becoming a bottleneck
- When load exceeds acceptable thresholds, the platform must automatically provision additional compute capacity
- Each server instance must be uniquely identifiable during demonstrations so stakeholders can verify traffic is being served by multiple instances and observe scaling events in real time
- Backend servers must not be directly exposed to the public internet
- The deployment must support repeatability through automated infrastructure provisioning

---

## Technical Requirements

### Auto Scaling Configuration

Create an Auto Scaling Group (ASG) with:

- Minimum capacity: **1**
- Desired capacity: **1**
- Maximum capacity: **4**

Configure scaling policies to:

- Trigger scale-out when average CPU utilization exceeds **30%**
- Use a Launch Template defined in CloudFormation

### Networking and Load Balancing

Deploy:

- Two public subnets (across two Availability Zones) for the ALB
- Private subnets for EC2 instances

The Application Load Balancer must:

- Be internet-facing
- Distribute traffic across instances using round-robin behaviour

A **Regional NAT Gateway** must be provisioned to allow private instances to access the internet for package installation and updates.

### Instance Configuration

EC2 instances must:

- Use Amazon Linux AMI
- Install and configure Apache HTTP Server using EC2 User Data
- Deploy the web application as part of instance initialization
- Have no inbound SSH access

### Infrastructure Automation

All infrastructure components must be:

- Defined in a single or modular CloudFormation template
- Deployed using **CloudFormation GitSync**

The template must include:

- VPC, subnets, routing, IGW, NAT Gateway
- ALB, target groups, and listeners
- ASG, launch template, and scaling policies

---

## Validation and Demonstration (Live Review)

During the live review session you must demonstrate:

- Access to the application via the ALB endpoint
- Requests being served by different instances (verified via instance ID or IP changes)
- Scale-out event triggered by a CPU stress test
- New instances joining the target group automatically

---

## Deliverables

- Public GitHub repository URL containing:
  - CloudFormation template(s)
  - Any supporting documentation
- ALB DNS name for testing and validation
- Live demonstration during the lab review session

---

## Rubrics

| Category | Criteria | Points |
|----------|----------|--------|
| **Infrastructure and high availability design** | Correct multi-AZ VPC and subnet configuration | 10 |
| | Provisioning of ALB, Regional NAT Gateway, and routing setup | 15 |
| | Well-defined ASG, launch template, and scaling policies | 10 |
| | Infrastructure follows security and cost optimization best practices | 10 |
| **Application behaviour and auto scaling** | Web application correctly displays instance-specific information | 10 |
| | CPU stress mechanism functions as intended | 10 |
| | Scale-out event successfully triggered and observed | 10 |
| | New instances register with ALB target group automatically | 5 |
| **Load balancing and traffic distribution** | ALB distributes traffic across multiple instances | 10 |
| **Extra credit** | Clean, modular, well-documented CloudFormation template; clear explanation of scaling policies and thresholds; optional scale-in behaviour implemented and demonstrated | Up to 10 |
| **Total** | | **100 pts** |
