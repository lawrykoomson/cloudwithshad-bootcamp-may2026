# cloudwithlarry — Lab 2: EC2 Web Server

## What I Built
- Launched a t2.micro EC2 instance on Amazon Linux 2023
- Created SSH key pair and security group
- SSH'd into a real Linux server from my laptop in Accra
- Installed and configured Nginx web server
- Deployed a custom branded HTML page (cloudwithlarry)
- Built and ran a Node.js API returning random AWS facts

## AWS Resources Created
- Key Pair: cloudwithlarry-key
- Security Group: cloudwithlarry-web-sg
- EC2 Instance: cloudwithlarry-web-server (t2.micro)
- Region: us-east-1
- Public IP: 54.90.92.63 (stopped after lab)

## Ports Opened
- Port 22 (SSH) — My IP only
- Port 80 (HTTP) — Anywhere
- Port 3000 (Node.js API) — Anywhere

## Commands Used
chmod 400 cloudwithlarry-key.pem
ssh -i cloudwithlarry-key.pem ec2-user@54.90.92.63
sudo dnf update -y
sudo dnf install -y nginx
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl status nginx
sudo dnf install -y nodejs
node ~/app.js

## Live URLs (while instance running)
- HTML Page: http://54.90.92.63
- Node.js API: http://54.90.92.63:3000

## Skills Learned
- EC2 instance launching and management
- SSH key pairs and Linux permissions (chmod)
- Security groups as virtual firewalls
- Nginx installation and configuration
- Node.js API deployment on EC2
- Linux commands (dnf, systemctl, tee, cat)