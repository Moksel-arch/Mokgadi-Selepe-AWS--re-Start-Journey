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

***4: Creating an Auto Scaling group*
<img width="1906" height="876" alt="image" src="https://github.com/user-attachments/assets/a6820f82-9bd1-4329-9415-27c7c16d5832" />
<img width="1912" height="880" alt="image" src="https://github.com/user-attachments/assets/d0d007e9-3d3d-4224-9eb8-9ae89c19be77" />
<img width="1898" height="869" alt="image" src="https://github.com/user-attachments/assets/5882458e-7684-41df-96ba-e4e45e8b6fbc" />
<img width="1896" height="891" alt="image" src="https://github.com/user-attachments/assets/f57530d3-2624-4aaf-bb2b-b962228ee2dc" />
<img width="1913" height="877" alt="image" src="https://github.com/user-attachments/assets/1544da7b-9e05-438f-93e2-11122eb1851f" />
<img width="1889" height="852" alt="image" src="https://github.com/user-attachments/assets/e09fdcff-0d02-4422-9e38-a29db3db8f01" />
<img width="1916" height="884" alt="image" src="https://github.com/user-attachments/assets/e73aa025-dd92-45f7-bc88-11d29bfb1474" />
<img width="1910" height="875" alt="image" src="https://github.com/user-attachments/assets/5a38a827-495a-4e01-8fde-f0c285a841ee" />
<img width="1912" height="881" alt="image" src="https://github.com/user-attachments/assets/416c45b3-bc4a-463e-ad1e-a44607d044fb" />
<img width="1914" height="757" alt="image" src="https://github.com/user-attachments/assets/a70429f3-648b-4a3d-a4a4-754822139fa4" />
<img width="1894" height="876" alt="image" src="https://github.com/user-attachments/assets/f1003d80-aae7-4f31-8bdd-1c77e02e5bfb" />
<img width="1915" height="877" alt="image" src="https://github.com/user-attachments/assets/8e9c0457-ac12-429f-89d6-e3c447ea3a11" />
<img width="1913" height="678" alt="image" src="https://github.com/user-attachments/assets/89a6aecd-ef2a-469b-8278-8c69f9ec781e" />

***5: Verifying that load balancing is working*
<img width="1916" height="880" alt="image" src="https://github.com/user-attachments/assets/3051dbf0-f2d6-4764-8141-fe1bba14e2be" />
<img width="1916" height="883" alt="image" src="https://github.com/user-attachments/assets/e82642a4-f74b-4ea0-ae19-8d91779e9792" />
<img width="1595" height="558" alt="image" src="https://github.com/user-attachments/assets/c44f096f-4fd1-4eaa-8833-ce606c71bcf6" />
I just checked that the load balancer is doing its job, and here’s what happened in plain English:

- I opened the Instances page and saw two new EC2 instances called Lab Instance.
    - Auto Scaling launched them automatically.
    - If they didn’t show up right away, I waited a few seconds and hit Refresh.

- Next I went to Target Groups under Load Balancing and selected lab‑target‑group.
    - The two Lab Instance targets appeared in the Registered targets list.
    - I kept hitting Refresh until both showed a Health status of healthy.
    - “Healthy” means the load balancer’s health check passed and it will start sending traffic to them.

- With the instances healthy, I opened a new browser tab, pasted the DNS name I copied earlier (the load balancer’s URL), and hit Enter.
    - The Load Test application loaded, which tells me the load balancer received the request, forwarded it to one of the EC2 instances, and returned the response.

That’s it – the load balancer is up and routing traffic to the two auto‑scaled instances.

***6: Testing auto scaling*
<img width="1912" height="874" alt="image" src="https://github.com/user-attachments/assets/0f1315c4-b135-42af-ba1b-2aaa2d867320" />
<img width="1906" height="889" alt="image" src="https://github.com/user-attachments/assets/c14b7c42-6ed7-46db-b6ee-d98ef8db9be5" />
<img width="1909" height="880" alt="image" src="https://github.com/user-attachments/assets/a4a1ab4c-d08e-4892-a1d5-256c1e6f5096" />
<img width="1625" height="422" alt="image" src="https://github.com/user-attachments/assets/cd1b7508-5277-4594-b55c-28104db44296" />
<img width="1895" height="877" alt="image" src="https://github.com/user-attachments/assets/a07bda5e-e3ce-43c2-aa03-a367f7b27692" />

I just finished testing the auto‑scaling part of the lab, and here’s what happened in plain English:

- Started with two instances – the Auto Scaling group I created has a minimum of 2 and a maximum of 4, so at the moment I’m only running the two base instances.
- Opened CloudWatch – I went to the CloudWatch console, looked at All alarms, and saw the two alarms that Auto Scaling automatically created (one for scaling up when CPU > 50 % and one for scaling down).
- Checked the “AlarmHigh” alarm – it was in an OK state, meaning CPU usage was low and the alarm hadn’t triggered yet.
- Generated load – I switched back to the Load Test web app, clicked Load Test, and the page started doing heavy calculations. This drove the CPU up on the running instances.
- Watched the alarm – After a minute or two the AlarmHigh alarm flipped to In alarm (the chart showed CPU crossing the 50 % line). That’s the signal for Auto Scaling to add more instances.
- Auto Scaling launched new instances – I went back to the EC2 Instances page and saw more than two Lab Instance entries appear. Auto Scaling automatically created the extra instances to keep the average CPU around 50 %.
- Result – Now I have more instances running, and the load balancer will start sending traffic to them. When the load drops, the “AlarmLow” will trigger and the extra instances will be terminated, bringing the count back down to the minimum of two.

That’s the whole flow of how I forced the system to scale out and verified it with CloudWatch.

***7: Terminating the Web Server 1 instance*
<img width="1030" height="551" alt="image" src="https://github.com/user-attachments/assets/ddca6609-16bc-42e3-83b9-cbb0c29446a7" />
<img width="1916" height="884" alt="image" src="https://github.com/user-attachments/assets/a802d6f1-c0f7-46cb-ae0f-f096e67a81a7" />

I just got rid of the original Web Server 1 instance:

- I opened the EC2 console and selected Web Server 1 (the only one I wanted to delete).
- From the Instance state dropdown I chose Terminate instance.
- I clicked Terminate to confirm.

That instance was only used to create the AMI for the Auto Scaling group, so it’s no longer needed.
