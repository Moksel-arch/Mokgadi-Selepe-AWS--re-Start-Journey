# **AWS Lab – Creating a VPC and Subnets**

*Written by Mokgadi Selepe*

### The customer  
Paulo Santos – startup owner, brand new to AWS.  
He asked for:  
- A VPC with about 15,000 private IP addresses (he likes the 192.x.x.x range)  
- One public subnet that has at least 50 IP addresses  

### What I built in the lab (and it worked perfectly)  
- VPC CIDR: **192.168.0.0/18**  
  → Gives 16,384 IPs total (the smallest size that is bigger than 15,000)  
  → 192.168.x.x is 100% private – safe from the internet.  

- Public subnet CIDR: **192.168.1.0/26**  
  → Gives 64 usable IPs (more than the 50 he wanted)  
  → Fits nicely inside the VPC range.  

- VPC name: First VPC  
- Subnet name: Public subnet  

### Quick cheat-sheet of the sizes  
- /18 = 16,384 IPs → perfect for ~15,000  
- /26 = 64 IPs → perfect for 50+  

### Super easy steps (copy-paste ready for Paulo)  
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

### Message I will send to Paulo  
Hi Paulo,  

I already built the exact VPC you asked for in my lab – it works great!  

- More than 15,000 private IPs  
- Public subnet with 64 IPs  
- All in the safe 192.168.x.x private range  

I wrote the 6 simple steps above. You can do it yourself in seconds, or I can jump into your account and create it for you right now – whichever you prefer.  

Just let me know! 

Kind regards,  
Mokgadi  

### Status  
Lab completed, VPC created and checked.  
Waiting for Paulo to reply and say if he wants me to build it in his real account.

That’s everything! Hope this helps anyone else who is just starting with VPCs
