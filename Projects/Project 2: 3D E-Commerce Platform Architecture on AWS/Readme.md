## GROUP PROJECT: 
***
# AWS 3D E-Commerce Architecture
<img width="796" height="714" alt="image" src="https://github.com/user-attachments/assets/0ed70c0c-4d3a-4b38-8b3c-773bdbb2c32c" />

## Introduction

This project is about building an online shopping platform where customers can view and interact with **3D models of products** (like furniture, gadgets, clothes) before buying.  
We chose **AWS** because it helps us scale globally, stay secure, and keep costs under control.

***

## What We Needed

*   Always online (24/7)
*   Handle big traffic spikes (e.g., Black Friday)
*   Super-fast loading of 3D models
*   Strong security for customer data and payments
*   Cost efficiency

***

## Our Architecture

We designed a cloud architecture using these AWS services:

*   **Amazon S3** – Stores all 3D models and images
*   **Amazon CloudFront** – Delivers files quickly from the nearest location
*   **Amazon EC2** – GPU-powered servers for rendering 3D models
*   **AWS Lambda** – Runs small tasks without full-time servers
*   **Amazon RDS** – Stores product details, orders, and customer info
*   **Amazon DynamoDB** – Handles shopping carts and fast-changing data
*   **Elastic Load Balancer (ELB)** – Distributes traffic across servers
*   **Amazon Route 53** – DNS and failover routing
*   **Amazon CloudWatch & Trusted Advisor** – Monitoring and cost optimization

***

## Why These Services?

*   **S3**: Cheap, secure, and great for large files
*   **CloudFront**: Speeds up loading worldwide
*   **EC2 with GPU**: Smooth 3D experience
*   **Lambda**: Cost-effective for short tasks
*   **RDS & DynamoDB**: Best mix for structured and fast data
*   **ELB & Route 53**: High availability and failover
*   **CloudWatch & Trusted Advisor**: Monitoring and cost savings

***

## How It Meets Our Goals

*   **Always online**: Multi-AZ setup + Route 53 failover
*   **Scalable**: EC2 Auto Scaling + Lambda
*   **Fast**: CloudFront caching + GPU servers
*   **Secure**: Encryption, IAM, WAF, GuardDuty
*   **Cost-efficient**: Auto Scaling, Lambda, Spot Instances

***

## Lessons Learned

*   Speed matters for 3D shopping → CDN and caching are essential
*   Use managed services to save time
*   Auto Scaling and serverless help handle traffic spikes
*   Plan security and cost from day one
*   CloudWatch is critical for monitoring

***

## Well-Architected Review

We checked our design against AWS’s six pillars:

*   Operational Excellence: 5/5
*   Security: 5/5
*   Reliability: 5/5
*   Performance Efficiency: 5/5
*   Cost Optimization: 4.5/5
*   Sustainability: 4/5

***

## Conclusion

Our AWS-based design delivers a **fast, secure, and scalable 3D shopping experience** without breaking the bank. It’s ready to grow with our startup and give customers something amazing.

***

## References

*   AWS Well-Architected Framework – https://aws.amazon.com/architecture/well-architected/ 
*   AWS Documentation – https://docs.aws.amazon.com/


***
Contacts:
- Mokgadi: 067 719 3860
- mokgadi9939@gmail.com
