# **AWS 3D E-Commerce Architecture Design**

 Group Members: Mokgadi, Kazizwe, Tiisetso, Lufhuno & Ivyn
 
 Course:        AWS re‑Start Cloud Computing Programme
 
 Date given:    01 December 2025
 
 Date due:      05 December 2025
 

 **Title:      Designing a 3D E‑Commerce Platform on AWS**
---

***1. Introduction*

We are a startup team building a new kind of online shop where customers can see and play with 3D models of products (furniture, gadgets, clothes, etc.) before they buy. 
We chose AWS because it can help us serve millions of people worldwide, keep the site fast, safe, and it is not too expensive.

***2. What the project needs*

 * Always online (24/7)
 * Can handle huge traffic spikes (for example Black Friday) 
 * Super fast loading of 3D models 
 * Very secure (protect customer data and payments) 
 * Not waste money

***3. Our 3D Diagram-Architecture Diagram*
<img width="834" height="679" alt="image" src="https://github.com/user-attachments/assets/4f04ed1e-ee49-4857-b0a2-66aa7c9590e7" />

Main AWS pieces we use:

* Amazon S3 → stores all 3D models and pictures 
* Amazon CloudFront → sends files from the closest city to the user 
* Amazon EC2 → powerful computers that show the 3D models (with GPU) 
* AWS Lambda → does quick jobs without keeping servers on all the time 
* Amazon RDS → keeps product details, orders, customer info 
* Amazon DynamoDB → stores shopping carts and fast-changing data 
* Elastic Load Balancer (ELB) → shares traffic between EC2 servers 
* Amazon Route 53 → our website address and automatic backup routing 
* Amazon CloudWatch & Trusted Advisor → watches everything and tells us how to save money

***4. Why we chose each service*

* S3: cheap, safe, and can hold huge 3D files 
* CloudFront: makes 3D models load in seconds anywhere in the world 
* EC2: we need strong GPUs for smooth 3D experience 
* Lambda: perfect for small tasks, we only pay when it runs 
* RDS: good for normal tables (products, orders) 
* DynamoDB: super fast for shopping carts and live data 
* ELB: keeps the site alive even if some servers crash 
* Route 53: smart DNS that switches to a backup if needed 
* CloudWatch & Trusted Advisor: help us see problems and lower the bill

