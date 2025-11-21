# **Introduction to Amazon DynamoDB – AWS Re:start Lab** 
**By Mokgadi Selepe**

First time ever using a NoSQL database and I’m officially obsessed with **DynamoDB**! No schemas, no stress, just pure speed and flexibility. This lab was so much fun – I built a little music library in like 10 minutes.

## What I Did – My Music Collection in DynamoDB

### 1. Created My First DynamoDB Table
- Table name: **Music**  
- Partition key: **Artist** (String)  
- Sort key: **Song** (String)  
- Left everything else on default (on-demand capacity – no thinking about read/write units!)  
- Table went from “Creating” → “Active” in seconds

### 2. Added Some of My Favourite Songs
Added these bangers straight from the console:

| Artist         | Song              | Album                          | Year | Extra stuff I added                  |
|----------------|-------------------|--------------------------------|------|--------------------------------------|
| Pink Floyd     | Money             | The Dark Side of the Moon      | 1973 | Genre: Progressive Rock             |
| John Lennon    | Imagine           | Imagine                        | 1971 | Genre: Classic Rock                  |
| Psy            | Gangnam Style     | Psy 6 (Six Rules), Part 1      | 2012 | LengthSeconds: 219 (fixed from 2011) |

The coolest part? Every item can have different attributes. No need to pre-define columns like in SQL – pure freedom!

### 3. Fixed a Mistake
Realised I put Gangnam Style as 2011 → edited the item directly in the console and changed it to **2012**. One click, done.

### 4. Searched My Library
- **Query**: Found “Gangnam Style” instantly using Artist = "Psy" and Song = "Gangnam Style"  
- **Scan** with filter: Found all songs from 1971 → returned “Imagine”  

Query is lightning fast when you know the key. Scan reads everything (good to know the difference now).

### 5. Cleaned Up (Deleted the Table)
Selected the Music table → Actions → Delete table → typed “delete” → goodbye music library!  
Everything gone in seconds, no charges left behind.

## What I Learned (and why I love DynamoDB now)
- No schema = add whatever fields you want, whenever you want  
- Partition key + sort key = perfect for things like music, playlists, leaderboards, user sessions  
- Query = super fast when you know the key  
- Scan = useful but reads everything (can get expensive at scale)  
- On-demand mode = I literally don’t have to think about capacity  
- Perfect for apps that need speed and don’t fit neatly into rows and columns

**Lab completed – I went from zero to NoSQL hero in one afternoon!**  
Next I want to try DynamoDB with Lambda and API Gateway. This is the future and I’m here for it!

-Mokgadi: mokgadi9939@gmail.com
