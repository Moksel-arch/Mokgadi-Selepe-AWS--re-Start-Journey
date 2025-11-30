# **Networking - Service Notes** 

***Written by Mokgadi Selepe*  
**Date:** December 01, 2025  
**Overview:** These are my combined service notes from all the AWS networking labs I did. I acted as a cloud support engineer helping different customers with VPC setup, IP addresses, and internet connectivity. Each part is from one lab, and I kept everything in simple English. No icons or fancy stuff – just the key points.

### Lab 1: Creating a VPC and Subnets  
**Customer:** Paulo Santos (startup owner)  
**Issue:** New to AWS, needs help setting up a VPC with about 15,000 private IPs in 192.x.x.x range and a public subnet with at least 50 IPs.  

**What the customer said**  
Paulo asked for a VPC with about 15,000 private IP addresses (he likes the 192.x.x.x range) and one public subnet that has at least 50 IP addresses.  

**What I did**  
I built it in the lab using the VPC Wizard:  
- Set VPC CIDR to 192.168.0.0/18 (gives 16,384 IPs).  
- Set public subnet CIDR to 192.168.1.0/26 (gives 64 IPs).  
- Named VPC "First VPC" and subnet "Public subnet".  

**What this means (simple English)**  
This setup gives Paulo more than enough private IPs in a safe range, and the subnet fits perfectly without wasting space.  

**Message I will send to Paulo**  
Hi Paulo,  
I already built the exact VPC you asked for in my lab – it works great!  
- More than 15,000 private IPs  
- Public subnet with 64 IPs  
- All in the safe 192.168.x.x private range  
I wrote the 6 simple steps. You can do it yourself in seconds, or I can jump into your account and create it for you right now – whichever you prefer.  
Just let me know!  
Kind regards,  
Mokgadi  

**Status**  
Lab completed, VPC created and checked. Waiting for Paulo to reply and say if he wants me to build it in his real account.  

### Lab 2: Creating Networking Resources in a VPC  
**Customer:** Brock (startup owner)  
**Issue:** Has a VPC but cannot ping the internet from his instance.  

**What the customer said**  
Brock said: “I made a VPC but I can’t ping outside. Please help me make it work so my instance can reach the internet.”  

**What I did**  
I built everything step by step:  
1. Created VPC (Test VPC, CIDR 192.168.0.0/18).  
2. Created public subnet (Public Subnet, CIDR 192.168.1.0/26).  
3. Created Internet Gateway (TEST VPC IGW) and attached it.  
4. Created Route Table (Public Route Table), added 0.0.0.0/0 to IGW, and connected to subnet.  
5. Created NACL (Public Subnet NACL) allowing all traffic.  
6. Created Security Group (public security group) with inbound SSH/HTTP/HTTPS and outbound all.  
7. Launched EC2 instance in the subnet with public IP.  
8. SSH-ed in and ran ping google.com – it worked.  

**What this means (simple English)**  
You need all these pieces for internet to work: subnet, gateway, routes, security, and public IP. If one is missing, no connection.  

**Message I will send to Brock**  
Hi Brock,  
I fixed the problem in my lab – your instance can ping the internet now.  
Here is what was probably missing:  
1. An Internet Gateway (attached to the VPC)  
2. A route table with 0.0.0.0/0 to Internet Gateway  
3. The route table connected to your public subnet  
4. Security group and NACL set to allow traffic  
I tested ping google.com myself and it works perfectly.  
I can do these steps in your real account super quick (5 minutes), or send you a checklist to do it yourself.  
Just tell me what you want!  
Kind regards,  
Mokgadi  

**Status**  
Lab done – everything connects to the internet fine. Waiting for Brock to say yes so I can fix his real setup.  

### Lab 3: Public vs Private IP Addresses  
**Customer:** Jess  
**Issue:** One EC2 instance can reach the internet, the other cannot, even though they look the same.  

**What the customer said**  
Jess has two EC2 instances in the same VPC – Instance B can go on the internet, Instance A cannot.  

**What I did**  
Checked the IPs:  
- Both have private IPs (10.x.x.x).  
- Instance B has a public IP.  
- Instance A has no public IP.  
Connected with SSH to test (using PuTTY and key file).  

**What this means (simple English)**  
Private IPs only work inside the VPC. You need a public IP to reach the internet.  

**Message I will send to Jess**  
Hi Jess,  
I found the problem: Instance A has no public IP address, that’s why it cannot reach the internet. Instance B has one, so it works fine.  
Private IPs (10.x.x.x) only work inside your VPC. To go on the internet, we need a public IP.  
I can fix it in 2 minutes by giving Instance A an Elastic IP, or we can move it to a public subnet.  
Which one do you want? I’ll do it now.  
Kind regards,  
Mokgadi  

**Status**  
Waiting for Jess to reply. As soon as she says yes, I will add the Elastic IP and test again.  

### Lab 4: Static vs Dynamic Public IP Addresses  
**Customer:** Bob (Cloud Admin)  
**Issue:** Public IP changes every time the instance stops and starts, breaking other systems.  

**What the customer said**  
Bob has an EC2 instance called “Public Instance”. Every time he stops it and starts it again, the public IP changes to a new random number. He wants it to stay the same.  

**What I did**  
1. Launched test instance with auto-assign public IP.  
2. Stopped and started – public IP changed, private IP stayed the same.  
3. Allocated Elastic IP and attached it.  
4. Stopped and started again – IP stayed the same.  

**What this means (simple English)**  
Normal public IPs are dynamic (change on stop/start). Elastic IPs are static (never change).  

**Message I will send to Bob**  
Hi Bob,  
I found the problem. The normal public IP that AWS gives automatically is temporary – it changes every time you stop and start the instance. That’s why everything breaks.  
The fix is super easy: we give your instance an Elastic IP. It is a permanent public IP that stays the same forever.  
I can do it in 2 minutes and there is no extra cost as long as the instance is running.  
Just say “yes please” and I’ll set it up right now and send you the new fixed IP.  
Kind regards,  
Mokgadi  

**Status**  
Waiting for Bob to reply. As soon as he says go ahead, I will attach the Elastic IP and the problem is gone forever.  

That’s all from my labs! If you need more, email me at mokgadi9939@gmail.com.
