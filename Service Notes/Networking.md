# **Service Note – Written by Mokgadi Selepe**

**Date:** 30 November 2025  
**Customer:** Jess  
**Issue:** One EC2 instance can reach the internet, the other can not.

**What the customer told me**  
Jess has two EC2 instances in the same VPC (10.0.0.0/16). Instance B works fine and can go on the internet. Instance A cannot, even though both look the same.

**What I did**  
I opened the AWS console and looked at both instances.  
I checked the Networking tab for each one and wrote down their IP addresses.

**What I found**  
- Both instances have private IP addresses that start with 10.x.x.x – this is normal and only works inside the VPC.  
- Instance B also has a public IP address, so the internet can reach it and it can reach the internet.  
- Instance A has no public IP address at all – that is why it cannot go online.

**Simple explanation**  
Private IPs (10.x.x.x) are like the phone extension inside an office – they only work inside the building.  
Public IPs are like the main office phone number – they work from anywhere on the internet.  
Instance A is missing the “main phone number”, so it is stuck inside the VPC.

**What needs to be fixed**  
To give Instance A internet access, we must do one of these two things:  
1. Put Instance A in a public subnet and turn on “Auto-assign public IPv4 address”, or  
2. Create an Elastic IP and attach it to Instance A.

We must also check:  
- The route table has a line that says 0.0.0.0/0 → Internet Gateway  
- The security group allows outbound traffic (usually port 80 and 443)

**How I tested it myself**  
I used PuTTY on my Windows laptop:  
- Downloaded the labsuser.ppk key file  
- Put the public IP of an instance in the Host Name box  
- Loaded the .ppk file under Connection → SSH → Auth  
- Clicked Open and logged in as ec2-user  
It worked perfectly when the instance had a public IP.

**What I told Jess (my exact message)**  
Hi Jess,

I found the problem. Instance A does not have a public IP address, that is why it cannot reach the internet. Instance B has one, so it works.

Private IPs (10.x.x.x) only work inside your VPC. To talk to the internet, an instance needs a public IP.

Fix options:  
1. Give Instance A an Elastic IP (quickest way), or  
2. Move it to a public subnet and enable auto-assign public IP.

I also checked the route table and security group – once we add the public IP, everything should work.

Let me know which option you prefer and I will do it for you right now.

Kind regards,  
Mokgadi Selepe  
Cloud Support Engineer

**Status**  
Waiting for Jess to reply and choose the fix. Once she says yes, I will add the Elastic IP and test again.

That is everything I did today.
