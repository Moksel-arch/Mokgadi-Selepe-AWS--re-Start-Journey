# **AWS Lab – Public vs Private IP Addresses** 

*My notes from the Internet Protocols lab*  
Written by Mokgadi Selepe  

### What this lab was about  
Jess (the customer) has two EC2 instances in the same VPC.  
- Instance B can go on the internet.  
- Instance A cannot, even though they look the same.  

I had to find out why and fix it.

### What I discovered (very simple)  
- Both instances have private IPs that start with 10.x.x.x → these only work inside the VPC (like an internal office phone).  
- Instance B also has a public IP → this is the “real” internet address.  
- Instance A has NO public IP → that is why it is stuck and cannot reach the internet.

### How to fix it (the two easy ways)  
1. Give Instance A an Elastic IP (fastest).  
2. Put it in a public subnet and turn on “Auto-assign public IPv4 address” when launching.

We also need:  
- Route table must have 0.0.0.0/0 → Internet Gateway  
- Security group must allow outbound traffic (ports 80 and 443 are the main ones)

### How I connected with SSH (Windows)  
- Downloaded the labsuser.ppk key file  
- Opened PuTTY  
- Put the public IP in Host Name  
- Went to Connection → SSH → Auth → browsed to the .ppk file  
- Clicked Open and logged in as ec2-user  

It only works when the instance has a public IP.

### Message I sent to Jess  
Hi Jess,  

I found the problem: Instance A has no public IP address, that’s why it cannot reach the internet. Instance B has one, so it works fine.  

Private IPs (10.x.x.x) only work inside your VPC. To go on the internet, we need a public IP.  

I can fix it in 2 minutes by giving Instance A an Elastic IP, or we can move it to a public subnet.  

Which one do you want? I’ll do it now.  

Kind regards,  
Mokgadi  

### What happens next  
Waiting for Jess to reply. As soon as she says yes, I will add the Elastic IP and test again.

- Mokgadi: mokgadi9939@gmail.com
