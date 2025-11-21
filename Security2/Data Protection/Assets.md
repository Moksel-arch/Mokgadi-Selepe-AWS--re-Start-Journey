**DATA PROTECTION USING ENCRYPTION**

<img width="1231" height="753" alt="image" src="https://github.com/user-attachments/assets/8d548423-60bd-449d-ae3b-8e3b644128dc" />

*1: Create an AWS KMS key*
<img width="1901" height="875" alt="image" src="https://github.com/user-attachments/assets/16d42f8b-5c7d-43fd-ba9c-549429875b33" />

I opened the AWS console and searched for KMS, then chose Key Management Service.
- Clicked Create a key.
- Chose Symmetric (the same key encrypts and decrypts) and clicked Next.
- On the “Add labels” page I set:
    - Alias: MyKMSKey
    - Description: Key used to encrypt and decrypt data files
and clicked Next.
- For key administrators I selected the voclabs role and clicked Next.
- For key usage permissions I also selected voclabs and clicked Next.
- Reviewed the settings and chose Finish.

After the key was created I opened its details, copied the ARN to a text editor (I’ll need it later), and noted that the key is symmetric and owned by the voclabs IAM role.

So, I just created a simple symmetric KMS key called MyKMSKey and gave the voclabs role permission to use it.

