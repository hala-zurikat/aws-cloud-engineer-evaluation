# Well-Architected Design Decisions

I used the main ideas of the AWS Well-Architected Framework while building the project.

## Operational Excellence

I used CloudWatch for logs and monitoring.

The EC2 setup is automated using a Launch Template and user data, which makes it easier for Auto Scaling to create replacement instances.

## Security

The ALB is public, but EC2 and RDS are private.

Security groups control which services can communicate with each other.

Database credentials are stored in Secrets Manager and the EC2 instances use an IAM role to access them.

## Reliability

The application is deployed across two Availability Zones.

The ALB sends traffic to healthy EC2 instances and Auto Scaling replaces failed instances.

RDS uses Multi-AZ and EFS provides shared storage across the application servers.

## Performance Efficiency

The ALB distributes traffic between the EC2 instances.

Auto Scaling can add more instances when CPU usage increases.

## Cost Optimization

I used small EC2 and RDS instance sizes because the expected traffic is low.

Auto Scaling limits the number of EC2 instances to avoid unnecessary resources.

The environment will also be deleted after the evaluation.
