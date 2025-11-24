

**Introduction to AWS Identity and Access Management (IAM)**
<img width="2200" height="1100" alt="image" src="https://github.com/user-attachments/assets/9549e819-3938-42d0-b7fc-a672bd18b501" />

README.md – AWS IAM Introduction Lab

---


**What this lab is about**

I wanted to see how AWS Identity and Access Management (IAM) lets you control who can use which AWS resources. The idea is simple: give people the right level of access without handing out the keys to the whole kingdom.

What I did
- Opened the AWS console and noted the Region (e.g., Oregon).
- Searched for IAM and opened the service.
- Went to Account settings → changed the password policy:
    - Minimum length = 10 characters (instead of 8)
    - Ticked every box except “Password expiration requires administrator reset”
    - Kept the defaults of 90‑day expiration and 5‑password reuse limit
    - Saved the changes.

Result: All users now have a stricter password policy.

Users and groups I found
- Users: user-1, user-2, user-3 (all with console passwords).
- Groups: EC2-Admin, EC2-Support, S3-Support.

Group permissions
- EC2-Support – managed policy AmazonEC2ReadOnlyAccess (list/describe EC2, ELB, CloudWatch, Auto Scaling).
- S3-Support – managed policy AmazonS3ReadOnlyAccess (Get/List on S3 buckets).
- EC2-Admin – custom inline policy EC2-Admin-Policy (describe, start, stop EC2 instances).

Mapping users to groups
I added the users so they inherit the right permissions:
- user-1 → S3-Support (read‑only S3)
- user-2 → EC2-Support (read‑only EC2)
- user-3 → EC2-Admin (full EC2 admin).

Testing the permissions
1. *Signed in as user-1* (private window, IAM sign‑in URL)
    - Saw S3 buckets, could browse contents.
    - Got “not authorized” when trying to view EC2 instances.

2. *Signed in as user-2*
    - Could list EC2 instances but couldn’t stop them.
    - Got “you don’t have permissions to list buckets” for S3.

3. *Signed in as user-3*
    - Could list EC2 instances and stop one successfully.

Summary
- user-1 → S3 read‑only.
- user-2 → EC2 read‑only.
- user-3 → EC2 admin.

Conclusion
I’ve walked through creating a stricter password policy, explored the pre‑created users and groups, attached the appropriate policies, added users to the right groups, and tested the resulting permissions. 

All set! 

-Mokgadi: mokgadi9939@gmail.com
