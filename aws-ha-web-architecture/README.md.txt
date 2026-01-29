# Highly Available Web Architecture using AWS

This project demonstrates how to build a highly available web application using:

- VPC
- Public Subnets
- Internet Gateway
- Route Tables
- Security Groups
- EC2
- Application Load Balancer
- Target Group
- Launch Template
- Auto Scaling Group

## Architecture

Internet → ALB → Target Group → Auto Scaling (2 EC2 instances)

## Steps Followed

1. Created custom VPC with CIDR 10.0.0.0/16
2. Created 2 public subnets in different AZs
3. Created and attached Internet Gateway
4. Created route table and added route 0.0.0.0/0 → IGW
5. Created Security Group allowing HTTP and SSH
6. Launched EC2 instance and installed Apache
7. Created Target Group and verified health
8. Created Application Load Balancer and attached TG
9. Created Launch Template with Apache installation in user data
10. Created Auto Scaling Group with desired capacity 2
11. Verified load balancing by changing pages in both instances

## Commands Used in User Data

```bash
#!/bin/bash
sudo apt update -y
sudo apt install apache2 -y
sudo systemctl start apache2
sudo systemctl enable apache2
echo "Hello from Auto Scaling Instance" > /var/www/html/index.html


## Result

The Load Balancer successfully distributes traffic between multiple EC2 instances.

Both instances are healthy in the target group and Auto Scaling automatically maintains the desired number of instances.

Screenshots are attached below as proof of working architecture.

