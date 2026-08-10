# Challenges and Future Improvements

## Challenges

### WordPress Login

I had a problem where WordPress accepted my login details but returned me to the login page.

Because there were two EC2 instances behind the ALB, the login session could move between the instances.

I enabled ALB stickiness and the login worked correctly.

### Understanding the Connections

One of the main challenges was understanding how all the AWS services work together.

Building the project helped me understand the flow from the ALB to EC2, RDS, EFS, Auto Scaling, IAM, and CloudWatch much better.

## Future Improvements

### HTTPS

The current demo uses HTTP.

For a production application, I would add HTTPS with an SSL/TLS certificate and a custom domain.

### WordPress Sessions

Instead of depending on ALB stickiness, I would configure the WordPress instances to use the same authentication keys and salts.

### Infrastructure as Code

I created this environment mainly through the AWS Console.

In the future, I would use Terraform or CloudFormation so the infrastructure can be created automatically and consistently.

### More Testing

I tested the failure of one EC2 instance.

For a production system, I would also test RDS failover, higher traffic, backup and recovery, and other failure scenarios.
