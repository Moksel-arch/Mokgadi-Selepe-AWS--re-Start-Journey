# **Create Subnets and Allocate IP addresses in an Amazon Virtual Private Cloud (Amazon VPC)**

***Objectives*

In this lab, you will:

- Summarize the customer scenario
- Create a Amazon Virtual Private Cloud (Amazon VPC) and understand how to create subnets and allocate IP addresses
- Familiarize yourself with the Amazon Web Services (AWS) Management Console
- Develop a solution to the customer's issue in this lab
- Summarize and describe your findings (group activity)

<img width="867" height="569" alt="image" src="https://github.com/user-attachments/assets/970341d9-49aa-492d-8d1d-4b3c1fdeb13c" />
***1: Investigate the customer's needs*

What I did:

I looked at the customer’s request and figured out what they need for a VPC.

- The customer (Paulo) wants about 15 000 private IP addresses and a public subnet that can hold at least 50 IPs.
- I used the IP‑subnet calculator to pick a CIDR that gives more than 15 000 addresses.
    - A /16 block gives 65 536 IPs, which is plenty.
    - For the public subnet I chose a /26 block (64 IPs) because it’s the smallest block that still provides at least 50 usable addresses.
- I created the VPC with the following settings:
    - VPC name: First VPC
    - IPv4 CIDR: 192.168.0.0/16 (private range from RFC 1918)
    - Public subnet CIDR: 192.168.1.0/26 (64 IPs, 62 usable)
    - No IPv6
    - Availability Zone: No Preference
    - Subnet name: Public subnet
- After clicking Create VPC, the wizard built the VPC and the public subnet.
- I verified the VPC was ready by checking the “Your VPCs” list – it showed “First VPC” with the status “Available”.

That’s the quick walk‑through I’ll hand to the customer so they can see exactly what was built and why those CIDR blocks were chosen.

---

***2: Send the response to the customer (group activity)*

What happened – simple English (in my own words)

I just finished the VPC design for Brock, the customer. Here’s what I did and how I’ll walk him through it:

- Figured out what Brock needs
    - About 15 000 private IP addresses for his whole VPC.
    - A public subnet that can hold at least 50 IP addresses.

- Picked the right CIDR blocks
    - Used a /16 private range (e.g., 192.168.0.0/16) – that gives 65 536 IPs, plenty for 15 000.
    - Chose a /26 public subnet (e.g., 192.168.1.0/26) – that gives 64 total IPs (62 usable), which meets the 50‑IP requirement.

- Built the VPC in the AWS console
    1. Opened the VPC service and clicked Launch VPC Wizard.
    2. Selected VPC with a Single Public Subnet.
    3. Entered the VPC name First VPC.
    4. Set the IPv4 CIDR to 192.168.0.0/16.
    5. Set the public subnet CIDR to 192.168.1.0/26.
    6. Left the rest at defaults and clicked Create VPC.

- Verified everything
    - After creation, the VPC showed up in Your VPCs as Available.
    - The public subnet appeared under Subnets with the correct IP range.

Now I’ll explain all of this to Brock (the customer) in our group activity. I’ll be the cloud support engineer, and he’ll be Brock. We’ll walk through each step together, and I’ll answer any questions he has. If we’re not in a pair, I’ll present the same walk‑through to the whole class.

***Recap*
What I did:

- I looked at the customer’s request and figured out what they need for a VPC.
- The customer wants about 15 000 private IP addresses and a public subnet that can hold at least 50 IPs.
- I chose the right CIDR blocks:
    - VPC CIDR: 192.168.0.0/16 (gives 65 536 IPs, enough for 15 000)
    - Public subnet CIDR: 192.168.1.0/26 (gives 64 IPs, 62 usable, which meets the 50‑IP requirement)
- I launched the VPC in the AWS console using the VPC Wizard:
    1. Selected “VPC with a Single Public Subnet”.
    2. Named it “First VPC”.
    3. Entered the VPC and public subnet CIDRs as above.
    4. Kept the default settings and created the VPC.
- After it finished, I verified that the VPC and public subnet were available in the “Your VPCs” and “Subnets” sections.
- I put together a short walkthrough that shows the customer exactly how to build the same VPC, explaining why those CIDR ranges were chosen.

That’s the recap of what I investigated, the decisions I made, and how I’ll show the customer to set up their VPC.
