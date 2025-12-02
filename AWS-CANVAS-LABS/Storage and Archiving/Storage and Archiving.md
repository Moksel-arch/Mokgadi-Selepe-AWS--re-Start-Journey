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

<img width="1538" height="970" alt="image" src="https://github.com/user-attachments/assets/375c8079-b70d-45b0-8454-f84dab928ad5" />

***Objectives*
- By the end of this lab, you will be able to do the following:

- Create and maintain snapshots for Amazon EC2 instances.

- Use Amazon S3 sync to copy files from an EBS volume to an S3 bucket.

- Use Amazon S3 versioning to retrieve deleted files.

***1: Creating and configuring resources*
In this task, I must create an Amazon S3 bucket and configure the "Command Host" EC2 instance to have secure access to other AWS resources.
<img width="1909" height="874" alt="image" src="https://github.com/user-attachments/assets/5bdc31f8-fec8-4229-9eee-c10378247f9b" />

***1.1: Create an S3 bucket*
