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
<img width="1914" height="877" alt="image" src="https://github.com/user-attachments/assets/d965fec9-d0f4-4f1e-b4c9-d74e20dfc294" />
<img width="1911" height="884" alt="image" src="https://github.com/user-attachments/assets/8ddd3d7f-1278-411f-b802-a8f7a861b7e2" />
