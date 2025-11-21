**@MALLS – "Africa's Finest Roots"**


Overview
This repository contains the source code and documentation for @MALLS, a South African restaurant project showcasing cultural heritage through food and design. The project includes:
- A static website built with HTML/CSS/Script.js.
- Deployment on AWS S3 using a serverless architecture.
- Integration with AWS services for scalability, security, and cost efficiency.

Features
- Responsive Static Website:
  - Menu with traditional dishes (Bobotie, Braai, Kota, Potjiekos, Malva Pudding, Mala & Mogudu).
  - Dine-in booking form.
  - Take-away order form.
  - Loyalty program integration.
  - Contact details and interactive map.
- AWS Integration:
  - Amazon S3 – Hosts the website and images.
  - CloudFront – Global content delivery.
  - Route 53 – Custom domain and DNS.
  - API Gateway & Lambda – Handles booking and order logic.
  - DynamoDB – Stores reservations, orders, and loyalty points.
  - Cognito – User authentication.
  - Location Service – Interactive map.

AWS Migration Benefits
- Speed: Pages load globally in seconds via CloudFront.
- Reliability: 99.9% uptime with automatic failover.
- Security: Built-in encryption, IAM, and free SSL certificates.
- Scalability: Handles peak traffic without extra hardware.
- Cost Efficiency: Reduced monthly cost from R6,000 to ~R540–R630.

Cost Analysis
Service                | Cost
-----------------------|------
Amazon S3             | R4
CloudFront            | R470
Route 53              | R16
API Gateway           | R0.50
Lambda                | R4.50
DynamoDB              | R48
Cognito & ACM         | Free
Total                 | R540–R630


Team
- Mokgadi – Web Developer
- Aytee – Research & Documentation
- Lethabo – AWS Deployment
- Leah – Presentation Lead
- Skhumbuzo – Web Developer

[My static site](https://static-website-on-s3.netlify.app)
