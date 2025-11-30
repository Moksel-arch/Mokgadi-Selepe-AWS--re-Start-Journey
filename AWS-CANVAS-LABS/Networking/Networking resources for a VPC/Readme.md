# **AWS Lab – Creating Networking Resources in a VPC**

***Written by Mokgadi Selepe*

### The customer  
Brock – he owns a startup.  
He said: “I made a VPC but I can’t ping outside. Please help me make it work so my instance can reach the internet.”

### What I did in the lab (step by step)  
I built everything from scratch to make sure it works:  
1. Made a new VPC  
   - Name: Test VPC  
   - CIDR: 192.168.0.0/18  

2. Made a public subnet  
   - Name: Public Subnet  
   - CIDR: 192.168.1.0/26  

3. Made an Internet Gateway  
   - Name: TEST VPC IGW  
   - Attached it to Test VPC  

4. Made a Route Table  
   - Name: Public Route Table  
   - Added the route: 0.0.0.0/0 → TEST VPC IGW  
   - Connected the route table to Public Subnet  

5. Made a Network ACL (NACL)  
   - Name: Public Subnet NACL  
   - Allowed ALL traffic in and out (rule 100)  

6. Made a Security Group  
   - Name: public security group  
   - Inbound rules: SSH on port 22, HTTP on 80, HTTPS on 443 – from anywhere  
   - Outbound: All traffic allowed  

7. Launched an EC2 instance (Amazon Linux 2023)  
   - Put it in Public Subnet  
   - Turned on Auto-assign public IP  
   - Used the new security group  

8. Logged into the instance with SSH (using PuTTY on Windows and labsuser.ppk key)  

9. Ran `ping google.com` – it worked! Got replies back with no packet loss.

### Simple explanation  
To get internet working on an instance, you need every single one of these:  
- A public subnet  
- An Internet Gateway attached to the VPC  
- A route table with 0.0.0.0/0 pointing to the Internet Gateway  
- The route table connected to the subnet  
- A security group that allows outbound traffic (and inbound for SSH)  
- A NACL that does not block traffic  
- The instance needs a public IP (like auto-assign)  

If even one thing is missing, no internet and no ping.

### Message I will send to Brock  
Hi Brock,  

I fixed the problem in my lab – your instance can ping the internet now.  

Here is what was probably missing:  
1. An Internet Gateway (attached to the VPC)  
2. A route table with 0.0.0.0/0 → Internet Gateway  
3. The route table connected to your public subnet  
4. Security group and NACL set to allow traffic  

I tested `ping google.com` myself and it works perfectly.  

I can do these steps in your real account super quick (5 minutes), or send you a checklist to do it yourself.  

Just tell me what you want!  

Kind regards,  
Mokgadi  

### Status  
Lab done – everything connects to the internet fine.  
Waiting for Brock to say yes so I can fix his real setup.

-Mokgadi: mokgadi9939@gmail.com

That’s everything from this lab – hope it helps someone else who is stuck with VPC networking!
