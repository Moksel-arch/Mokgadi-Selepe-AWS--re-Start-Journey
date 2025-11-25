# **Scailing and Name Resolution**


***Here’s what the lab is about:*

- I’m using Elastic Load Balancing (ELB) and Amazon EC2 Auto Scaling to spread traffic and automatically grow or shrink my servers.
- ELB takes incoming requests and sends them to several EC2 instances, so if one fails the others keep handling traffic.
- Auto Scaling makes sure I always have the right number of instances: it adds more when demand spikes and removes them when it’s quiet, which saves money and keeps the app responsive.
- This setup works best for apps with steady usage or regular daily/weekly peaks.

That’s the whole idea in a nutshell.

***The following is the starting architecture:*
<img width="1202" height="688" alt="image" src="https://github.com/user-attachments/assets/0ddc467c-0e9e-406f-8415-dc64bedf46bc" />

***The following is the final architecture:*
<img width="2534" height="1550" alt="image" src="https://github.com/user-attachments/assets/7f6f3c83-1d57-4bbe-836f-761aba3387f2" />

***1: Creating an AMI for auto scaling*
<img width="1905" height="878" alt="image" src="https://github.com/user-attachments/assets/338339b9-ed2f-47e5-aff5-fb3ddef218b2" />
<img width="1911" height="884" alt="image" src="https://github.com/user-attachments/assets/8ddd3d7f-1278-411f-b802-a8f7a861b7e2" />
<img width="1895" height="882" alt="image" src="https://github.com/user-attachments/assets/08e2ddb3-dbcc-48db-8003-6fa11ca82605" />
<img width="1895" height="875" alt="image" src="https://github.com/user-attachments/assets/0873036e-1886-4080-8b91-60cb60b07a1c" />
I just made an Amazon Machine Image (AMI) from the “Web Server 1” instance so I can launch identical copies later.

- Opened the EC2 console (typed EC2 in the AWS search bar).
- Went to Instances in the left‑hand menu and found Web Server 1 (it was running).
- Selected the instance, clicked Actions → Image and templates → Create image.
- Filled in the details:
    - Image name: Web Server AMI
    - Image description: Lab AMI for Web Server (optional)
- Hit Create image.

A confirmation screen popped up showing the new AMI ID – I’ll use that ID when I set up the Auto Scaling group later.

***2: Creating a load balancer*
<img width="1906" height="877" alt="image" src="https://github.com/user-attachments/assets/7029a674-e57f-44dd-b662-bf5a8be41ee6" />
<img width="1904" height="877" alt="image" src="https://github.com/user-attachments/assets/3a8bb5e7-fd3a-47f6-98b2-81272de5ce68" />
<img width="1904" height="869" alt="image" src="https://github.com/user-attachments/assets/9f3e39eb-0d95-4941-9e89-6f6d08e69093" />
<img width="1892" height="875" alt="image" src="https://github.com/user-attachments/assets/890b125a-d35c-43e4-b9d0-af5061b6b268" />
<img width="1900" height="881" alt="image" src="https://github.com/user-attachments/assets/617bdd00-55ce-4275-b85a-be4bc6c62f8b" />
<img width="1899" height="887" alt="image" src="https://github.com/user-attachments/assets/510e496f-27dc-4b7d-9c01-04d2c13f786b" />
<img width="1899" height="882" alt="image" src="https://github.com/user-attachments/assets/e2d65225-7bed-4263-aedb-92ac2cf34918" />
<img width="1906" height="884" alt="image" src="https://github.com/user-attachments/assets/4039fc10-e618-439c-9414-383787a8382f" />
<img width="1896" height="889" alt="image" src="https://github.com/user-attachments/assets/4fddb060-21ff-42ca-a582-b629959ac581" />
<img width="1899" height="875" alt="image" src="https://github.com/user-attachments/assets/cc2d7ac4-32c3-4668-8319-dc0eb65f1722" />
<img width="1900" height="879" alt="image" src="https://github.com/user-attachments/assets/7b49ad1b-d078-4a2e-b491-03b671b4227f" />
<img width="1915" height="880" alt="image" src="https://github.com/user-attachments/assets/27ed21c2-5345-4b80-8e56-a7cebd34c12c" />
I just set up a load balancer in AWS, and here’s what I did:

- Opened the EC2 console (typed EC2 in the search bar).
- In the left‑hand menu under Load Balancing, clicked Load Balancers and hit Create load balancer.
- Chose Application Load Balancer and clicked Create.
- Basic configuration
    - Named it LabELB.
- Network mapping
    - Selected Lab VPC.
    - Mapped both Availability Zones – Public Subnet 1 in the first AZ and Public Subnet 2 in the second AZ.
- Security groups
    - Removed the default security group (clicked the “X”).
    - Chose Web Security Group (it already allows HTTP traffic).
- Listeners and routing
    - Clicked the Create target group link (opened a new tab).
    - Set target type to Instances and named it lab‑target‑group, then clicked Next and Create target group.
    - Closed the target‑group tab and went back to the load‑balancer page.
    - Hit Refresh next to the “Forward to” dropdown and selected lab‑target‑group.
- Clicked Create load balancer at the bottom.
- Got a success message: “Successfully created load balancer: LabELB”.
- Clicked View load balancer, copied the DNS name (it looks something like LabELB-123456789.us-east-1.elb.amazonaws.com) and pasted it into a text editor – I’ll need that later.

That’s it – I now have a load balancer called LabELB that will spread traffic across the two public subnets, using the Web Security Group and the lab‑target‑group I created.

***3: Creating a launch template*
<img width="1912" height="880" alt="image" src="https://github.com/user-attachments/assets/ac5e7079-b82e-486f-b823-b54ed47ec83b" />
<img width="1903" height="877" alt="image" src="https://github.com/user-attachments/assets/1a7254fc-8dda-4473-8223-292ee41d3050" />
<img width="1894" height="871" alt="image" src="https://github.com/user-attachments/assets/dcca37ed-8418-49cb-8f1a-2185d5b3da5f" />
<img width="1918" height="882" alt="image" src="https://github.com/user-attachments/assets/6a68eaaf-74e5-4e93-8934-d383e2d53fd6" />
<img width="1918" height="875" alt="image" src="https://github.com/user-attachments/assets/8f6f1b65-a39e-4972-9e0e-7d095e5c5a58" />
<img width="1918" height="883" alt="image" src="https://github.com/user-attachments/assets/78949b76-c14a-4b3b-9dfb-eda5cd6394c4" />
<img width="1905" height="887" alt="image" src="https://github.com/user-attachments/assets/f381727f-0c90-4c8d-82a6-b817fed9fd22" />


I just created a launch template for an Auto Scaling group, and here’s what I did in simple terms:

- Went to the EC2 console (typed EC2 in the search bar).
- In the left menu under Instances, clicked Launch Templates and hit Create launch template.
- Launch template name: lab-app-launch-template
- Template version description: “A web server for the load test app”
- Turned on Auto Scaling guidance so it helps me set it up for Auto Scaling.
- AMI: chose the My AMIs tab and selected Web Server AMI (the one I created earlier).
- Instance type: picked t3.micro.
- Key pair: left it at “Don’t include in launch template” because I won’t be logging into the instances in this lab.
- Network settings: chose Web Security Group (allows HTTP).
- Clicked Create launch template and got a success message.
- Clicked View launch templates to see the new template listed.

That’s it – I now have a launch template called lab-app-launch-template that Auto Scaling will use to spin up web‑server instances automatically.
