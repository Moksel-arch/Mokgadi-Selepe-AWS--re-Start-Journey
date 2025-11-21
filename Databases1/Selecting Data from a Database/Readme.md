# **AWS re/Start – Selecting Data from a Database Lab**
### My very first proper SQL adventure on a real MySQL instance in AWS!

Hey GitHub! Still deep in the AWS re/Start programme and today we finally got to play with actual databases instead of just reading about them. This lab was all about connecting to a MySQL instance and running SELECT queries on the famous world database (the one with country, city, and countrylanguage tables).

## What I Did – Step by Step

1. Connected to the Command Host  
   Used Session Manager to jump onto a special EC2 instance that already has the MySQL client installed. Felt like a hacker when the terminal finally said “Welcome to the MySQL monitor” 😎

2. Logged into the database  
   ```bash
   mysql -h <endpoint> -u admin -p
   ```
   Typed the password (obviously not sharing that here) and boom – inside!

3. Checked what databases exist  
   ```sql
   SHOW DATABASES;
   ```
   Saw the world database sitting there waiting for me.

4. Switched to the world database  
   ```sql
   USE world;
   ```

5. Started exploring the country table  
   - Saw all the data: `SELECT * FROM country;`
   - Counted rows: `SELECT COUNT(*) FROM country;`
   - Grabbed just the columns I wanted:  
     ```sql
     SELECT Name, Capital, Region, SurfaceArea, Population FROM country;
     ```

6. Made things prettier with AS  
   ```sql
   SELECT Name AS "Country Name",
          Capital,
          SurfaceArea AS "Surface Area (sq km)",
          Population
   FROM country;
   ```

7. Sorted by population (biggest first)  
   ```sql
   SELECT Name, Population 
   FROM country 
   ORDER BY Population DESC;
   ```

8. Used WHERE to filter  
   ```sql
   SELECT * FROM country WHERE Population > 50000000;
   ```

9. Combined conditions with AND  
   ```sql
   SELECT Name, Capital, Region, Population 
   FROM country 
   WHERE Population > 50000000 AND Region = 'Southern Europe';
   ```
   (Spoiler: only Italy made the cut!)

## Challenge – Find the Southern European giant
The question was: “Which country in Southern Europe has a population over 50 million?”  
My final winning query:
```sql
SELECT Name, Capital, Region, SurfaceArea AS "Surface Area", Population 
FROM country 
WHERE Region = 'Southern Europe' AND Population > 50000000;
```
Answer: Italy 🇮🇹 (of course)

## What I Learned Today
- SELECT is basically asking the database questions in English-but-make-it-code
- WHERE = the bouncer that only lets the rows you want through
- ORDER BY + DESC = instant “top 10 richest/biggest/etc.” lists
- AS is my new best friend for readable column names
- You can chain conditions with AND, OR, etc. – feels like real power now

Honestly, after this lab I actually felt like I could query pretty much anything. Give me a database and I’ll find whatever you need!

Still so much more to learn, but this one felt like a proper milestone.

- Mokgadi: mokgadi9939@gmail.com  
