# **AWS re/Start – Working with Functions Lab**
### My second SQL day and now we’re using actual FUNCTIONS (mind officially blown)

Still deep in the AWS re/Start database module and today we levelled up from basic SELECT to using all the cool built-in functions. Same setup as last time: Session Manager → Command Host → MySQL client → world database. But now we’re doing math and string magic inside SQL!

## What I Did Today

### 1. Connected like a pro 

### 2. Aggregation Functions – the “give me summaries” squad
```sql
SELECT 
  SUM(Population) AS "Total World Population",
  AVG(Population) AS "Average Country Population",
  MAX(Population) AS "Biggest Country",
  MIN(Population) AS "Smallest Country",
  COUNT(*) AS "Total Countries"
FROM country;
```
Result: Over 6 billion people, average ~26 million per country, China on top, Vatican at the bottom.

### 3. String Functions – because some data is messy
Found countries with "Southern" in the region:
```sql
SELECT Name, Region 
FROM country 
WHERE Region LIKE '%Southern%';
```

Counted characters in region names:
```sql
SELECT Region, LENGTH(Region) AS "Length"
FROM country 
WHERE LENGTH(Region) < 10;
```

Removed duplicates:
```sql
SELECT DISTINCT Region FROM country;
```

### 4. The Challenge – Split "Micronesia/Caribbean" like a boss
Some countries have region = "Micronesia/Caribbean" (yes, really). Task was to split it into two columns.

My winning query:
```sql
SELECT 
  Name,
  Region,
  SUBSTRING_INDEX(Region, '/', 1) AS "Region Name 1",
  SUBSTRING_INDEX(Region, '/', -1) AS "Region Name 2"
FROM country 
WHERE Region = 'Micronesia/Caribbean';
```
Worked perfectly! Every country now shows:
- Region Name 1 → Micronesia
- Region Name 2 → Caribbean

## Functions I Now Love
- SUM(), AVG(), MAX(), MIN(), COUNT() → aggregation
- SUBSTRING_INDEX() → split strings by delimiter
- LENGTH() → count characters
- TRIM() → clean spaces (tried it, worked like magic)
- DISTINCT → no more duplicates
- LIKE → search with wildcards

## Final Thoughts
I used to think databases just stored stuff. Now I know they can calculate, clean, and transform data on the fly. This is actually powerful! I can already imagine using these at a real job – “Hey boss, want to know average order value by region? Give me 10 seconds.”

Next stop: JOINs (apparently that’s when it gets really fun).

Still grinding through re/Start, one query at a time.

- Mokgadi: mokgadi9939@gmail.com  
