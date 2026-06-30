# cloudwithlarry — Lab 3: VPC + RDS Two-Tier App

## What I Built
- Custom VPC (10.0.0.0/16) with 2 public + 2 private subnets across 2 AZs
- Two security groups: web-sg (HTTP/SSH) and db-sg (MySQL from web-sg only)
- EC2 web server in public subnet running Nginx
- RDS MySQL 8.4 database in private subnets (Single-AZ, free tier)
- Verified EC2 → RDS connectivity with real SQL queries

## AWS Resources Created
- VPC: cloudwithlarry-week2-vpc (10.0.0.0/16)
- Subnets: 2 public (10.0.0.0/20, 10.0.16.0/20), 2 private (10.0.128.0/20, 10.0.144.0/20)
- Security Groups: cloudwithlarry-web-sg, cloudwithlarry-db-sg
- EC2 Instance: cloudwithlarry-web (Ubuntu 24.04, t2.micro)
- RDS Instance: cloudwithlarry-db (MySQL 8.4, db.t3.micro)
- RDS Endpoint: cloudwithlarry-db.co7megiq4jda.us-east-1.rds.amazonaws.com

## Major Debugging Journey (6+ hours!)
1. Auto-assign public IP disabled at subnet level — fixed by editing subnet settings
2. SSH security group rule reverted to stale IP despite console showing 0.0.0.0/0
   — discovered via AWS CLI that console UI wasn't reflecting actual API state
3. Used AWS CloudShell to rule out local ISP/network blocking port 22
4. Used AWS CLI describe-instances to find correct (non-terminated) instance ID
5. Discovered the AMI used was Ubuntu 24.04, not Amazon Linux —
   required `ubuntu` username instead of `ec2-user`
6. Fixed security group rule via CLI commands (revoke + authorize)
   for guaranteed accuracy over console UI

## Commands Used
```bash
mysql -h cloudwithlarry-db.co7megiq4jda.us-east-1.rds.amazonaws.com -u admin -p
CREATE DATABASE cloudwithlarry_db;
USE cloudwithlarry_db;
CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    course VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
INSERT INTO students (name, course) VALUES
('Lawrence Koomson', 'Information Technology'),
('Emmanuel Sakyi Butuakwah', 'Information Technology'),
('Twumasi Felix', 'Information Technology');
SELECT * FROM students;
```

## Skills Learned
- VPC design — public vs private subnets
- Security groups as layered firewalls
- Network ACLs vs Security Groups
- AWS CloudShell for network-independent debugging
- AWS CLI for verifying and fixing console UI inconsistencies
- RDS MySQL provisioning and connection
- Two-tier application architecture
- Reading EC2 system/boot logs for diagnostics
- AMI-to-username mapping (Amazon Linux vs Ubuntu)