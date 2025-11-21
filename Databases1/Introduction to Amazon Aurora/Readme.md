# **Introduction to Amazon Aurora – AWS Re:start Lab**  
**By Mokgadi Selepe**

Today was my first time working with **Amazon Aurora** and wow – it really does feel like MySQL on steroids! I created a real Aurora MySQL-compatible cluster, connected to it from an EC2 instance, and ran queries like I normally do with regular MySQL. Everything just worked, but behind the scenes it’s way faster and more reliable.

## What I Did – Step by Step

### 1. Created an Amazon Aurora MySQL Cluster
- Went to RDS → Create database → Chose **Amazon Aurora** with MySQL compatibility  
- DB cluster identifier: `aurora`  
- Master username: `admin` | Password: `admin123` (yes, I know – only for the lab!)  
- Instance class: `db.t3.medium`  
- Placed it in the existing **LabVPC** and used the pre-made **dbsubnetgroup** and **DBSecurityGroup**  
- Created an initial database called `world`  
- Hit create and watched it go from “Creating” → “Available” in a few minutes  
- Copied the **writer endpoint** (looks like `aurora-xxxxxx.cluster-xxxxxx.region.rds.amazonaws.com`)

### 2. Jumped onto the Command Host (EC2 Linux instance)
- Found the EC2 instance labelled “Command Host”  
- Connected using **Session Manager** → instant terminal, no SSH keys needed!

### 3. Installed the MySQL client and connected to Aurora
Since Aurora is MySQL-compatible but the instance didn’t have the client yet:
```bash
sudo yum install mariadb -y
```
Then connected using the writer endpoint:
```bash
mysql -h aurora.xxxx.region.rds.amazonaws.com -u admin -p
```
Typed the password → boom, I was inside my Aurora database!

### 4. Created a Table and Played with Data
Switched to the `world` database and built a quick `country` table:
```sql
USE world;

CREATE TABLE country (
    Code CHAR(3) PRIMARY KEY,
    Name CHAR(52),
    Continent CHAR(20),
    Region CHAR(26),
    Population INT,
    GNP DECIMAL(10,2)
);
```
Inserted five countries I really like:
```sql
INSERT INTO country VALUES
('ZAF','South Africa','Africa','Southern Africa',60000000,450000.00),
('AUS','Australia','Oceania','Australia and New Zealand',26000000,1500000.00),
('IRL','Ireland','Europe','British Islands',5000000,400000.00),
('THA','Thailand','Asia','Southeast Asia',70000000,550000.00),
('BRA','Brazil','South America','South America',215000000,2100000.00);
```
Then ran my first real query on Aurora:
```sql
SELECT Name, GNP, Population 
FROM country 
WHERE GNP > 350000 AND Population > 10000000;
```
Result → Australia and Thailand! Exactly what I expected.

## What I Learned
- Aurora feels 100% like normal MySQL – same commands, same client  
- You connect using the **cluster endpoint** (writer for read/write, reader for read-only)  
- RDS + Aurora handles all the heavy lifting: replication, backups, failover  
- Way faster than regular RDS MySQL (I could feel it even in this small lab)  
- Perfect for apps that need high performance and high availability

**Lab completed – I now have hands-on experience creating and using an Amazon Aurora cluster!**  
Next stop: Aurora Serverless and read replicas. I’m officially in love with this service!

-Mokgadi: mokgadi9939@gmail.com
