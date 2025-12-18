# **AWS Cloud Projects Portfolio**

Welcome to my project portfolio. This repository documents my journey in cloud computing. It currently features a group project from the AWS re/Start program (06 October 2025 Cohort).

I will be updating this file with one more upcoming project soon.

---

## Project 1: Moving a Traditional South African Restaurant Online (@MALLS)

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/7b3adecf-fe7d-4f15-87a2-6ae030aaba1e" />

**Context:** Group Project: Static Website on S3

### Overview
For this project, our team of five built a modern, low-cost online presence for a fictional, yet realistic, South African restaurant called @MALLS.

### The Problem
Even in 2025, many small traditional restaurants struggle with manual processes. We addressed common issues such as:
* Reliance on paper bookings.
* Taking orders via WhatsApp.
* Lack of a centralized customer database.

### The Solution
We moved the restaurant operations online to improve efficiency and customer experience.
* **Hosting:** We used AWS S3 to host a static website.
* **Functionality:** We integrated serverless services to handle dynamic parts of the site.
* **Design:** The site features a "Proudly South African" theme, utilizing orange colors and local design elements.

**Live Site:**[Our group static website](https://static-website-on-s3.netlify.app)

### The Team
We collaborated to deliver this solution, with each member focusing on a specific area:

* **Mokgadi M.** – Web Development
* **Skhumbuzo S.** – Web Development
* **Aytee A.** – Research & Documentation
* **Lethabo L.** – AWS S3 Deployment + Infrastructure
* **Leah L.** – Presentation & Design

---

## Project 2: AWS 3D E‑Commerce Architecture

<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/0ed70c0c-4d3a-4b38-8b3c-773bdbb2c32c" />

**Context:** Group Project: AWS 3D E-Commerce Architecture

### Overview
We have built an online shop that lets customers look at and spin around 3D models of products (think furniture, gadgets, clothes) before they buy. We chose AWS because it lets us stay online all the time, handle huge traffic spikes, and keep costs under control.

The Challenge
- Keep the site up 24/7.
- Handle sudden traffic bursts (like Black Friday).
- Load 3D models super fast.
- Keep customer data and payments secure.
- Stay cheap enough for a startup.

The Solution
We put together a cloud setup using AWS services:

- S3 stores the 3D files and images.
- CloudFront delivers them from the nearest edge location.
- EC2 with GPU power renders the models quickly.
- Lambda runs tiny tasks without a full server.
- RDS holds product details, orders, and customer info.
- DynamoDB handles fast‑changing cart data.
- Elastic Load Balancer spreads traffic across instances.
- Route 53 provides DNS and fail‑over.
- CloudWatch & Trusted Advisor monitor performance and keep costs in check.

This mix gives us high availability, automatic scaling, fast loading, strong security, and cost‑effective operation.We learned that a good CDN and caching are essential for 3D content, and that using managed services saves a lot of time.

Feel free to explore the repo, and if you need more details, just give me a shout!

### The Team
We collaborated to deliver this solution:

* **Mokgadi M.** 
* **Kazizwe C.** 
* **Tiisetso K.** 
* **Lufhuno N.** 
* **Ivyn N.**

---

## Project 3: AWS Lex Chatbot Project

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/fe134fee-5ebd-4b17-a1a5-0616a1602535" />

It's called Lex_Box_Chatbot: Create Your Interactive Chatbot Using AWS Lex.

### Overview

We built a quiz bot with Amazon Lex V2. The bot asks a question, waits for the user’s answer, checks if it’s right, and then moves on to the next question. We used custom slots and conditional branching to keep the conversation flowing.

Challenges we ran into
- Lex limits us to 4 branches per intent, so a long quiz was tricky.
- The bot wouldn’t build because we referenced slots that didn’t exist in that part of the flow.
- Lex is case‑sensitive – “UserAnswer” vs “userAnswer” caused crashes.
- We used the wrong comparison symbol (“==” instead of “=”).
- “FulfillmentCodeHook” was on, making the bot look for a Lambda we didn’t need.
- Jumping from Question 1 to Question 2 created ghost branches and conflicts.

How we fixed it
- Grouped all wrong answers into one “default” path to stay under the branch limit.
- Adopted a single naming style for slots and made every reference match exactly.
- Switched all comparisons to Lex syntax {UserAnswer} = "A".
- Turned off the FulfillmentCodeHook so the bot runs without Lambda.
- Split the quiz into several smaller intents (e.g., S3Quiz, S3Quiz_Q2) to avoid branching issues.
- Double‑checked every slot type and “required” flag.

What we learned
- Build error messages are useful – they usually point out the problem.
- Small typos in slot names or case can break everything.
- Work creatively within platform limits.
- A functional bot can be built using only Lex configuration, no Lambda required.
- Breaking a long conversation into tiny intents makes it far easier to manage.

Current status
The bot builds successfully in the English (South Africa) locale, runs from start to finish, and is ready for demo.

**Project Steps & Screenshots**  
Check the Lex_Box_Chatbox.md, PowerPoint slides, and screenshots of the working chatbot in AWS Lex.

**The Team**
- Mokgadi
- Aluwani
- Brite
- Nayana
- Sadiyah
- Ndzalo

If you have any questions or want to try the bot yourself, just message me! 

---
Contacts:
- Mokgadi: 067 719 3860
- mokgadi9939@gmail.com
