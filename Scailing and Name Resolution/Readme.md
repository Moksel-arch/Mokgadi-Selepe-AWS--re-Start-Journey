# **Scailing and Name Resolution**

AWS Load‑Balancing & Auto‑Scaling Lab
 
This repo captures the steps I followed to set up a highly‑available web environment on AWS using Elastic Load Balancing (ELB) and EC2 Auto Scaling. Below is a plain‑English walkthrough of what I did, each step broken into bite‑size pieces.

---

1. What the lab is about
- Goal: Spread incoming traffic across multiple EC2 instances and let the system grow or shrink automatically.
- Why it matters: If one instance fails, the others keep serving requests; adding instances during traffic spikes saves money and keeps the app responsive.
- Best for: Apps with steady usage or predictable daily/weekly peaks.

---

2. Creating an Amazon Machine Image (AMI)
1. Open the EC2 console (type EC2 in the AWS search bar).
2. Go to Instances → find Web Server 1 (it’s running).
3. Select it, click Actions → Image and templates → Create image.
4. Fill in:
    - Image name: Web Server AMI
    - Image description: Lab AMI for Web Server (optional)
5. Click Create image.
6. A confirmation screen shows the new AMI ID – I saved this for later.

---

3. Setting up an Application Load Balancer
1. In the EC2 console, under Load Balancing, choose Load Balancers → Create load balancer.
2. Pick Application Load Balancer → Create.
3. Basic configuration – name it LabELB.
4. Network mapping – select Lab VPC and map both Availability Zones:
    - Public Subnet 1 in AZ 1
    - Public Subnet 2 in AZ 2
5. Security groups – remove the default group and choose Web Security Group (allows HTTP).
6. Listeners and routing – create a target group:
    - Target type: Instances
    - Name: lab-target-group
    - Register the group and close the tab.
7. Back on the load‑balancer page, refresh the Forward to dropdown and select lab-target-group.
8. Click Create load balancer.
9. After creation, click View load balancer, copy the DNS name, and paste it somewhere – I’ll need it later.

---

4. Launch template for Auto Scaling
1. Still in the EC2 console, go to Launch Templates → Create launch template.
2. Name: lab-app-launch-template
3. Choose the AMI created earlier (Web Server AMI).
4. Instance type: t3.micro.
5. Key pair: “Don’t include in launch template” (no SSH needed for this lab).
6. Network settings – select Web Security Group.
7. Click Create launch template and then View launch templates.

---

5. Creating the Auto Scaling group
1. From the launch template, choose Actions → Create Auto Scaling group.
2. Group name: Lab Auto Scaling Group.
3. Network: choose Lab VPC and the private subnets (10.0.1.0/24 and 10.0.3.0/24).
4. Load balancing: attach to the existing load balancer → select lab-target-group | HTTP.
5. Health check: set to ELB.
6. Group size:
    - Desired capacity: 2
    - Minimum: 2
    - Maximum: 4
7. Scaling policy: Target tracking → keep average CPU utilization at 50 %.
8. Skip notifications, add a tag Name = Lab Instance, then click Create Auto Scaling group.

Result: the group starts with 0 instances, but Auto Scaling immediately launches 2 instances in the private subnets.

---

6. Verifying the load balancer
1. After a few seconds, two Lab Instance EC2s appear in the Instances list.
2. In Target Groups, select lab-target-group and wait until both targets show healthy.
3. Open a new browser tab, paste the load‑balancer DNS name, and hit Enter.
4. The Load Test page loads – this confirms the balancer is routing traffic to the instances.

---

7. Testing auto‑scaling
1. Open CloudWatch → All alarms. Two alarms were auto‑created: one for scaling up (CPU > 50 %) and one for scaling down.
2. The AlarmHigh alarm starts in OK state (low CPU).
3. In the Load Test app, click Load Test to generate heavy CPU load.
4. After a minute, AlarmHigh flips to In alarm; Auto Scaling launches additional instances (up to 4).
5. Back in Instances, I see more than two Lab Instance entries – the new ones were created automatically.
6. When the load drops, the AlarmLow will trigger and the extra instances will be terminated, bringing the count back to 2.

---

8. Cleaning up
- I terminated the original Web Server 1 instance (it was only needed to create the AMI).
- All other resources (load balancer, target group, launch template, Auto Scaling group) can be deleted from the AWS console when the lab is finished.

---
-Mokgadi: mokgadi9939@gmail.com
