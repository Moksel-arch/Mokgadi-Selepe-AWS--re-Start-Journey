# **Introduction to Amazon EC2**

**Overview**

<img width="549" height="419" alt="image" src="https://github.com/user-attachments/assets/93c37cd7-76a1-43aa-83b4-ec2a99a5c9c5" />

In this lab I’m going to walk through the basics of working with an Amazon EC2 instance – from launching it, to resizing, managing, and finally monitoring its performance.

Amazon EC2 is essentially a cloud‑based computer that you can spin up on demand. Because it’s part of AWS, you get a simple web interface that lets you grab a new server in just a few clicks, scale it up or down as your needs change, and only pay for the compute time you actually use.

Here’s what the lab covers, in plain English:

- Launch an instance – I pick an Amazon Machine Image (AMI), choose the instance type, and fire it up.
- Resize the instance – I can change the instance size (CPU, memory, etc.) while it’s running or stop it and resize it later.
- Manage the instance – I start, stop, reboot, or terminate the server, and attach or detach storage as needed.
- Monitor the instance – I use CloudWatch to keep an eye on CPU usage, network traffic, and other metrics, so I know if something’s going wrong.

By the end of the lab I’ll have a solid feel for how EC2 lets you get compute resources quickly, scale them flexibly, and keep everything running smoothly without having to buy physical hardware.

**Task 1: Launching your EC2 instance**

I just started the first part of the lab, so here’s what I’m doing:

- I opened the AWS Management Console, went to the Services menu and picked EC2.
- In the left‑hand navigation pane I clicked EC2 Dashboard just to make sure I’m on the right page.
- Next I hit Launch instance (the button that says “Launch instance”) to start creating a new virtual server.

What’s happening now:

1. I’m going to launch an Amazon EC2 instance, but I’ll turn on termination protection so I can’t accidentally delete the instance later.
2. I’ll also add a User Data script that will automatically set up a simple web server when the instance boots up

3. <img width="1888" height="872" alt="image" src="https://github.com/user-attachments/assets/3b77ff4c-8836-42f6-828e-1498c58630e7" />
<img width="1893" height="876" alt="image" src="https://github.com/user-attachments/assets/afe6051c-a02d-40af-bb60-fa02b834e4e3" />
<img width="1911" height="875" alt="image" src="https://github.com/user-attachments/assets/00f7db06-7262-4e80-babb-13ef12d986a3" />
<img width="1891" height="868" alt="image" src="https://github.com/user-attachments/assets/f19d6bb0-b4db-4d58-ba3c-f4a214cff921" />

***Step 1: Naming my EC2 instance*




