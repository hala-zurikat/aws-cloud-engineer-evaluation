# Highly Available WordPress Application on AWS

This project was created for my AWS Cloud Engineer Trainee evaluation.

The goal was to build a 3-tier web application that is available, scalable, secure, and monitored.

I used WordPress as the application and deployed it in the AWS Europe (Ireland) Region across two Availability Zones.

## Application

Public link:

https://halla-evaluation.cirrusgo.me/

The application allows users to:

- View posts and media.
- Submit comments.
- Store dynamic content in a database.
- Upload media through the WordPress admin area.

## Main AWS Services

The main services I used are:

- VPC
- EC2
- Application Load Balancer
- Auto Scaling
- Amazon RDS
- Amazon EFS
- IAM
- Secrets Manager
- CloudWatch
- Route 53

## Architecture

The Application Load Balancer receives traffic from the internet and sends it to WordPress EC2 instances running in private subnets.

Amazon RDS stores the WordPress database, while Amazon EFS is used to share uploaded media between the EC2 instances.

The application is deployed across two Availability Zones for better availability.

The architecture diagram is available in:

`architecture-diagram.png`

## Documentation

More information can be found in the `docs` folder:

- `requirements.md`
- `setup.md`
- `well-architected.md`
- `challenges-and-improvements.md`
