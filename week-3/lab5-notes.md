# cloudwithlarry — Lab 5: Auto Scaling + ALB

## What I Built
- Application Load Balancer (internet-facing)
- Auto Scaling Group with 2 EC2 instances
- Launch Template with Nginx + metadata script
- Target Group with health checks
- Traffic distributed across 2 Availability Zones

## AWS Resources Created
- Security Group: cloudwithlarry-alb-sg (HTTP from internet)
- Security Group: cloudwithlarry-asg-sg (HTTP from ALB only)
- Launch Template: cloudwithlarry-launch-template
- Load Balancer: cloudwithlarry-alb
- Target Group: cloudwithlarry-tg
- Auto Scaling Group: cloudwithlarry-asg
  - Desired: 2, Min: 1, Max: 4
  - CPU target tracking: 50%

## ALB DNS Name
cloudwithlarry-alb-1163054908.us-east-1.elb.amazonaws.com

## Proof of Load Balancing
Refresh 1: Instance i-0ffc9b6461640402a (us-east-1a)
Refresh 2: Instance i-0b12aa0f1625641d3 (us-east-1b)
Traffic alternating between 2 AZs = High Availability!

## Architecture
Internet → ALB → Target Group → ASG
                                 ├── EC2 (us-east-1a)
                                 └── EC2 (us-east-1b)

## Skills Learned
- Application Load Balancer configuration
- Launch Templates for Auto Scaling
- Auto Scaling Groups with health checks
- Target tracking scaling policies
- High availability across multiple AZs
- EC2 metadata service for instance info
- Security group chaining (ALB → EC2)