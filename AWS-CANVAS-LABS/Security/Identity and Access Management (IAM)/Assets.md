**Introduction to AWS Identity and Access Management (IAM)**

I just read the intro to the IAM lab, and here’s what it says:

- In most workplaces a single login gives you access to everything – files, printers, intranet sites, etc.
- If those permissions aren’t set up carefully, someone who shouldn’t have access can easily get in.
- This lab will show how AWS Identity and Access Management (IAM) lets you control who can use which AWS resources, using users, groups, and policies.

So, the lab is going to walk through the basics of IAM: creating users, putting them into groups, and attaching policies that define what each person can do.


Here is diagram of the current environment with the listed IAM users and IAM groups.
<img width="2200" height="1100" alt="image" src="https://github.com/user-attachments/assets/9fa763d4-4caa-4413-b1b5-fcaee0cdd9a3" />

***

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

***

***Task 2: Explore users and user groups*
<img width="1919" height="880" alt="image" src="https://github.com/user-attachments/assets/7546ab31-df58-4e26-8444-b5f95a571940" />
<img width="1891" height="875" alt="image" src="https://github.com/user-attachments/assets/622ccd50-29c1-4f4a-99a3-314a86b6cbc7" />
<img width="1911" height="885" alt="image" src="https://github.com/user-attachments/assets/c0adc494-9ab1-47e2-b7f9-1a1962fc6a19" />
<img width="1892" height="876" alt="image" src="https://github.com/user-attachments/assets/b91605d9-ac60-4cf6-8e51-fdac71524a42" />
<img width="1914" height="877" alt="image" src="https://github.com/user-attachments/assets/5a1a81a8-eeb7-4a59-a83c-e3c2b879f88e" />
<img width="1906" height="870" alt="image" src="https://github.com/user-attachments/assets/002190a1-f1d4-4d46-9301-458f343c15af" />
<img width="1895" height="887" alt="image" src="https://github.com/user-attachments/assets/c9363cb2-b39b-4bc0-86a7-2a097461bee8" />
<img width="1895" height="875" alt="image" src="https://github.com/user-attachments/assets/0058f7b0-bdff-4aeb-b7ab-58b589c119dc" />
<img width="1890" height="885" alt="image" src="https://github.com/user-attachments/assets/52a9dc63-35f9-4d0e-8ecd-6de953b5fb2d" />
<img width="1890" height="890" alt="image" src="https://github.com/user-attachments/assets/965dc974-55b8-4063-a464-5b0dd6699b70" />
<img width="1903" height="879" alt="image" src="https://github.com/user-attachments/assets/697a8214-aa35-431d-a213-582784977d6e" />
<img width="1914" height="875" alt="image" src="https://github.com/user-attachments/assets/445b28d2-3f41-42ce-b36f-7a71d6b76abe" />


What I just did - a quick walk‑through:

- I opened the IAM console and looked at the Users section.
    - Three users were already there: user-1, user-2, and user-3.
    - I clicked on user-1. The Permissions tab showed that this user has no permissions at all, and the Groups tab confirmed the user isn’t in any group.
    - The Security credentials tab told me that user-1 has a console password set.

- Next I went to User groups. Three groups were already created:
    - EC2‑Admin
    - EC2‑Support
    - S3‑Support

- EC2‑Support group
    - I opened its Permissions tab and saw a managed policy called AmazonEC2ReadOnlyAccess.
    - I expanded the policy and saw it lets you list and describe EC2, ELB, CloudWatch, and Auto Scaling resources – perfect for a read‑only support role.

- S3‑Support group
    - This group has the managed policy AmazonS3ReadOnlyAccess.
    - Expanding the policy showed it only allows Get and List actions on S3 buckets.

- EC2‑Admin group
    - Unlike the other groups, this one uses a customer inline policy (EC2‑Admin‑Policy).
    - The inline policy lets you describe EC2 resources and start or stop instances – a one‑off set of permissions for an admin role.

- Business scenario
    - The lab now expects me to map the users to groups with the right level of access:
        - user-1 → S3‑Support → read‑only S3
        - user-2 → EC2‑Support → read‑only EC2
        - user-3 → EC2‑Admin → view, start, and stop EC2 instances

That’s the whole picture: I inspected the pre‑created users and groups, looked at the policies attached to each group, and understood how the permissions line up with the business needs.

***

***3: Add users to user groups*
<img width="1919" height="898" alt="image" src="https://github.com/user-attachments/assets/476e7072-9234-4c68-b226-75df4a82a475" />
<img width="1916" height="888" alt="image" src="https://github.com/user-attachments/assets/b1b4f029-bf7e-48d7-abbe-584a4602bee6" />
<img width="1907" height="874" alt="image" src="https://github.com/user-attachments/assets/091ce904-739a-46b4-bb1a-f9c1d5bc0d89" />
<img width="1915" height="882" alt="image" src="https://github.com/user-attachments/assets/6243f6e4-59da-4389-a46d-19da424ecad6" />


I just walked through adding the three users to the right groups, and here’s what I did in simple English:

- Added user‑1 to the S3‑Support group
    - Went to User groups, selected S3‑Support, opened the Users tab, clicked Add users, ticked the box for user‑1, and hit Add Users.
    - (I ignored any “not authorized” warnings – they’re just a quirk of the lab account.)

- Added user‑2 to the EC2‑Support group
    - Repeated the same steps, but chose the EC2‑Support group and selected user‑2 instead.

- Added user‑3 to the EC2‑Admin group
    - Again, same process, this time picking the EC2‑Admin group and adding user‑3.

- Checked the results
    - Back in the User groups list, each group now shows a 1 in the Users column, confirming that every user is attached to the correct group as outlined in the business scenario.

That’s it – all the users are now part of the appropriate groups and inherit the permissions they need.

***

***Task 4: Sign in and test user permissions*
<img width="1899" height="885" alt="image" src="https://github.com/user-attachments/assets/c6402b21-8142-4668-b030-98a3087eb273" />
<img width="1919" height="984" alt="image" src="https://github.com/user-attachments/assets/a7fe0744-6f2e-41d6-9466-51f2cceae97a" />
<img width="1919" height="1016" alt="image" src="https://github.com/user-attachments/assets/14d1d3fb-f073-4b52-af81-d25e0795df18" />
<img width="1915" height="978" alt="image" src="https://github.com/user-attachments/assets/08b2b098-4691-4cce-95ba-baec1f154435" />
<img width="1916" height="869" alt="image" src="https://github.com/user-attachments/assets/8d3db7bd-1c1b-445d-9bed-4c9878fc77ad" />
<img width="1917" height="965" alt="image" src="https://github.com/user-attachments/assets/a3961ab2-38a7-4b79-bc13-d0930b0efe4e" />
<img width="1919" height="968" alt="image" src="https://github.com/user-attachments/assets/91f95501-263d-4368-8c5a-4d2d1ead8665" />
<img width="1919" height="978" alt="image" src="https://github.com/user-attachments/assets/42a1f4fa-b5d0-4ac4-b342-db7dd20b86da" />
<img width="1919" height="971" alt="image" src="https://github.com/user-attachments/assets/1be44a82-7ad2-4c3d-bfd1-1a566d680771" />
<img width="1919" height="789" alt="image" src="https://github.com/user-attachments/assets/9cbf432f-ffe6-4331-9ec2-13d87cdcfa20" />
<img width="1919" height="1012" alt="image" src="https://github.com/user-attachments/assets/96087724-3772-4fa3-9fb8-dd2e747332b9" />
<img width="1916" height="1009" alt="image" src="https://github.com/user-attachments/assets/acdd5b0e-3d93-45fc-a640-86a19eacdaf9" />
<img width="1910" height="967" alt="image" src="https://github.com/user-attachments/assets/82febbf7-50e8-4176-93c4-246680e421d4" />
<img width="1915" height="978" alt="image" src="https://github.com/user-attachments/assets/9ad025c1-218d-41ce-a304-d95c8fad31cd" />
<img width="1911" height="956" alt="image" src="https://github.com/user-attachments/assets/2df90686-dd0a-40ca-95f3-18ce7b84fcbd" />
<img width="1919" height="975" alt="image" src="https://github.com/user-attachments/assets/7d92d45c-7a27-43ab-92b7-a56ee1a117e8" />
<img width="1910" height="976" alt="image" src="https://github.com/user-attachments/assets/3ba8adc3-60f8-42f7-b4c2-b4a61c308a70" />
<img width="1896" height="1002" alt="image" src="https://github.com/user-attachments/assets/c871ec7e-cba5-4eae-8992-5c6e90c7bedb" />
<img width="1919" height="978" alt="image" src="https://github.com/user-attachments/assets/63b3b1aa-7bc6-4162-819b-586e67a3abfe" />
<img width="1919" height="974" alt="image" src="https://github.com/user-attachments/assets/f83da2bc-baee-40a9-a543-2de9b89dedd7" />
<img width="1919" height="986" alt="image" src="https://github.com/user-attachments/assets/39606327-15bd-45b1-84af-8caba7cdddea" />

This task was about **signing in and testing IAM user permissions** in AWS. The goal was to check what each user can and cannot do based on their assigned permissions.

***

#### **Steps Taken:**

*   **Sign in as user-1 (S3 Support Staff):**
    *   Used the IAM Sign-in URL in a private browser window.
    *   Entered credentials:
        *   Username: `user-1`
        *   Password: `Lab-Password1`
    *   Checked **Amazon S3**:
        *   Could view buckets and their contents (because user-1 is in the S3-Support group).
    *   Checked **Amazon EC2**:
        *   Could NOT view instances.
        *   Message: *You are not authorized to perform this operation.*

***

*   **Sign in as user-2 (EC2 Support Person):**
    *   Signed out user-1 and signed in with:
        *   Username: `user-2`
        *   Password: `Lab-Password2`
    *   Checked **Amazon EC2**:
        *   Could view EC2 instances (read-only permissions).
        *   Tried to stop an instance → Failed.
            *   Message: *You are not authorized to perform this operation.*
    *   Checked **Amazon S3**:
        *   Could NOT view buckets.
        *   Message: *You don't have permissions to list buckets.*

***

*   **Sign in as user-3 (EC2 Administrator):**
    *   Signed out user-2 and signed in with:
        *   Username: `user-3`
        *   Password: `Lab-Password3`
    *   Checked **Amazon EC2**:
        *   Could view EC2 instances.
        *   Successfully stopped an instance (full EC2 admin permissions).

***

### **Summary of Task**

*   **user-1:** Can view S3 buckets but cannot access EC2.
*   **user-2:** Can view EC2 instances but cannot stop them; cannot access S3.
*   **user-3:** Can view and manage EC2 instances (including stopping them).

***

**This exercise shows how IAM policies control what each user can do in AWS.**

***

**Conclusion**

I’m done! Here’s what I’ve wrapped up:

- Created and applied an IAM password policy.
- Explored the pre‑created IAM users and user groups.
- Inspected the policies attached to those groups.
- Added each user to the appropriate group with the right permissions.
- Located and used the IAM sign‑in URL.
- Tested how the policies affect access to S3 and EC2.

All set!

---
Contacts:
- Mokgadi: 067 719 3860
- mokgadi9939@gmail.com
