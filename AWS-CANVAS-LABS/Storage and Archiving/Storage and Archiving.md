# ***Managing Storage*

I worked through a lab that shows how to manage data on an Amazon EBS volume.

- What I did
    - I opened the AWS Command Line Interface (AWS CLI) from the “Command Host” instance.
    - I created snapshots of an EBS volume that is attached to the “Processor” instance.
    - I set up a simple scheduler (using a cron‑like entry) that runs a Python script to delete older snapshots automatically.
    - In the challenge part, I used the aws s3 sync command to copy the contents of a directory on the EBS volume to an Amazon S3 bucket.

- My lab environment
    - A VPC with a public subnet.
    - Two EC2 instances already running:
        - Command Host – the machine I used to run all AWS CLI commands and manage resources.
        - Processor – the instance whose EBS volume I was snapshotting and syncing.

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/375c8079-b70d-45b0-8454-f84dab928ad5" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/46741209-9ee9-4e99-b94f-810e6f19d246" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/b356eea5-6f0b-473e-953c-438e5b44f5c8" />


***Objectives*

- By the end of this lab, you will be able to do the following:

- Create and maintain snapshots for Amazon EC2 instances.

- Use Amazon S3 sync to copy files from an EBS volume to an S3 bucket.

- Use Amazon S3 versioning to retrieve deleted files.

***Creating and configuring resources*
In this task, I must create an Amazon S3 bucket and configure the "Command Host" EC2 instance to have secure access to other AWS resources.

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/5bdc31f8-fec8-4229-9eee-c10378247f9b" />

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/f0bce62e-e80c-4ba4-ad9c-f4f4e05335da" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/0f9c3409-6fd3-4d4f-b1c9-c294e703ee64" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/d3377177-5f76-48af-b0d7-46941530e9a8" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/044c25cc-2600-45c7-967c-e5bcc2b1f361" />

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/0a3cee5b-839d-4526-a8c4-ad673973a24a" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/0c690ee5-369d-4657-8500-3f60e6ad3e2b" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/f808e331-310e-436c-82ca-866180da8ba1" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/4827630a-b92c-4ba6-98e7-f181b19c9a9c" />

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/7bc53f98-e001-43ec-affd-260578704a38" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/734a42d9-b91b-4072-888b-a61800ad32a3" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/919357af-b7eb-478c-aeab-b98aa8bc4921" />

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/6fdad716-3193-429a-af05-c9fb970ea720" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/e0dadfe5-776f-4a51-a8ea-7a2519c8e24a" />

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/ea12ab0d-eb77-4f86-becb-19af3d39903a" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/338af5aa-858f-402e-ac33-be61adea7b1e" />

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/65d143c7-65ce-430c-b584-43e5692ff32c" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/2297e51a-8043-4cd4-a9fe-c9483b70491d" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/548650f7-a334-4fc1-be44-65e0c0bf4232" />

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/18fd1bdb-29c0-4f3a-b6d3-91d61857ffb0" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/bd7b9598-5c6c-4135-8c75-892444e1d3d5" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/66777c56-802a-46a6-9451-17adc6f111db" />

***Created an S3 bucket*

What Happened:

- I created an Amazon S3 bucket to store files and data from my EC2 instances.
- I attached an IAM role (S3BucketAccess) to the Processor EC2 instance so it could securely interact with S3 and EBS volumes.
- I connected to the Command Host EC2 instance using EC2 Instance Connect, which gave me a terminal to run AWS CLI commands.
- I identified the EBS volume attached to the Processor instance and took an initial snapshot of it.
- I scheduled automatic snapshots using a cron job so that new snapshots were created every minute.
- I ran a Python script (snapshotter_v2.py) to keep only the last two snapshots and delete the older ones.
- I synced files between my EC2 instance and the S3 bucket, enabling versioning so I could recover deleted files.
- I tested the sync process by deleting a file locally, syncing again with the --delete option, and then restoring the deleted file using S3 versioning.
- I reviewed the Security Groups in the AWS console, which showed how inbound and outbound traffic rules protect my instances.
---
What I Learned
- S3 Buckets are useful for storing and syncing files, and versioning helps recover deleted data.
- IAM roles allow EC2 instances to securely access other AWS services without needing manual credentials.
- Snapshots are backups of EBS volumes, and they can be automated with cron jobs to ensure regular backups.
- Python scripts can be used to manage snapshots efficiently, keeping only the most recent ones.
- Security Groups act like firewalls, controlling which traffic can reach my EC2 instances.
- Managing storage in AWS involves not just saving data, but also setting up permissions, backups, and recovery processes.
- I practiced using the AWS CLI, which is a powerful tool for automating tasks and managing resources directly from the terminal.
---
In simple terms: I learned how to store, back up, sync, and recover data in AWS while keeping everything secure with IAM roles and security groups.

---
Contacts:
- Mokgadi: 067 719 3860
- mokgadi9939@gmail.com

