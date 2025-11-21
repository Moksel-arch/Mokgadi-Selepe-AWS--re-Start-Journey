# **Insert, Update, and Delete Data in a Database – AWS Re:start Lab**
**By Mokgadi Selepe**

Today I spent the whole lab inside the MySQL terminal playing with real data! I inserted rows, updated them, deleted everything (on purpose), and then brought the whole world database back to life with one SQL file. It felt like being a real DBA for a day.

## What I Did Step-by-Step

### 1. Connected to the Database
- Jumped onto the Command Host EC2 instance via Session Manager  
- Logged into MySQL as root with the password `re:St@rt!9`  
- Ran `SHOW DATABASES;` → the `world` database was already there waiting for me

### 2. Inserted My Own Data
Added two missing countries that I love:
```sql
INSERT INTO world.country (Code, Name, Continent, Region, SurfaceArea, IndepYear, Population, LifeExpectancy, GNP, GNPOld, LocalName, GovernmentForm, HeadOfState, Capital, Code2)
VALUES 
('IRL', 'Ireland', 'Europe', 'British Islands', 70273, 1921, 4987000, 78.9, 223500, 200000, 'Ireland', 'Republic', 'Mary McAleese', 123, 'IE'),
('AUS', 'Australia', 'Oceania', 'Australia and New Zealand', 7741220, 1901, 25690000, 82.4, 1090000, 1050000, 'Australia', 'Constitutional Monarchy', 'Elizabeth II', 135, 'AU');
```
Checked with:
```sql
SELECT * FROM world.country WHERE Code IN ('IRL','AUS');
```
They were there – felt so good seeing my own rows in the table!

### 3. Updated Data (and learned a scary lesson)
First I accidentally set everyone's population to 0:
```sql
UPDATE world.country SET Population = 0;
```
Then fixed it (kind of) by setting Population and SurfaceArea to 100 for everyone. Lesson learned: **never run UPDATE without a WHERE clause in real life!**

### 4. Deleted Everything
Turned off foreign key checks because other tables link to country:
```sql
SET FOREIGN_KEY_CHECKS = 0;
DELETE FROM world.country;
```
Table completely empty – scary but cool.

### 5. Brought the Database Back to Life
Exited MySQL, then imported the full dataset in one command:
```bash
mysql -u root -p world < /home/ec2-user/world.sql
```
This one file:
- Created the `city` and `countrylanguage` tables  
- Filled all three tables (`country`, `city`, `countrylanguage`) with real data  

Logged back in and ran:
```sql
SHOW TABLES;
SELECT COUNT(*) FROM country;   -- 239 rows!
SELECT * FROM city LIMIT 5;
SELECT * FROM countrylanguage LIMIT 5;
```
Everything was back and looking perfect.

## Key Takeaways
- `INSERT INTO` → add new rows  
- `UPDATE` → change existing data (be careful!)  
- `DELETE` → remove rows (add WHERE or cry later)  
- Importing a `.sql` file is the fastest way to load real data  
- Always verify with `SELECT` after every change  

**Lab completed – I can now confidently add, change, delete, and restore data like a pro!**

-Mokgadi: mokgadi9939@gmail.com
