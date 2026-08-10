# Requirements

This file explains how I addressed the main requirements of the assignment.

## Functional Requirements

### Internet Access

The application is accessible from the internet through an Application Load Balancer.

The EC2 instances themselves are inside private subnets.

### Media

WordPress allows authenticated users to upload images and other media.

Amazon EFS is used as shared storage so the EC2 instances can access the same uploaded files.

Visitors can view the uploaded media from the public website.

### Database

Amazon RDS for MySQL is used as the WordPress database.

Posts, comments, users, and other WordPress data are stored in RDS.

I tested this by creating a post and submitting a comment.

## Non-Functional Requirements

### Reliability

The application runs across two Availability Zones.

The ALB can send traffic to healthy EC2 instances in either Availability Zone.

RDS uses Multi-AZ deployment and EFS uses Regional storage.

### Security

EC2 and RDS are in private subnets.

Security groups control communication between the different services.

Database credentials are stored in AWS Secrets Manager instead of being hardcoded in the setup script.

### Performance

The EC2 instances are managed by an Auto Scaling Group.

The number of instances can increase when CPU usage becomes higher.

### Monitoring

CloudWatch is used for logs, metrics, and alarms.

### Cost

I used small resource sizes because this is a training project with low traffic.

Resources will be deleted after the evaluation to avoid unnecessary cost.
