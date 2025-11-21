# **Performing a Conditional Search – AWS Re:start Lab**
**By Mokgadi Selepe**

Today was all about asking the database smart questions! I spent the whole lab filtering data with **WHERE**, **BETWEEN**, **LIKE**, and a bunch of other tricks. By the end I could find exactly what I wanted in seconds – felt like a real data detective.

## What I Did – From Simple Filters to Pro-Level Searches

### 1. Connected Like Always
- Session Manager → Command Host  
- `mysql -u root -p` → password `re:St@rt!9`  
- `USE world;` → ready to explore the three tables (country, city, countrylanguage)

### 2. My Favourite Queries From Today

```sql
-- Countries with population between 50 and 100 million
SELECT Name, Population 
FROM country 
WHERE Population BETWEEN 50000000 AND 100000000;
-- Got Brazil, Mexico, Germany, etc.
```

```sql
-- All countries in Europe (case-insensitive search)
SELECT Name, Continent, Population
FROM country
WHERE LOWER(Continent) = 'europe';
```

```sql
-- Countries whose name contains "land"
SELECT Name 
FROM country 
WHERE Name LIKE '%land%';
-- Finland, Poland, Thailand, Iceland... so many!
```

```sql
-- European countries sorted by population (biggest first)
SELECT Name, Population
FROM country
WHERE LOWER(Continent) = 'europe'
ORDER BY Population DESC;
```

```sql
-- Total population of Europe (with nice column name)
SELECT SUM(Population) AS TotalEuropePopulation
FROM country
WHERE LOWER(Continent) = 'europe';
-- Over 745 million people!
```

### 3. The Challenge – North America Stats
I had to calculate total surface area AND total population for North America:
```sql
SELECT 
    SUM(SurfaceArea) AS TotalSurfaceArea_km2,
    SUM(Population) AS TotalPopulation
FROM country
WHERE Region = 'North America';
```
Result was massive – Canada + USA really add up!

## What I Learned (These Are Now My Go-To Tools)
- `WHERE` + `AND` / `OR` → combine conditions  
- `BETWEEN` → cleaner than writing `>=` and `<=`  
- `LIKE '%something%'` → search inside text  
- `LOWER()` → ignore case when searching  
- Column aliases (`AS`) → make output actually readable  

**Lab completed – I can now slice and dice data however I want!**  
Next time someone says “show me all countries with X” I’m ready in 5 seconds flat.

-Mokgadi: mokgadi9939@gmail.com
