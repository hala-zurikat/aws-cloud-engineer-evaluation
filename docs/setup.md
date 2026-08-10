# Basic Setup

This is a short overview of how I built the application.

## 1. Network

I created a custom VPC in `eu-west-1` using two Availability Zones.

I created public, private application, and private database subnets.

The public subnets contain the ALB and NAT Gateways.

The EC2 instances and RDS database are in private subnets.

## 2. Security

I created separate security groups for the ALB, EC2, RDS, and EFS.

Only the required ports are allowed between the services.

I did not open SSH access to the EC2 instances.

## 3. Database

I created an Amazon RDS MySQL database using a Multi-AZ deployment.

The database is private and is used by WordPress.

## 4. Shared Storage

I created Amazon EFS and mounted it to the WordPress uploads directory.

This allows both EC2 instances to use the same uploaded media.

## 5. EC2 and IAM

I created an IAM role for the EC2 instances.

The role allows EC2 to read the database credentials from Secrets Manager and send logs to CloudWatch.

A Launch Template and user data are used to install and configure WordPress automatically.

## 6. Load Balancer and Auto Scaling

I created an Application Load Balancer and connected it to a target group.

The Auto Scaling Group runs EC2 instances in both Availability Zones.

The configuration is:

- Minimum: 2
- Desired: 2
- Maximum: 4

## 7. Monitoring

CloudWatch collects Apache and setup logs.

I also created alarms for unhealthy ALB targets and high RDS CPU usage.

## 8. Testing

I tested the application by:

- Opening the website from the internet.
- Creating a WordPress post.
- Uploading an image.
- Submitting a comment.
- Terminating one EC2 instance.

The website stayed available and Auto Scaling created a replacement instance.
