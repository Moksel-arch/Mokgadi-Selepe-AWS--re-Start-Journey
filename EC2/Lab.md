# **Introduction to Amazon EC2**

**Overview**

<img width="549" height="419" alt="image" src="https://github.com/user-attachments/assets/93c37cd7-76a1-43aa-83b4-ec2a99a5c9c5" />

In this lab I’m going to walk through the basics of working with an Amazon EC2 instance – from launching it, to resizing, managing, and finally monitoring its performance.

Amazon EC2 is essentially a cloud‑based computer that you can spin up on demand. Because it’s part of AWS, you get a simple web interface that lets you grab a new server in just a few clicks, scale it up or down as your needs change, and only pay for the compute time you actually use.

Here’s what the lab covers:

- Launch an instance – I pick an Amazon Machine Image (AMI), choose the instance type, and fire it up.
- Resize the instance – I can change the instance size (CPU, memory, etc.) while it’s running or stop it and resize it later.
- Manage the instance – I start, stop, reboot, or terminate the server, and attach or detach storage as needed.
- Monitor the instance – I use CloudWatch to keep an eye on CPU usage, network traffic, and other metrics, so I know if something’s going wrong.

By the end of the lab I’ll have a solid feel for how EC2 lets you get compute resources quickly, scale them flexibly, and keep everything running smoothly without having to buy physical hardware.

**Task 1: Launching your EC2 instance**

I just started the first part of the lab, so here’s what I’m doing:

- I opened the AWS Management Console, went to the Services menu and picked EC2.
- In the left‑hand navigation pane I clicked EC2 Dashboard just to make sure I’m on the right page.
- Next I hit Launch instance (the button that says “Launch instance”) to start creating a new virtual server.

What’s happening now:

1. I’m going to launch an Amazon EC2 instance, but I’ll turn on termination protection so I can’t accidentally delete the instance later.
2. I’ll also add a User Data script that will automatically set up a simple web server when the instance boots up


<img width="1888" height="872" alt="image" src="https://github.com/user-attachments/assets/3b77ff4c-8836-42f6-828e-1498c58630e7" />
<img width="1893" height="876" alt="image" src="https://github.com/user-attachments/assets/afe6051c-a02d-40af-bb60-fa02b834e4e3" />

***Step 1 & 2: Naming my EC2 instance and Choosing an Amazon Machine Image (AMI)*
<img width="1902" height="871" alt="image" src="https://github.com/user-attachments/assets/b40102c0-dfd6-4f98-b1d9-8076cf071495" />

***Step 3: Choosing an instance type*
<img width="1917" height="877" alt="image" src="https://github.com/user-attachments/assets/847bc9e5-f242-4093-a8a7-8bb8177ddec5" />

***Step 4: Configuring a key pair*
<img width="1900" height="868" alt="image" src="https://github.com/user-attachments/assets/56039057-f802-4231-bfed-4a7a913be1f5" />

***Step 5: Configuring the network settings *
<img width="1896" height="876" alt="image" src="https://github.com/user-attachments/assets/ef338c42-3857-463b-905e-724daa90e58c" />

***Step 6: Adding storage*
<img width="1894" height="873" alt="image" src="https://github.com/user-attachments/assets/822657b5-23b3-495e-b327-a73e419b877a" />

***Step 7: Configuring advanced details *
<img width="1899" height="873" alt="image" src="https://github.com/user-attachments/assets/d5bdd7ab-5350-4398-bd3e-bc10c49201fe" />
<img width="1919" height="883" alt="image" src="https://github.com/user-attachments/assets/6c43484c-0e75-43b1-9446-60dba64ea1c6" />
<img width="1904" height="882" alt="image" src="https://github.com/user-attachments/assets/92bee2fe-8b52-4132-a4e0-5709f1d69c58" />

***Step 8: Launching an EC2 instance*
<img width="1898" height="878" alt="image" src="https://github.com/user-attachments/assets/5f5458a7-5847-4091-a3e1-d4fe4270c2cf" />
<img width="1906" height="873" alt="image" src="https://github.com/user-attachments/assets/b407db68-ab19-46b5-9d3b-436cb93ed4ee" />
<img width="1906" height="893" alt="image" src="https://github.com/user-attachments/assets/dacbd5eb-0309-4595-a1cf-64a9747e975b" />

Here's what happened:

I created a virtual server on Amazon Web Services (AWS) called an EC2 instance. Here's what I did:

1. Named the instance: I named it "Web Server".
2. Chose an operating system: I selected Amazon Linux 2023 as the operating system.
3. Selected instance type: I chose a t3.micro instance, which has 2 virtual CPUs and 1 GB of memory.
4. Configured security: I created a security group to control traffic to the instance and removed SSH access for security.
5. Added storage: I used the default 8 GB disk volume.
6. Enabled termination protection: I enabled protection to prevent accidental termination of the instance.
7. Added a script: I added a script that installs a web server (Apache) and creates a simple web page.
8. Launched the instance: I launched the instance and waited for it to start running.

Now, my web server is up and running, and I can access it using its public DNS name!
                                                                                                                                                                                                                              


**Task 2: Monitor Your Instance**








