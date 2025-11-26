# **Organizing Data with GROUP BY and Window Functions – AWS Re:start Lab**  
**By Mokgadi Selepe**

Today I levelled up my SQL game big time! I spent the whole lab inside the `world` database playing with **GROUP BY**, **SUM()**, and especially the super powerful **OVER()** clause with window functions. I now finally get why people say window functions are life-changing.

## What I Did – From Basic Grouping to Ranking Like a Pro

### 1. Connected to the Command Host
- Jumped onto the EC2 “Command Host” via Session Manager  
- Logged into MySQL with the usual `re:St@rt!9` password  
- Switched to the `world` database that already had the `country`, `city`, and `countrylanguage` tables

### 2. Explored Australia & New Zealand Region
First I just wanted to see the countries there, sorted by population:
```sql
SELECT Name, Population 
FROM country 
WHERE Region = 'Australia and New Zealand' 
ORDER BY Population DESC;
```
Australia → New Zealand → Fiji → etc. Makes sense!

### 3. Total Population per Region (Classic GROUP BY)
```sql
SELECT Region, SUM(Population) AS TotalPopulation
FROM country
WHERE Region = 'Australia and New Zealand'
GROUP BY Region;
```
Got one row with the combined population – easy.

### 4. Running Total (My Mind Was Blown)
Used `OVER()` to get a running total as I go down the list:
```sql
SELECT Name, Population,
       SUM(Population) OVER (ORDER BY Population DESC) AS RunningTotal
FROM country
WHERE Region = 'Australia and New Zealand'
ORDER BY Population DESC;
```
Watching the numbers add up row by row was so satisfying!

### 5. Ranking Countries Inside the Region
```sql
SELECT Name, Population,
       RANK() OVER (ORDER BY Population DESC) AS RankInRegion
FROM country
WHERE Region = 'Australia and New Zealand';
```
Australia = 1, New Zealand = 2, and so on.

### 6. The Big Challenge – Rank Every Country Inside Its Own Region
This was the one that made me shout “YES!” when it worked:
```sql
SELECT Region, Name, Population,
       RANK() OVER (PARTITION BY Region ORDER BY Population DESC) AS PopulationRank
FROM country
ORDER BY Region, PopulationRank;
```
Now I can see the #1 most populous country in EVERY region on the planet, all in one query!

## My Favourite Queries From Today

```sql
-- Running total in one region
SELECT Name, Population,
       SUM(Population) OVER (ORDER BY Population DESC) AS RunningTotal
FROM country
WHERE Region = 'Australia and New Zealand';
```

```sql
-- Rank countries globally by population
SELECT Name, Population,
       RANK() OVER (ORDER BY Population DESC) AS GlobalRank
FROM country;
```

```sql
-- The winner: rank inside each region
SELECT Region, Name, Population,
       RANK() OVER (PARTITION BY Region ORDER BY Population DESC) AS RankInRegion
FROM country
ORDER BY Region, RankInRegion;
```

## What I Learned (These Are Game-Changers)
- `GROUP BY` → one row per group  
- `OVER()` + `PARTITION BY` → do calculations inside groups without collapsing rows  
- `RANK()`, `SUM() OVER()`, `ROW_NUMBER()` → I can now answer questions I used to need multiple queries (or Excel!) for  

**Lab completed – I’m officially addicted to window functions!**  
Next time someone asks “Who’s the biggest country in each region?” I’ll write one query and look like a wizard.

-Mokgadi: mokgadi9939@gmail.com
