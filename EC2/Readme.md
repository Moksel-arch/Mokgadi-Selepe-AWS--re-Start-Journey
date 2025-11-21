# **EC2 Lab – Mokgadi Selepe**

This is my write-up (more like a personal log) of the Amazon EC2 hands-on lab I did. I basically went through launching a web server, fixing the usual “why can’t I see my page” problem, resizing the instance, and finally cleaning everything up safely.

## What I did – step by step

### 1. Launching the EC2 instance
- Named it “Web Server”
- Chose Amazon Linux 2023 AMI
- Went with the free-tier t3.micro (2 vCPUs, 1 GiB RAM)
- Created a new security group but accidentally removed SSH (on purpose for extra security at first)
- Kept the default 8 GB gp3 root volume
- Turned on termination protection so I wouldn’t delete it by mistake
- Added a simple user-data script to install Apache and serve a “Hello From Your Web Server!” page
- Launched it and waited until it showed “running”

At the end of this step the instance was up and I could already see it had a public IP/DNS.

### 2. Monitoring the instance
Just normal health checks:
- Status Checks → 2/2 checks passed
- Looked at the Monitoring tab (CPU was basically idle, as expected)
- Grabbed a couple of console screenshots to see the boot process

Everything looked healthy.

### 3. Fixing the web server access (Security Group)
Tried opening the public IP in my browser → “can’t reach this page” (classic).

Realised I never opened port 80!  
So I:
- Went to the security group
- Added an inbound rule: HTTP (port 80) from 0.0.0.0/0
- Refreshed the browser → “Hello From Your Web Server!”

Lesson learned: security groups are firewalls, nothing gets in unless you explicitly allow it.

### 4. Resizing the instance (instance type + EBS volume)
Wanted to see how upgrading works, so I:
- Stopped the instance
- Changed instance type from t3.micro → t3.small (2 vCPUs, 2 GiB RAM)
- Increased the root volume from 8 GB → 10 GB
- Started the instance again
- Extended the file system inside the OS so the extra 2 GB became usable

Everything came back online with more memory and a tiny bit more disk space.

### 5. Testing Termination Protection
Just to be sure the safety net works:
- Tried to terminate → got the expected error because protection was enabled
- Disabled termination protection
- Terminated the instance for real

Instance deleted, no surprises.

## What I take away from this lab
- EC2 is basically a virtual machine in the cloud, but you control networking with security groups
- Always remember to open the ports you need (port 80 for web servers!)
- You can upgrade/downgrade instance types and grow disks on the fly (just have to stop/start for type changes)
- Termination protection is super useful so you don’t accidentally blow away something important

That’s it! Pretty straightforward once you get the security group part right. Feel free to use this as a cheat-sheet if you’re doing the same lab.

– Mokgadi
