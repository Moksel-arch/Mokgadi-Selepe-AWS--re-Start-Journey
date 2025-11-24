**Introduction to AWS Identity and Access Management (IAM)**

I just read the intro to the IAM lab, and here’s what it says:

- In most workplaces a single login gives you access to everything – files, printers, intranet sites, etc.
- If those permissions aren’t set up carefully, someone who shouldn’t have access can easily get in.
- This lab will show how AWS Identity and Access Management (IAM) lets you control who can use which AWS resources, using users, groups, and policies.

So, the lab is going to walk through the basics of IAM: creating users, putting them into groups, and attaching policies that define what each person can do.


Here is diagram of the current environment with the listed IAM users and IAM groups.
<img width="2200" height="1100" alt="image" src="https://github.com/user-attachments/assets/9fa763d4-4caa-4413-b1b5-fcaee0cdd9a3" />

***Task 1: Create an account password policy*
<img width="1905" height="893" alt="image" src="https://github.com/user-attachments/assets/b0a32f53-85db-4535-a73d-97bbddcb6ae7" />
<img width="1901" height="876" alt="image" src="https://github.com/user-attachments/assets/d4701424-7c6e-4c0d-8176-1a9596034415" />
<img width="1895" height="868" alt="image" src="https://github.com/user-attachments/assets/640b1adb-7146-44d3-a110-a91cafa30c44" />
<img width="1903" height="877" alt="image" src="https://github.com/user-attachments/assets/3839ad4d-03be-49af-be39-0bdf4c831211" />
<img width="749" height="209" alt="image" src="https://github.com/user-attachments/assets/6ae40bbe-a299-4dbe-8c68-186491bcb112" />
<img width="1885" height="878" alt="image" src="https://github.com/user-attachments/assets/36046130-ad41-45d3-8e94-7eeb38aadfcf" />
Here’s what I just did:

- I opened the AWS console and checked the Region in the top‑right corner (for example, Oregon).
- I typed IAM in the search box and opened the IAM service.
- In the left‑hand menu I clicked Account settings to see the current password policy.
- The default policy was too weak, so I chose Change password policy.
- I set the minimum password length to 10 characters (instead of the default 8).
- I ticked every box except the one that says Password expiration requires administrator reset.
- I left Enable password expiration at the default 90 days and Prevent password reuse at the default 5 passwords.
- I hit Save changes.

What happened:
All users in this AWS account now have to follow a stricter password policy—longer passwords, extra complexity requirements, passwords that expire after 90 days, and they can’t reuse the last five passwords. This makes the passwords much harder to crack.

