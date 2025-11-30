# **AWS Networking Labs – My Notes Collection**

*Written by Mokgadi Selepe*

Hi! This is my GitHub repo where I keep all my notes from AWS networking labs. I am Mokgadi Selepe, and I wrote these in simple English so anyone can understand. Each section is from a different lab I did. I acted like a cloud support engineer helping customers with VPCs, IPs, and internet setup.

If you are new to AWS networking, start from the top. I removed any icons or fancy stuff – just plain text.

### Lab 1: Creating a VPC and Subnets
#### The Customer
Paulo Santos – startup owner, brand new to AWS.  
He asked for:  
- A VPC with about 15,000 private IP addresses (he likes the 192.x.x.x range)  
- One public subnet that has at least 50 IP addresses  

#### What I Built in the Lab (and It Worked Perfectly)
- VPC CIDR: 192.168.0.0/18  
  → Gives 16,384 IPs total (the smallest size that is bigger than 15,000)  
  → 192.168.x.x is 100% private – safe from the internet.  
- Public subnet CIDR: 192.168.1.0/26  
  → Gives 64 usable IPs (more than the 50 he wanted)  
  → Fits nicely inside the VPC range.  
- VPC name: First VPC  
- Subnet name: Public subnet  

#### Quick Cheat-Sheet of the Sizes
- /18 = 16,384 IPs → perfect for ~15,000  
- /26 = 64 IPs → perfect for 50+  

#### Super Easy Steps (Copy-Paste Ready for Paulo)
1. Log into AWS console  
2. Search “VPC” → open it  
3. Click the orange button “Launch VPC Wizard”  
4. Choose “VPC with a Single Public Subnet” → click Select  
5. Fill in these:  
   - IPv4 CIDR block: 192.168.0.0/18  
   - Public subnet CIDR: 192.168.1.0/26  
   - VPC name: First VPC  
   - Subnet name: Public subnet  
6. Leave everything else as default → click “Create VPC”  

Done in less than 30 seconds!

#### Message I Will Send to Paulo
Hi Paulo,  

I already built the exact VPC you asked for in my lab – it works great!  

- More than 15,000 private IPs  
- Public subnet with 64 IPs  
- All in the safe 192.168.x.x private range  

I wrote the 6 simple steps above. You can do it yourself in seconds, or I can jump into your account and create it for you right now – whichever you prefer.  

Just let me know!  

Kind regards,  
Mokgadi  

#### Status
Lab completed, VPC created and checked.  
Waiting for Paulo to reply and say if he wants me to build it in his real account.  

That’s everything! Hope this helps anyone else who is just starting with VPCs.

### Lab 2: Creating Networking Resources in a VPC
#### The Customer
Brock – he owns a startup.  
He said: “I made a VPC but I can’t ping outside. Please help me make it work so my instance can reach the internet.”

#### What I Did in the Lab (Step by Step)
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

#### Simple Explanation
To get internet working on an instance, you need every single one of these:  
- A public subnet  
- An Internet Gateway attached to the VPC  
- A route table with 0.0.0.0/0 pointing to the Internet Gateway  
- The route table connected to the subnet  
- A security group that allows outbound traffic (and inbound for SSH)  
- A NACL that does not block traffic  
- The instance needs a public IP (like auto-assign)  

If even one thing is missing, no internet and no ping.

#### Message I Will Send to Brock
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

#### Status
Lab done – everything connects to the internet fine.  
Waiting for Brock to say yes so I can fix his real setup.  

That’s everything from this lab – hope it helps someone else who is stuck with VPC networking!

### Lab 3: Public vs Private IP Addresses
#### What This Lab Was About
Jess (the customer) has two EC2 instances in the same VPC.  
- Instance B can go on the internet.  
- Instance A cannot, even though they look the same.  

I had to find out why and fix it.

#### What I Discovered (Very Simple)
- Both instances have private IPs that start with 10.x.x.x → these only work inside the VPC (like an internal office phone).  
- Instance B also has a public IP → this is the “real” internet address.  
- Instance A has NO public IP → that is why it is stuck and cannot reach the internet.

#### How to Fix It (The Two Easy Ways)
1. Give Instance A an Elastic IP (fastest).  
2. Put it in a public subnet and turn on “Auto-assign public IPv4 address” when launching.  

We also need:  
- Route table must have 0.0.0.0/0 → Internet Gateway  
- Security group must allow outbound traffic (ports 80 and 443 are the main ones)

#### How I Connected with SSH (Windows)
- Downloaded the labsuser.ppk key file  
- Opened PuTTY  
- Put the public IP in Host Name  
- Went to Connection → SSH → Auth → browsed to the .ppk file  
- Clicked Open and logged in as ec2-user  

It only works when the instance has a public IP.

#### Message I Sent to Jess
Hi Jess,  

I found the problem: Instance A has no public IP address, that’s why it cannot reach the internet. Instance B has one, so it works fine.  

Private IPs (10.x.x.x) only work inside your VPC. To go on the internet, we need a public IP.  

I can fix it in 2 minutes by giving Instance A an Elastic IP, or we can move it to a public subnet.  

Which one do you want? I’ll do it now.  

Kind regards,  
Mokgadi  

#### What Happens Next
Waiting for Jess to reply. As soon as she says yes, I will add the Elastic IP and test again.

### Lab 4: Static vs Dynamic Public IP Addresses
#### What the Customer (Bob) Was Complaining About
Bob has an EC2 instance called “Public Instance”.  
Every time he stops it (to save money) and starts it again, the public IP changes to a new random number.  
This breaks all the other systems that need to talk to that exact IP. He wants the public IP to stay the same forever.

#### What I Did in the Lab to See the Problem Myself
1. Launched a normal EC2 instance in a public subnet with “Auto-assign Public IP = Enable”.  
2. Noted the public IP (for example 54.123.45.67).  
3. Stopped the instance → public IP disappeared.  
4. Started it again → public IP came back as something totally different (like 54.987.65.43).  
5. Private IP never changed – it stayed the same the whole time.  

So yes, the normal public IP that AWS gives you is dynamic – it changes on every stop/start.  
That is exactly Bob’s problem.

#### The Real Fix – Elastic IP (EIP)
AWS has a special thing called an Elastic IP.  
It is a permanent public IP that belongs to your account and never changes.  

How I fixed it in the lab:  
1. Went to EC2 → Network & Security → Elastic IPs.  
2. Clicked “Allocate Elastic IP address” → got a fixed IP (e.g. 3.456.789.012).  
3. Selected the new EIP → Actions → Associate Elastic IP address.  
4. Picked my test instance and clicked Associate.  

Now the instance shows the Elastic IP as its public IP.

#### Tested the Fix
- Stopped the instance → Elastic IP stayed attached.  
- Started it again → public IP was still the same Elastic IP. No change!  
It works perfectly.

#### Quick Summary
- Normal public IP (auto-assigned) = dynamic → changes on stop/start  
- Private IP = always static  
- Elastic IP = real static public IP → never changes, even after 100 stops/starts  

#### Message I Will Send to Bob
Hi Bob,  

I found the problem. The normal public IP that AWS gives automatically is temporary – it changes every time you stop and start the instance. That’s why everything breaks.  

The fix is super easy: we give your instance an Elastic IP. It is a permanent public IP that stays the same forever.  

I can do it in 2 minutes and there is no extra cost as long as the instance is running.  

Just say “yes please” and I’ll set it up right now and send you the new fixed IP.  

Kind regards,  
Mokgadi  

#### Status
Waiting for Bob to reply. As soon as he says go ahead, I will attach the Elastic IP and the problem is gone forever.

That’s all! If you have questions, email me at mokgadi9939@gmail.com. Hope this repo helps you with AWS networking.
