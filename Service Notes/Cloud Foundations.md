````markdown
# AWS EC2 Lab – Launching, Configuring, and Managing a Web Server
**Author:** Mokgadi Selepe  
**Date:** November 2025  

---

## Objective
Practice core Amazon EC2 operational skills, including:

- Launching EC2 instances  
- Configuring security groups  
- Monitoring and troubleshooting  
- Resizing instance types and EBS volumes  
- Using user data scripts for automation  
- Enabling/validating termination protection  

---

# Task 1: Launch an EC2 Web Server Instance

### **Instance Specifications**
- **Name:** `Web Server`
- **AMI:** Amazon Linux 2023 (64-bit x86)
- **Instance Type:** `t3.micro` (Free Tier)
- **Key Pair:** Newly created (later not needed)
- **Networking:**
  - Default VPC  
  - Auto-assign public IP enabled  
- **Security Group (initial):**
  - SSH (22) only
- **Storage:** 8 GiB gp3 (default)
- **Termination Protection:** Enabled

### **User Data Script**
```bash
#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
echo "<h1>Hello From Your Web Server!</h1>" > /var/www/html/index.html
````

### Outcome

The EC2 instance launched successfully, installed Apache automatically, and served a custom HTML message.

---

# Task 2: Monitor the Instance

* Viewed **2/2 status checks** under the EC2 Status Checks tab
* Observed metrics via **CloudWatch graphs** (CPU, network traffic, etc.)
* Captured **instance screenshot and system logs** to verify successful boot and Apache service

---

# Task 3: Update Security Group & Access Web Server

### Issue

The web server wasn’t accessible in the browser.

### Root Cause

HTTP (port 80) was not allowed in the security group.

### Fix Applied

Added inbound rule:

| Type | Protocol | Port | Source    |
| ---- | -------- | ---- | --------- |
| HTTP | TCP      | 80   | 0.0.0.0/0 |

### Result

`Hello From Your Web Server!` successfully displayed in the browser.

### Key Learning

Security groups are **stateful firewalls**—even if the server is running, traffic won't reach it unless rules allow it.

---

# Task 4: Resize Instance (Instance Type + EBS Volume)

## **4.1 Change Instance Type**

Steps:

1. Stopped the instance
2. Changed instance type → `t3.small`
3. Restarted instance
4. Verified web server still running

## **4.2 Increase EBS Volume Size**

* Modified volume from **8 GiB → 10 GiB**
* Extended filesystem inside the instance:

```bash
lsblk
sudo growpart /dev/xvda 1
sudo xfs_growfs -d /
```

### Result

Disk space successfully expanded with no data loss.

### Key Learning

* Instance must be **stopped** to change instance type
* EBS volumes can be resized while running, but filesystem must be manually extended

---

# Task 5: Test Termination Protection

* Attempted instance termination → **blocked** due to protection
* Disabled protection → Instance successfully terminated

### Key Learning

Termination protection prevents accidental deletion—great for production environments.

---

# Summary of Key AWS Concepts Learned

| Concept                | Task Reference | Key Takeaway                              |
| ---------------------- | -------------- | ----------------------------------------- |
| EC2 Instance Launch    | Task 1         | AMI, instance type, user data, key pairs  |
| Security Groups        | Tasks 1 & 3    | Must allow inbound HTTP for web access    |
| User Data Scripts      | Task 1         | Automates initial server configuration    |
| Monitoring             | Task 2         | Use CloudWatch graphs and system logs     |
| Instance Type Resizing | Task 4         | Requires stopping the instance            |
| EBS Volume Expansion   | Task 4         | Resize → grow partition → grow filesystem |
| Termination Protection | Task 5         | Prevents accidental deletion              |

---

# Final Status

Successfully launched, configured, secured, scaled, monitored, and safely terminated an EC2 web server instance.

A complete hands-on introduction to real-world EC2 administration!

---

**Contact:**
**Mokgadi:** [mokgadi9939@gmail.com](mailto:mokgadi9939@gmail.com)

```

