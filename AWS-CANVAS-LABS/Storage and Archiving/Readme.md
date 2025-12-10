# Managing Storage - My AWS Lab Experience

Hi! This is my personal repo for the "Managing Storage" AWS lab I completed on December 11, 2025.  
I wanted to document everything I did so I can look back on it later (and maybe help others too).  
The lab was really practical – it showed how to manage EBS volumes, automate snapshots, and sync data to S3 using the AWS CLI.

## What the lab was about

The goal was to learn how to safely store and back up data on Amazon EBS volumes.  
We used the AWS Command Line Interface (CLI) to:

- Create snapshots of an EBS volume
- Automate snapshot creation with cron
- Automatically delete old snapshots so we only keep the latest ones
- Sync files from an EBS volume to an Amazon S3 bucket (including handling deletions and recovering files using S3 versioning)

## My lab environment

Everything was already set up for us:

- A VPC with a public subnet
- Two EC2 instances:
  - **Command Host** – the machine where I ran all the AWS CLI commands
  - **Processor** – the instance whose EBS volume I was working with

There was also a pre-created IAM role to give the instances the permissions they needed.

## Step-by-step what I did

### 1. Created an S3 bucket and set up permissions

- Created a new S3 bucket (I gave it a unique name)
- Attached an IAM role to the "Processor" instance so it could access S3

### 2. Took snapshots of the EBS volume

- Connected to the Command Host using EC2 Instance Connect
- Found the volume ID and instance ID of the Processor instance
- Stopped the Processor instance (required for a consistent snapshot)
- Created a manual snapshot
- Started the instance again

### 3. Automated snapshot creation

- Set up a cron job on the Command Host to create a new snapshot every minute (just for testing)
- Watched the snapshots appear by running `aws ec2 describe-snapshots`

### 4. Kept only the last two snapshots

- Stopped the cron job
- Ran a provided Python script (`snapshotter_v2.py`)
- The script deleted all but the two most recent snapshots
- After running it, only two snapshots remained – exactly what we wanted

### 5. Challenge: Sync files to S3

This was the fun part! I had to figure it out mostly on my own.

- Connected to the Processor instance
- Downloaded and unzipped a sample folder with three text files
- Enabled versioning on my S3 bucket
- Used `aws s3 sync` to upload the files to S3
- Deleted one file locally and ran `aws s3 sync --delete` to remove it from S3
- Recovered the deleted file using S3 versioning (by listing versions, downloading the old version, and syncing it back)

## What I learned

- How to create consistent EBS snapshots (by stopping the instance)
- How to automate backups with cron and clean up old snapshots with a script
- The power of `aws s3 sync` – it's great for keeping local folders and S3 buckets in sync
- How S3 versioning works and how to recover deleted files (super useful!)

## Screenshots

Here are the main screenshots I took during the lab:

![Lab diagram showing the VPC, Command Host, Processor, and S3 bucket](https://github.com/user-attachments/assets/375c8079-b70d-45b0-8454-f84dab928ad5)

![Creating the S3 bucket and attaching the IAM role to the Processor instance](https://github.com/user-attachments/assets/5bdc31f8-fec8-4229-9eee-c10378247f9b)


If you have any questions or want to see the exact commands I used, just let me know. Happy learning! 🚀

---
Contacts:
- Mokgadi: 067 719 3860
- mokgadi9939@gmail.com
