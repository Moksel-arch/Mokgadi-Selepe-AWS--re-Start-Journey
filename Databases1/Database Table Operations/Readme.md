Mokgadi

# **Database Table Operations - AWS Re:start Lab**  
**By Mokgadi Selepe**

This was a hands-on lab where I practiced the most common SQL commands for creating, viewing, modifying, and deleting databases and tables on a MySQL instance running on AWS.

## What I Did

### 1. Connected to the Command Host
- Logged into the AWS Management Console  
- Found the lab-provided EC2 instance (the "Command Host")  
- Connected via Session Manager / SSH  
- Launched the MySQL client and connected to the local database  

### 2. Created a Database and a Table
- Checked existing databases with `SHOW DATABASES;`  
- Created a new database called `world`  
- Inside it, created a `country` table with several columns (Code, Name, Continent, Region, etc.)  
- Noticed I had typed `Conitinent` instead of `Continent` → fixed it using `ALTER TABLE`  
- Now the table was clean and ready!

### 3. Challenge 1 – Created a Simple City Table
```sql
CREATE TABLE world.city (
  `Name` CHAR(52),
  `Region` CHAR(26)
);
```
Both columns use fixed-length `CHAR` because that’s how the original world database stores them.

### 4. Dropped Tables
- Deleted the `city` table:  
  ```sql
  DROP TABLE world.city;
  ```
- Deleted the `country` table:  
  ```sql
  DROP TABLE world.country;
  ```

### 5. Cleaned Everything Up
- Verified no tables were left with `SHOW TABLES;`  
- Dropped the entire `world` database:  
  ```sql
  DROP DATABASE world;
  ```
- Confirmed it was gone with `SHOW DATABASES;`

## Key SQL Commands I Used

| Command              | What I Used It For                              |
|----------------------|--------------------------------------------------|
| `SHOW DATABASES;`    | List all databases                               |
| `CREATE DATABASE`   | Create the `world` database                      |
| `CREATE TABLE`      | Create `country` and `city` tables               |
| `ALTER TABLE`       | Fix the spelling mistake in the column name      |
| `SHOW TABLES;`      | Check which tables exist in the current database|
| `SHOW COLUMNS FROM` | See the structure of a table                     |
| `DROP TABLE`        | Permanently delete a table                       |
| `DROP DATABASE`     | Delete the entire database and everything in it |

## What I Learned
I now feel confident with the basic lifecycle of databases and tables:
- How to create them  
- How to inspect what’s there  
- How to fix small mistakes in the structure  
- How to completely remove things when they’re no longer needed  

These are the commands I’ll be using every day when working with relational databases!

**Lab completed successfully – everything created and cleanly removed!**
```
