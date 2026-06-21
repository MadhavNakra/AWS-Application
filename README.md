# 🚀 AWS End-to-End Highly Available Infrastructure Project

## 📖 Project Overview

This project demonstrates the design and implementation of a highly available, scalable, and secure cloud infrastructure on AWS using a custom Virtual Private Cloud (VPC). The infrastructure incorporates networking, compute, load balancing, auto scaling, monitoring, storage, and security services to simulate a production-grade cloud environment.

The primary objective of this project was to gain hands-on experience with AWS core services while implementing industry-standard cloud architecture principles such as High Availability, Fault Tolerance, Scalability, and Monitoring.

---

# 🏗️ Architecture Overview

The infrastructure was designed using a custom VPC with resources distributed across multiple Availability Zones to ensure high availability and fault tolerance.

### Architecture Components

* Custom VPC
* Public Subnets
* Private Subnets
* Internet Gateway
* Route Tables
* Security Groups
* EC2 Instances
* Application Load Balancer (ALB)
* Target Groups
* Auto Scaling Group (ASG)
* CloudWatch Monitoring
* IAM Roles and Policies
* S3 Storage
* CloudTrail Logging

> 📌 Insert Architecture Diagram Here

```text
Internet
    │
Application Load Balancer
    │
Auto Scaling Group
    │
EC2 Instances
    │
CloudWatch Monitoring

Custom VPC
├── Public Subnet - AZ A
├── Public Subnet - AZ B
├── Private Subnet - AZ A
└── Private Subnet - AZ B
```

---

# 🌐 VPC Configuration

A custom VPC was created to provide complete control over networking and security configurations.

### Configuration

* Custom CIDR Block
* DNS Hostnames Enabled
* DNS Resolution Enabled

### Screenshot

![VPC Configuration](screenshots/01-vpc/vpc.png)

---

# 🔀 Public and Private Subnets

Public and private subnets were created across multiple Availability Zones to improve fault tolerance and support high availability.

### Public Subnets

* Host internet-facing resources
* Associated with Internet Gateway

### Private Subnets

* Host internal resources
* Isolated from direct internet access

### Screenshot

![Subnets](screenshots/02-subnets/subnets.png)

---

# 🌍 Internet Gateway & Route Tables

Internet Gateway was attached to the VPC to provide internet connectivity for resources located in public subnets.

### Implemented

* Internet Gateway Attachment
* Public Route Table Configuration
* Route Propagation

### Screenshot

![Internet Gateway](screenshots/03-igw/igw.png)

---

# 🔐 Security Groups

Security Groups were configured as virtual firewalls to control inbound and outbound traffic.

### Inbound Rules

| Service | Port |
| ------- | ---- |
| SSH     | 22   |
| HTTP    | 80   |
| HTTPS   | 443  |

### Screenshot

![Security Groups](screenshots/04-security-groups/security-groups.png)

---

# 🖥️ EC2 Instance Deployment

Amazon EC2 instances were deployed using Amazon Linux 2023.

### Features

* Apache Web Server Installation
* Automated User Data Configuration
* Security Group Association

### User Data Script

```bash
#!/bin/bash
yum update -y
yum install httpd -y

systemctl start httpd
systemctl enable httpd

echo "<h1>Server Created by Auto Scaling</h1>" > /var/www/html/index.html
```

### Screenshot

![EC2](screenshots/05-ec2/ec2.png)

---

# ⚖️ Application Load Balancer

An Application Load Balancer was deployed to distribute incoming traffic across multiple EC2 instances.

### Features

* HTTP Listener (Port 80)
* Target Group Association
* Health Checks
* High Availability

### Screenshot

![ALB](screenshots/06-alb/alb.png)

---

# 🎯 Target Groups & Health Checks

Target Groups were configured to route traffic to healthy EC2 instances.

### Health Check Configuration

* Protocol: HTTP
* Port: Traffic Port
* Path: /

### Screenshot

![Target Group](screenshots/07-target-group/target-group.png)

---

# 📈 Auto Scaling Group (ASG)

An Auto Scaling Group was configured to automatically launch and terminate EC2 instances based on workload demand.

### ASG Configuration

| Parameter        | Value |
| ---------------- | ----- |
| Minimum Capacity | 1     |
| Desired Capacity | 1     |
| Maximum Capacity | 3     |

### Benefits

* High Availability
* Self-Healing Infrastructure
* Dynamic Resource Allocation

### Screenshot

![ASG](screenshots/08-asg/asg.png)

---

# 📊 Dynamic Scaling Policy

Target Tracking Scaling Policy was implemented using CPU Utilization as the scaling metric.

### Policy Configuration

| Setting      | Value                   |
| ------------ | ----------------------- |
| Policy Type  | Target Tracking         |
| Metric       | Average CPU Utilization |
| Target Value | 50%                     |

### Screenshot

![Scaling Policy](screenshots/09-scaling-policy/scaling-policy.png)

---

# 📉 CloudWatch Monitoring

Amazon CloudWatch was used to monitor infrastructure metrics and trigger scaling actions.

### Monitored Metrics

* CPU Utilization
* Network Traffic
* Instance Health
* Auto Scaling Events

### Screenshot

![CloudWatch](screenshots/10-cloudwatch/cloudwatch.png)

---

# 🧪 Stress Testing Auto Scaling

Stress testing was performed to validate the scaling behavior of the Auto Scaling Group.

### Command Used

```bash
stress-ng --cpu 2 --timeout 600s
```

### Observations

* CPU Utilization increased significantly.
* CloudWatch metrics reflected the workload.
* Auto Scaling policies evaluated scaling requirements.
* Additional EC2 instances were launched when thresholds were exceeded.

### Screenshot

![Stress Test](screenshots/11-stress-test/stress-test.png)

---

# 🗂️ AWS Services Used

| Service         | Purpose           |
| --------------- | ----------------- |
| VPC             | Network Isolation |
| EC2             | Compute Resources |
| Security Groups | Traffic Filtering |
| ALB             | Load Distribution |
| ASG             | Automatic Scaling |
| CloudWatch      | Monitoring        |
| IAM             | Access Management |
| S3              | Object Storage    |
| CloudTrail      | Audit Logging     |

---

# ⚠️ Challenges Faced

During implementation, several real-world cloud engineering challenges were encountered and resolved:

* Load Balancer Health Check Failures
* Auto Scaling Group Configuration Issues
* Target Group Registration Problems
* EC2 Connectivity Troubleshooting
* Security Group Misconfigurations
* Dynamic Scaling Policy Validation
* CloudWatch Alarm Configuration

---

# 🎯 Key Learnings

This project provided practical experience in:

* AWS Networking Fundamentals
* Designing Highly Available Architectures
* Load Balancing Concepts
* Auto Scaling Strategies
* Cloud Monitoring and Observability
* Infrastructure Troubleshooting
* Security Best Practices

---

# 🚀 Future Enhancements

* Implement HTTPS using ACM Certificates
* Deploy Instances in Private Subnets
* Configure NAT Gateway
* Automate Infrastructure using Terraform
* Containerize Application using Docker
* Deploy Applications using Amazon EKS

---

# 👨‍💻 Author

**Madhav Nakra**

AWS | DevOps | Cloud Engineer

GitHub: https://github.com/<your-username>

LinkedIn: https://linkedin.com/in/<your-profile>
