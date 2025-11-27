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
<img width="1915" height="896" alt="image" src="https://github.com/user-attachments/assets/53e054fa-5b83-43be-ab71-508331a946c8" />
<img width="1912" height="452" alt="image" src="https://github.com/user-attachments/assets/2fbc46ba-115f-4764-bac8-145c9dd514fc" />
Here is what i did here:

- I downloaded a CloudFormation template called task1.yaml.
- The file is written in YAML and tells AWS what resources to create.
- The template has three parts:
    - Parameters – asks for two CIDR ranges (VPC and subnet); defaults are already set.
    - Resources – defines a VPC and a Security Group.
    - Outputs – shows the default Security Group ID after the stack is built.
- Here’s what I did to deploy the stack:
    - Saved the file by right‑clicking the link and choosing “Save as task1.yaml”.
    - Opened it in a plain‑text editor to look at the three sections.
    - Went to the AWS console → Services → CloudFormation.
    - Clicked Create stack, chose Upload a template file, selected task1.yaml, and clicked Next.
    - Named the stack Lab (the parameters were already filled with defaults).
    - Skipped the Options page, kept the defaults, and clicked Next.
    - On the Review page I acknowledged the custom‑name warning and clicked Create stack.
    - Watched the progress: the Events tab showed each step (VPC → Security Group) and the Resources tab listed everything being created in the right order.
    - Waited until the status changed to CREATE_COMPLETE (refreshed a few times).
    - (Optional) Checked the new VPC in the VPC console, then went back to CloudFormation.

That’s the whole lab in a nutshell.

***2: Add an Amazon S3 Bucket to the Stack*
<img width="1908" height="873" alt="image" src="https://github.com/user-attachments/assets/901f4358-3979-4253-8763-d5958fa811e5" />
<img width="1909" height="623" alt="image" src="https://github.com/user-attachments/assets/b6933b9d-30a3-4fde-affc-1d1588d57662" />
<img width="1895" height="877" alt="image" src="https://github.com/user-attachments/assets/02f65e33-20ce-4961-8513-ae9698c316c2" />
<img width="1913" height="866" alt="image" src="https://github.com/user-attachments/assets/c37b0d1d-cd0f-453c-ab02-57d763b3e7c7" />
<img width="1918" height="868" alt="image" src="https://github.com/user-attachments/assets/3c916e74-5796-4b9c-9ba7-e99e5c22fbb0" />
<img width="1912" height="862" alt="image" src="https://github.com/user-attachments/assets/2488943c-0d35-4430-83db-885837a61104" />
Here is what I did:

- I edited task1.yaml to add an S3 bucket under Resources (MyS3Bucket: Type: AWS::S3::Bucket).
- Then I updated the Lab stack by uploading the file and clicking Update.
- The stack finished with UPDATE_COMPLETE and the bucket appeared in the Resources list.
- I also checked it in the S3 console. 

***3: Add an Amazon EC2 Instance to the Stack*

- I added a parameter called AmazonLinuxAMIID to fetch the latest Amazon Linux AMI from SSM.
- I edited the template under Resources to create an EC2 instance.
- The instance uses ImageId: !Ref AmazonLinuxAMIID, InstanceType: t3.micro, SecurityGroupIds: - !Ref AppSecurityGroup, SubnetId: !Ref PublicSubnet, and Tags: - Key: Name Value: App Server.
- I uploaded the updated template and clicked Update on the Lab stack.
- The stack updated successfully and the new instance appeared in the Resources tab.
- I verified the App Server in the EC2 console.
