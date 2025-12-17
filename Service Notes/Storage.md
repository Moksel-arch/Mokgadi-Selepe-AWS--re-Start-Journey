# My Notes on AWS Storage - EBS and S3 Lab

Hey everyone! These are my personal notes from a hands-on lab I did about managing storage in AWS. I focused on Amazon EBS (block storage for EC2) and Amazon S3 (object storage). I wrote everything so I can come back to it later and understand what I did without confusion.

## What the Lab Was About

The main goal was to learn how to:
- Back up EC2 storage using EBS snapshots
- Sync files from an EC2 instance to an S3 bucket
- Use S3 versioning to recover deleted files
- Automate snapshot cleanup

## My Lab Setup

There was a VPC with a public subnet and two EC2 instances already running:
- **Command Host** – This is where I ran all my AWS CLI commands from.
- **Processor** – This instance had the EBS volume I was working with (taking snapshots and syncing data from it).

## What I Did Step by Step

1. **Created an S3 Bucket**  
   I made a new S3 bucket to store files that I would sync from the EC2 instance.

2. **Set Up Permissions**  
   I attached an IAM role called "S3BucketAccess" to the Processor instance. This role gave the instance permission to read/write to S3 and manage EBS snapshots without needing to hard-code any keys.

3. **Connected to the Command Host**  
   I used EC2 Instance Connect to open a terminal on the Command Host so I could run AWS CLI commands.

4. **Found the EBS Volume and Took Snapshots**  
   I identified the volume attached to the Processor instance and created my first manual snapshot.

5. **Automated Snapshots**  
   I set up a cron job that runs every minute to create new snapshots automatically.

6. **Cleaned Up Old Snapshots**  
   I used a provided Python script (snapshotter_v2.py) that deletes older snapshots and keeps only the most recent two. This prevents the snapshot list from growing forever and saves money.

7. **Synced Files to S3**  
   I used the command `aws s3 sync /path/on/ec2 s3://my-bucket-name` to copy files from the EBS volume on the Processor instance to my S3 bucket.

8. **Enabled Versioning on the Bucket**  
   This was important because it lets me recover files that get deleted.

9. **Tested Deletion and Recovery**  
   - I deleted a file on the EC2 side.
   - Ran `aws s3 sync` again with the `--delete` flag (this removes the file from S3 too).
   - Then I went into the S3 console, found the deleted version of the file, and restored it.

10. **Checked Security Groups**  
    I looked at the security group rules to see how inbound/outbound traffic is controlled – basically a firewall for my instances.

## What I Learned (The Important Stuff)

- **EBS Snapshots** are point-in-time backups of your EC2 volumes. Super useful for recovery or creating new volumes.
- You can **automate snapshots** with cron jobs and clean them up with simple Python scripts to avoid wasting storage.
- **S3 is great for durable object storage** and works really well for backing up or archiving files from EC2.
- The `aws s3 sync` command is awesome – it only copies what changed, just like rsync.
- **Versioning in S3** saves previous versions of files, so even if you delete something, you can get it back easily.
- **IAM roles** are the safe way to give EC2 instances access to other AWS services – no need to put access keys on the machine.
- **Security Groups** control network traffic to your instances and are a key part of keeping things secure.

In short, managing storage in AWS isn't just about putting files somewhere – it's about backing them up regularly, keeping costs down by cleaning old backups, syncing efficiently, and making sure you can recover data if something goes wrong.

I really enjoyed this lab because I got comfortable using the AWS CLI for real storage tasks.

If you have any questions about this, feel free to reach out!

---

Mokgadi @ 
- Phone: 067 719 3860  
- Email: mokgadi9939@gmail.com
