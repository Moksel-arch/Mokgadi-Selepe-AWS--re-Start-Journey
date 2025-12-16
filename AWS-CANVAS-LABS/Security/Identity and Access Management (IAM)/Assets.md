# **Introduction to AWS Identity and Access Management (IAM)**

I just read the intro to the IAM lab, and here’s what it says:

- In most workplaces a single login gives you access to everything – files, printers, intranet sites, etc.
- If those permissions aren’t set up carefully, someone who shouldn’t have access can easily get in.
- This lab will show how AWS Identity and Access Management (IAM) lets you control who can use which AWS resources, using users, groups, and policies.

So, the lab is going to walk through the basics of IAM: creating users, putting them into groups, and attaching policies that define what each person can do.


Here is diagram of the current environment with the listed IAM users and IAM groups.
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/9fa763d4-4caa-4413-b1b5-fcaee0cdd9a3" />

***

***Task 1: Create an account password policy*
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/b0a32f53-85db-4535-a73d-97bbddcb6ae7" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/d4701424-7c6e-4c0d-8176-1a9596034415" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/640b1adb-7146-44d3-a110-a91cafa30c44" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/3839ad4d-03be-49af-be39-0bdf4c831211" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/6ae40bbe-a299-4dbe-8c68-186491bcb112" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/36046130-ad41-45d3-8e94-7eeb38aadfcf" />

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

***

***Task 2: Explore users and user groups*
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/7546ab31-df58-4e26-8444-b5f95a571940" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/622ccd50-29c1-4f4a-99a3-314a86b6cbc7" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/c0adc494-9ab1-47e2-b7f9-1a1962fc6a19" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/b91605d9-ac60-4cf6-8e51-fdac71524a42" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/5a1a81a8-eeb7-4a59-a83c-e3c2b879f88e" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/002190a1-f1d4-4d46-9301-458f343c15af" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/c9363cb2-b39b-4bc0-86a7-2a097461bee8" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/0058f7b0-bdff-4aeb-b7ab-58b589c119dc" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/52a9dc63-35f9-4d0e-8ecd-6de953b5fb2d" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/965dc974-55b8-4063-a464-5b0dd6699b70" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/697a8214-aa35-431d-a213-582784977d6e" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/445b28d2-3f41-42ce-b36f-7a71d6b76abe" />

...

***3: Add users to user groups*
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/476e7072-9234-4c68-b226-75df4a82a475" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/b1b4f029-bf7e-48d7-abbe-584a4602bee6" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/091ce904-739a-46b4-bb1a-f9c1d5bc0d89" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/6243f6e4-59da-4389-a46d-19da424ecad6" />

...

***Task 4: Sign in and test user permissions*
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/c6402b21-8142-4668-b030-98a3087eb273" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/a7fe0744-6f2e-41d6-9466-51f2cceae97a" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/14d1d3fb-f073-4b52-af81-d25e0795df18" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/08b2b098-4691-4cce-95ba-baec1f154435" />
...
