# **Automated and Repeatable Deployments**

**Lab - Automation with CloudFormation**
Lab – Automation with CloudFormation

***1: Deploy a CloudFormation Stack*
![WhatsApp Image 2025-11-27 at 19 42 50_addc3e6c](https://github.com/user-attachments/assets/a746302c-f054-4731-9204-6e238ee29251)

![WhatsApp Image 2025-11-27 at 19 36 56_d629bb47](https://github.com/user-attachments/assets/a24fa384-dd74-48d7-912f-6014d5ca1d45)
![WhatsApp Image 2025-11-27 at 19 37 32_5cee7935](https://github.com/user-attachments/assets/1737f556-8a87-4eea-8489-5baa35c08047)
![WhatsApp Image 2025-11-27 at 19 42 05_cbcea9b3](https://github.com/user-attachments/assets/9b9fcc88-d881-40e9-8a82-974bc37f916b)

<img width="1910" height="880" alt="image" src="https://github.com/user-attachments/assets/94636662-4e97-4fca-a3d8-9c1e66415532" />
<img width="1913" height="867" alt="image" src="https://github.com/user-attachments/assets/36ababef-c510-4fd3-93e9-92727c57d79e" />
<img width="1909" height="886" alt="image" src="https://github.com/user-attachments/assets/fb6c7859-3662-4e1a-9b3a-ce5618075516" />
<img width="1918" height="874" alt="image" src="https://github.com/user-attachments/assets/fac5d814-2d13-4c3b-9ffc-ec755ae73e25" />
<img width="1897" height="878" alt="image" src="https://github.com/user-attachments/assets/3cbe9ad7-4512-41f8-82b5-a6937e4587ee" />
<img width="1902" height="875" alt="image" src="https://github.com/user-attachments/assets/0d2f9117-7380-4d8b-9ab4-a937958c9b1d" />
<img width="1916" height="869" alt="image" src="https://github.com/user-attachments/assets/4c6eb235-0e6c-44e5-b818-171bc5e54ce5" />
<img width="1900" height="879" alt="image" src="https://github.com/user-attachments/assets/14afbb29-c63e-4c96-bf2e-824bb09207cf" />
<img width="1895" height="880" alt="image" src="https://github.com/user-attachments/assets/c0547941-14c5-4492-a26a-c7fbacb35718" />
Lab – Deploy a CloudFormation Stack
Explain what happened here in simple English

I downloaded a CloudFormation template called task1.yaml. It’s written in YAML, which just tells AWS what resources to create. Here’s the short version of what the template does and how I used it.

---

What the template contains
- Parameters – asks for two CIDR ranges (VPC and subnet). Defaults are already set.
- Resources – defines the VPC and a Security Group.
- Outputs – shows the default Security Group ID after the stack is built.

---

How I deployed the stack
1. Download the template (right‑click the link → save as task1.yaml).
2. Open it in a plain‑text editor to see the three sections.
3. In the AWS console, go to Services → CloudFormation.
4. Click Create stack → Upload a template file → select task1.yaml → Next.
5. Name the stack Lab (parameters already have defaults).
6. Skip the Options page (keep defaults) and click Next.
7. On the Review page, acknowledge the custom‑name warning and click Create stack.
8. Watch the stack:
    - Events tab shows each step (VPC → Security Group).
    - Resources tab lists what’s being created, in the right order.
9. Wait until the status changes to CREATE_COMPLETE (refresh if needed).
10. (Optional) Verify the new VPC in the VPC console, then return to CloudFormation.

---

What I learned
- YAML is strict about indentation and hyphens.
- Parameters let you input values; Outputs give you quick info after creation.
- Deleting the stack removes every resource it created.

That’s the whole process in plain English. I’ll update this README as I add more projects.

***2: Add an Amazon S3 Bucket to the Stack*

