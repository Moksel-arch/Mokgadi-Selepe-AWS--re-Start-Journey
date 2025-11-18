#**Build Your DB Server and Interact With Your DB Using an App**

**Overview**
This project demonstrates how to set up a relational database in the cloud using Amazon RDS and connect it to a web application. The goal is to create a secure, highly available database and interact with it through an app.


**What I have Learned**

How to launch an Amazon RDS DB instance.
Configure security groups for controlled access.
Create a DB Subnet Group for high availability.
Deploy a Multi-AZ MySQL database.
Connect and interact with the database using a web application.


**Steps Covered**
1. Create a Security Group

Created a security group called DB Security Group.
Added a rule to allow MySQL/Aurora traffic on port 3306 from the web server’s security group.
This acts like a firewall to protect the database.

2. Create a DB Subnet Group

Selected two private subnets in different Availability Zones.
Grouped them into a DB Subnet Group for redundancy and security.
Ensures high availability and disaster recovery.

3. Launch an Amazon RDS DB Instance

Created a MySQL database instance with Multi-AZ deployment.
Configured:

Instance class: db.t3.medium
Storage: General Purpose SSD
Latest MySQL version
Dev/Test template

Once deployed, received an endpoint URL for database connectivity.

4. Interact with the Database

Opened a web application on the web server.
Configured the app with:

Database endpoint
Username and password

Tested by adding, editing, and deleting contacts.
Verified data replication across Availability Zones.

**Architecture**
The final setup includes:

Amazon RDS DB Instance (Multi-AZ)
Web Server connected to the database
Security Groups for controlled access
DB Subnet Group for high availability

**Technologies Used**
Amazon RDS
MySQL
AWS VPC
Web Application (HTML/PHP or similar)


**How to Use**
Clone this repository:
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
