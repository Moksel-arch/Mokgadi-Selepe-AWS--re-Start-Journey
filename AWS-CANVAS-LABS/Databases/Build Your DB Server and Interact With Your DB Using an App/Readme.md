
# **Build Your DB Server and Interact With Your DB Using an App – AWS Re:start Lab** 
**By Mokgadi Selepe**

This was such a cool lab! I finally got to create a real MySQL database in the cloud using Amazon RDS, make it highly available, secure it properly, and then connect a web application to it. It felt like building a real-world backend from scratch.

## What I Built
- A Multi-AZ MySQL database on Amazon RDS (primary + standby in different Availability Zones)  
- Proper networking and security so only my web server can talk to the database  
- A working web app that saves and reads data from my RDS database  

## Step-by-Step What I Did

### 1. Created a Security Group for the Database
- Made a new security group called "DB Security Group"  
- Added an inbound rule: allow MySQL (port 3306) only from the Web Server’s security group  
- This way the database is completely locked down – no random internet access!

### 2. Created a DB Subnet Group
- Picked two private subnets in different Availability Zones  
- Created a subnet group named "DB Subnet Group"  
- This tells RDS where it’s allowed to place the database instances and makes sure it’s spread across AZs for high availability

### 3. Launched the Actual RDS Instance
- Engine: MySQL (latest version)  
- Template: Dev/Test  
- Instance class: db.t3.medium  
- Storage: General Purpose SSD  
- Multi-AZ deployment → automatic standby replica in another AZ  
- Attached my "DB Security Group" and "DB Subnet Group"  
- Set master username and password  
- Hit create and waited (it took a few minutes)  
- Once it said "Available", I copied the endpoint (something like mydb.xxxxx.amazonaws.com)

### 4. Connected the Web Application
- Grabbed the public IP of the lab’s web server  
- Opened http://<web-server-ip> in my browser  
- Clicked the RDS section in the app  
- Pasted my RDS endpoint, username, and password  
- The app connected instantly!  
- Tested it by adding, editing, and deleting contacts – everything was being saved straight to my cloud database  
- Behind the scenes, data is automatically replicated to the standby instance

## What I Learned
- RDS takes away all the boring admin stuff (backups, patching, replication)  
- Multi-AZ = if one zone goes down, the database stays up  
- Never open port 3306 to the whole internet – always lock it down with security groups  
- Web apps just need the endpoint, username, and password to talk to RDS – super simple!

## Final Architecture
Internet → Web Server (public subnet) → RDS MySQL (private subnets, Multi-AZ)

**Lab completed – my database is live, secure, highly available, and my web app is happily using it!**

Feeling very proud right now – I can actually build this in a real job tomorrow!

-Mokgadi: mokgadi9939@gmail.com
