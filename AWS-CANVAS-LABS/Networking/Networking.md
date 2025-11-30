# **Internet Protocols - Public and Private IP addresses**

***Objectives*
In this lab, I must:

- Summarize and investigate the customer scenario.
- Analyze the difference between a private and public IP address.
- Develop a solution to the customer's issue in this lab.
- Summarize and describe your findings (group activity).
<img width="813" height="532" alt="image" src="https://github.com/user-attachments/assets/851b7c3b-a3ed-4a95-a39f-75b6b0dd22ab" />

<img width="1918" height="910" alt="image" src="https://github.com/user-attachments/assets/b4699839-e717-43b7-9e2e-04d7a442e3c4" />
<img width="1914" height="912" alt="image" src="https://github.com/user-attachments/assets/fe7a289b-689a-47c8-a904-0dba9d361152" />
<img width="1917" height="922" alt="image" src="https://github.com/user-attachments/assets/e1acb4df-28ea-47aa-81d7-b74029751679" />
<img width="1919" height="887" alt="image" src="https://github.com/user-attachments/assets/80879d82-1c67-4639-a02b-b718c0fd78d1" />
<img width="1910" height="880" alt="image" src="https://github.com/user-attachments/assets/04547d75-12f8-4fcf-8e17-f040e3a29928" />
What happened in the lab:

I started by looking at the customer’s setup. Jess told me she has two EC2 instances in the same VPC (10.0.0.0/16). One instance (A) can’t reach the internet, while the other (B) can, even though they look the same.

***What I did*

- Opened the AWS console and went to the EC2 service.
- In the left‑hand menu I chose Instances – I could see the two instances.
- I selected instance A, went to the Networking tab and wrote down its public and private IPv4 addresses.
- I did the same for instance B.
- I compared the two sets of addresses and noted any differences.

***What I noticed*

- Both instances are in the same VPC and subnet.
- Instance B has a public IP address that is reachable from the internet; instance A does not.
- The private IP ranges are both in the 10.0.x.x block, which is a private CIDR.
- The difference is that instance B has a public IP (or an attached Elastic IP) while instance A does not.

***Why it matters*

- Private IP ranges (like 10.0.0.0/16) are only used inside the VPC.
- A public IP is needed to talk to the internet, either by assigning an Elastic IP or letting the instance sit in a public subnet with an Internet Gateway.

***What I’ll do next*

- Check the route table and security group settings to see why instance A isn’t getting a public address.
- Explain to Jess why using a public IP range for a new VPC isn’t a good idea – it wastes public addresses and can cause routing problems.

That’s the quick rundown of what I observed and what I need to investigate further.


