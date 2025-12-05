# **AWS Cloud Projects Portfolio**

Welcome to my project portfolio. This repository documents my journey in cloud computing. It currently features a group project from the AWS re/Start program (06 October 2025 Cohort).

I will be updating this file with one more upcoming project soon.

---

## Project 1: Moving a Traditional South African Restaurant Online (@MALLS)

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

**Context:** Group Project: AWS 3D E-Commerce Architecture

AWS 3D E‑Commerce Architecture

Overview
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

## Project 3: Coming Soon

*This section will be updated once the third project is completed.*


Contact: Mokgadi - mokgadi9939@gmail.com
