# **Internet Protocols - Public and Private IP addresses**

***Objectives*
In this lab, I must:

- Summarize and investigate the customer scenario.
- Analyze the difference between a private and public IP address.
- Develop a solution to the customer's issue in this lab.
- Summarize and describe your findings (group activity).

 ***1: Investigate the customer's environment* 
<img width="813" height="532" alt="image" src="https://github.com/user-attachments/assets/851b7c3b-a3ed-4a95-a39f-75b6b0dd22ab" />
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

***2: Use SSH to connect to an Amazon Linux EC2 instance*

<img width="593" height="537" alt="image" src="https://github.com/user-attachments/assets/c98b0350-d7e0-4bb0-be95-1cf964e7f08b" />
<img width="818" height="518" alt="image" src="https://github.com/user-attachments/assets/b9913f32-63a4-4b29-8a13-ff54de8fcc8a" />
<img width="603" height="542" alt="image" src="https://github.com/user-attachments/assets/904b4cbe-ce1b-4701-96f2-08f12fa0c1d8" />
<img width="818" height="588" alt="image" src="https://github.com/user-attachments/assets/49c64af0-fe9c-402f-ac08-7df3cfd47f50" />
Explain what happened:

I needed to log into an Amazon Linux EC2 instance using SSH. Here’s what I did, step by step (Windows version):

- Opened the lab details panel and clicked Show to see the credentials.
- Downloaded the labsuser.ppk file (the private key) and noted the instance’s Public IP.
- Closed the details panel and downloaded PuTTY (the SSH client) if I didn’t already have it.
- Ran putty.exe and set up a new session:
    - In the “Host Name” field I entered the instance’s public IP.
    - Under “Connection → SSH → Auth” I browsed to the labsuser.ppk file.
- Clicked Open to start the SSH connection.
- A terminal window appeared; I logged in as ec2‑user (or the user specified) and was now inside the Amazon Linux instance.

That’s it – I’m now connected and can run commands on the EC2 instance.


***3: Send the Response to the customer (group activity)*
<img width="825" height="522" alt="image" src="https://github.com/user-attachments/assets/660f0a64-4fb3-4a13-a7cc-51a7f389607f" />
Explain what happened:

- I wrapped up the lab work and wrote a short summary of what I found.
- The summary includes:
    - The difference between the two EC2 instances (one can reach the internet, the other can’t).
    - Why a private IP range is used for the VPC and why a public IP is needed for internet access.
- I prepared to send this summary to the customer.
- In the group activity:
    - Person 2 took the role of Jess, the customer.
    - Person 1 (me) acted as the cloud support engineer.
- I talked through my findings with Person 2, explaining the issue and the proposed fix in plain language.
- After the discussion we agreed on the next steps and I will now send the response to Jess.

