# **Automated and Repeatable Deployments**
```markdown
# CloudFormation Lab

This project is about learning how to use AWS CloudFormation to create and manage resources. I worked through a few tasks step by step and noted what I did and learned.

---

## Task 1: Deploy a CloudFormation Stack
- I downloaded a template file called `task1.yaml`.
- The template is written in YAML and defines:
  - **Parameters**: asks for CIDR ranges (IP blocks) for VPC and subnet.
  - **Resources**: creates a VPC and a Security Group.
  - **Outputs**: shows the default Security Group ID after the stack is built.
- I uploaded the template in the CloudFormation console and created a stack named **Lab**.
- I watched the Events and Resources tabs until the status changed to `CREATE_COMPLETE`.
- Optional: I checked the VPC console to confirm the new VPC was created.

---

## Task 2: Add an Amazon S3 Bucket
- I edited `task1.yaml` and added this under **Resources**:

  ```yaml
  MyS3Bucket:
    Type: AWS::S3::Bucket
  ```

- I updated the stack in the CloudFormation console with the new template.
- After the update, the bucket appeared in the Resources tab.
- CloudFormation gave the bucket a random unique name.
- Optional: I checked the S3 console to confirm the bucket was created.

---

## Task 3: Add an Amazon EC2 Instance
- I added a new parameter for the Amazon Linux AMI:

  ```yaml
  AmazonLinuxAMIID:
    Type: AWS::SSM::Parameter::Value<AWS::EC2::Image::Id>
    Default: /aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2
  ```

- Then I added an EC2 instance under **Resources** with these properties:
  - **ImageId**: `!Ref AmazonLinuxAMIID`
  - **InstanceType**: `t3.micro`
  - **SecurityGroupIds**: `!Ref AppSecurityGroup`
  - **SubnetId**: `!Ref PublicSubnet`
  - **Tags**: Name = App Server
- I updated the stack again and saw the new EC2 instance in the Resources tab.
- Optional: I checked the EC2 console to confirm the instance was running.

---

## Task 4: Delete the Stack
- In the CloudFormation console, I selected the **Lab** stack.
- Clicked **Delete**, then confirmed.
- The stack status changed to `DELETE_IN_PROGRESS` and after a few minutes it disappeared.
- Optional: I verified that the VPC, S3 bucket, and EC2 instance were all deleted.

---

## What I Learned
- YAML formatting is strict (indentation matters).
- CloudFormation templates can be updated easily to add new resources.
- Parameters make templates flexible by allowing input values.
- Outputs provide quick access to important resource details.
- Deleting a stack removes all resources it created automatically.
```
-Contact: Mokgadi - mokgadi9939@gmail.com
