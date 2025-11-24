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
<img width="1892" height="887" alt="image" src="https://github.com/user-attachments/assets/14b520be-d7d1-483a-9622-a741f4448c9b" />
<img width="1587" height="435" alt="image" src="https://github.com/user-attachments/assets/80022cf0-bd60-47d6-9181-aa0830f68d27" />
<img width="1579" height="450" alt="image" src="https://github.com/user-attachments/assets/5d665ef7-1ec8-47ea-9493-aecaaf57e7f9" />


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

<img width="1917" height="881" alt="image" src="https://github.com/user-attachments/assets/f12a044d-38c4-43be-9666-a5410a44ea02" />
<img width="1570" height="444" alt="image" src="https://github.com/user-attachments/assets/de426c6a-dd1e-47e7-ba8e-78e1b9844816" />
<img width="1543" height="260" alt="image" src="https://github.com/user-attachments/assets/cfa29f11-d765-4dfe-af48-a4e234897eac" />
<img width="1899" height="882" alt="image" src="https://github.com/user-attachments/assets/164609ba-2529-43f3-a53b-b6bcf1239403" />
<img width="1899" height="704" alt="image" src="https://github.com/user-attachments/assets/2adb369f-ef96-41b4-95d3-6df309efc998" />
Here's what happened:

I checked on the status of my virtual server (EC2 instance) to make sure it's running smoothly.

Here's what I did:

1. Checked instance status: I looked at the Status checks tab and saw that both system and instance checks passed, which means everything is okay.
2. Viewed monitoring metrics: I clicked on the Monitoring tab and saw some basic metrics about my instance, like CPU usage.
3. Took a screenshot: I took a screenshot of my instance's console to see what's happening on the screen, which can help with troubleshooting.

By doing this, I can:
- Make sure my instance is running properly
- Identify any potential issues
- Troubleshoot problems if they arise

Now I know my instance is up and running smoothly!

**Task 3: Update Your Security Group and Access the Web Server**
<img width="1247" height="821" alt="image" src="https://github.com/user-attachments/assets/8105bbbc-ccb6-462b-b36b-27d0dc1a56d0" />
<img width="1913" height="876" alt="image" src="https://github.com/user-attachments/assets/486c47c5-09a9-4111-a599-28923ba551d6" />
<img width="1917" height="661" alt="image" src="https://github.com/user-attachments/assets/cf8676a3-87ff-48b6-9725-ae1b75934ab3" />
<img width="1919" height="871" alt="image" src="https://github.com/user-attachments/assets/d599499b-9adc-40a1-9923-23bdb345823e" />
<img width="944" height="248" alt="image" src="https://github.com/user-attachments/assets/f0e00030-79bb-4f69-b34c-ae13f513e6a5" />








