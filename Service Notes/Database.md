Here is your file **strictly formatted for GitHub Markdown**, clean, consistent, and ready to paste directly into a README.md.

---

````markdown
# AWS re/Start Database Labs Portfolio
**Author:** Mokgadi Selepe  
**Date:** November 26, 2025  

---

## Overview
This portfolio summarizes the database-focused labs completed during the AWS re/Start program. These labs covered:

- Relational database setup using **Amazon RDS** and **Amazon Aurora**
- SQL operations: SELECT, INSERT, UPDATE, DELETE, ALTER, GROUP BY, window functions
- Data filtering with WHERE, BETWEEN, LIKE
- NoSQL data modeling using **Amazon DynamoDB**
- EC2 as a command host with MySQL/MariaDB

This showcases hands-on experience in deploying and managing cloud-based databases.

---

# Lab 1: Build Your DB Server and Interact With Your DB Using an App (Amazon RDS)
**Objective:** Launch an RDS MySQL database, configure access, and test using a web application.

### Steps
1. **Created RDS Security Group** (port 3306 open to Web SG)  
2. **Created DB Subnet Group** across two private subnets  
3. **Launched RDS Instance**
   - MySQL engine  
   - db.t3.medium  
   - Multi-AZ enabled  
   - DB name: `world`  
   - User: `admin`  
4. **Connected Web App** using DB endpoint and tested CRUD operations

### Key Learnings
- Multi-AZ provides failover
- Security groups control access
- RDS integrates easily with applications

---

# Lab 2: Database Table Operations
**Objective:** Create, modify, and delete databases and tables using SQL.

### Key SQL Examples
```sql
CREATE DATABASE world;

CREATE TABLE world.country (
  Code CHAR(3) NOT NULL,
  Name CHAR(52) NOT NULL,
  Continent ENUM('Asia','Europe','North America','Africa','Oceania','Antarctica','South America') NOT NULL,
  PRIMARY KEY (Code)
);

ALTER TABLE world.country CHANGE Conitinent Continent ENUM('Asia','Europe');

DROP TABLE world.country;
DROP DATABASE world;
````

### Key Learnings

* CREATE, SHOW, ALTER, and DROP are essential SQL admin tools
* Primary keys ensure unique identification

---

# Lab 3: Inserting Data into a Database

**Objective:** Use INSERT, UPDATE, DELETE, and import SQL files.

### Key SQL Examples

```sql
INSERT INTO world.country VALUES ('IRL','Ireland','Europe', ...);

UPDATE world.country SET Population = 0;

SET FOREIGN_KEY_CHECKS = 0;
DELETE FROM world.country;

mysql -u root -p < /home/ec2-user/world.sql
```

### Key Learnings

* INSERT adds new data
* UPDATE modifies existing rows
* DELETE removes rows
* SQL file imports enable fast data loading

---

# Lab 4: Introduction to Amazon Aurora

**Objective:** Create and connect to an Aurora MySQL cluster.

### SQL Examples

```sql
CREATE TABLE country (
  Code CHAR(3),
  Name CHAR(52)
);

INSERT INTO country VALUES ('AUS','Australia','Oceania', ...);

SELECT * FROM country 
WHERE GNP > 35000 AND Population > 10000000;
```

### Key Learnings

* Aurora is MySQL-compatible and highly performant
* EC2 can connect to Aurora via the MySQL client

---

# Lab 5: Introduction to Amazon DynamoDB

**Objective:** Create a NoSQL DynamoDB table and manage items.

### Operations

* Created table: **Music** (PK: Artist, SK: Song)
* Added and updated items
* Performed Query and Scan operations
* Deleted table

### Key Learnings

* DynamoDB is schema-less
* Query = key-based lookup
* Scan = full-table search

---

# Lab 6: Organizing Data

**Objective:** Use GROUP BY and window functions.

### SQL Examples

```sql
SELECT Region, SUM(Population) AS TotalPopulation
FROM country
GROUP BY Region;

SELECT Name, Population,
       RANK() OVER (PARTITION BY Region ORDER BY Population DESC) AS Rank
FROM country;
```

### Key Learnings

* GROUP BY aggregates data
* OVER enables ranking and advanced analytics

---

# Lab 7: Performing a Conditional Search

**Objective:** Use WHERE, BETWEEN, LIKE for filtering.

### SQL Examples

```sql
SELECT * FROM country 
WHERE Population BETWEEN 50000000 AND 100000000;

SELECT * FROM country 
WHERE Region LIKE '%Southern%';

SELECT SUM(Population)
FROM country
WHERE Continent = 'Europe';
```

### Key Learnings

* WHERE filters rows
* BETWEEN handles ranges
* LIKE performs pattern matching

---

# Lab 8: Selecting Data from a Database

**Objective:** Use SELECT, aliases, and ORDER BY.

### SQL Examples

```sql
SELECT Name, SurfaceArea AS 'Surface Area' FROM country;

SELECT * FROM country ORDER BY Population DESC;

SELECT Name, Capital, Region
FROM country
WHERE Population > 50000000
  AND Continent = 'Europe';
```

### Key Learnings

* SELECT retrieves specific columns
* ORDER BY sorts results
* Aliases (AS) improve readability

---

# Lab 9: Working with Functions

**Objective:** Use aggregate and string functions.

### SQL Examples

```sql
SELECT SUM(Population), AVG(Population), COUNT(*) FROM country;

SELECT SUBSTRING_INDEX(Region, '/', 1) AS Region1,
       SUBSTRING_INDEX(Region, '/', -1) AS Region2
FROM country;

SELECT DISTINCT Region FROM country;
```

### Key Learnings

* Aggregation: SUM, AVG, MAX, MIN, COUNT
* String functions: SUBSTRING_INDEX, LENGTH
* DISTINCT removes duplicates

---

# Overall Concepts Learned

| Category         | Concepts                                              |
| ---------------- | ----------------------------------------------------- |
| Relational Setup | RDS, Aurora, Multi-AZ, Subnet Groups, Security Groups |
| SQL Basics       | CREATE, ALTER, DROP, INSERT, UPDATE, DELETE, SELECT   |
| Advanced SQL     | GROUP BY, OVER, RANK, LIKE, BETWEEN, DISTINCT         |
| NoSQL            | DynamoDB Tables, Items, Query, Scan                   |

---

# Conclusion

These labs provided practical experience in cloud-based database management, SQL querying, and NoSQL data modeling. This portfolio reflects strong foundational skills in cloud data operations.

---

**Contact:**
📧 **[mokgadi9939@gmail.com](mailto:mokgadi9939@gmail.com)**

```

---

If you want, I can also generate:

✅ A Table of Contents  
✅ Badges (AWS, SQL, DynamoDB)  
✅ A polished GitHub portfolio version with sections + styling  

Just tell me!
```
