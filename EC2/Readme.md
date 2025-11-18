**AWS EC2 Instance Management and Web Server Deployment**

This repository documents a hands‑on project where I set up, configured, and managed a virtual server (EC2 instance) on Amazon Web Services (AWS) Elastic Compute Cloud (EC2). The project follows a step‑by‑step approach to launch a public‑facing instance, deploy a basic web service, and practice essential lifecycle management and security best practices.

**Project Overview**

The goal of this project was to gain practical exposure to the AWS console and EC2 features, including networking, security groups, instance configuration, and persistent storage management. The documentation was originally created by MOKGADI SELEPE.

**Key Topics Covered**

**The project successfully completed and documented the following five core tasks:**

1. EC2 Instance Launch – Provisioning an EC2 instance using an Amazon Machine Image (AMI) and configuring network settings, including the Security Group (firewall rules).
2. Web Server Setup – Connecting to the launched instance (e.g., via SSH or RDP) and installing the necessary software (e.g., IIS, Apache, or Nginx) to run a basic web server.
3. Instance Modification & Scaling – Practicing resource management by stopping and starting the instance to apply changes, including upgrading the Instance Type (e.g., from t2.micro to t3.small) to increase memory and CPU capacity.
4. Elastic Block Store (EBS) Management – Demonstrating how to increase the size of the persistent storage (EBS volume) attached to the EC2 instance to meet growing storage needs.
5. Termination Protection Test – Implementing a crucial security feature by enabling Termination Protection on the instance to prevent accidental deletion, and testing the failure message upon attempted termination.

**Learning Outcomes**

**The exercises in this project solidified the following practical AWS operational skills:**

- Understanding the instance lifecycle (Pending, Running, Stopping, Terminated).
- Ability to scale compute resources by changing instance types.
- Ability to scale storage resources by modifying EBS volume sizes.
- Implementing basic security measures using Security Groups and Termination Protection.
- Basic command‑line/server administration skills required to deploy applications.

**Technologies Used**
- Amazon Web Services (AWS): Primary cloud platform.
- AWS EC2: Core virtual computing service.
- AWS EBS: Persistent block storage service.
- Amazon Linux / Windows Server: Operating system environments (depending on the documented steps).
