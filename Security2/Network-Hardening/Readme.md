# **Using Amazon Inspector to Scan and Fix Vulnerabilities in Lambda Functions**

This is just my quick write-up of the AWS lab I did on Amazon Inspector (focusing on Lambda package scanning and remediation). I turned it into a simple README so I can keep it with my code examples and remember what I actually did. No fancy stuff, just what happened step by step.

### What I did – quick summary
I activated Amazon Inspector in my account, let it scan my Lambda functions, found a real vulnerability in the `requests` library (CVE-2023-32681), updated the package to the latest version, deployed the fix, and confirmed Inspector marked the finding as closed. Everything is now clean.

### Steps I followed

#### 1. Turning on Amazon Inspector
- Searched for "Inspector" in the AWS console and opened it.
- Clicked **Activate Inspector** in the left menu (you only do this once per account).
- Closed the welcome survey and banner, refreshed a couple times until the dashboard showed 100% coverage for Lambda functions.
- It automatically enables scanning for EC2, ECR, and Lambda by default. Cool, no extra config needed.

#### 2. Checking the findings
- Went to **Findings → All findings**.
- Saw three medium-severity findings, all related to outdated packages in my `get-request` Lambda function.
- Clicked on the one titled **CVE-2023-32681 – requests**.
- Clicked the link to the NVD page – properly scary vulnerability in older versions of `requests`.
- In the remediation section, Inspector straight-up told me: "Upgrade the requests package". Super helpful.

#### 3. Fixing the vulnerability
- Opened the Lambda console, went to my `get-request` function.
- In the inline code editor, opened `requirements.txt`.
- Changed this line:
  ```
  requests==2.20.0
  ```
  to just:
  ```
  requests
  ```
  (this way Lambda pulls the latest secure version).
- Hit **Deploy** → success banner appeared.
- Because the function changed, Inspector automatically started a new scan.
- Went back to Inspector → Findings → switched filter to **Closed**.
- Saw CVE-2023-32681 now listed as Closed. Nice!
- Checked **Resources coverage → Lambda functions** → last scanned timestamp was updated → confirmed the new version was scanned.

### Result
Zero active findings, Lambda function is using a safe version of `requests`, and Inspector automatically keeps watching it for future issues.

### Why this matters to me
I already knew about Inspector for EC2/ECR, but I didn't realize it also scans Lambda packages and code so easily. The fact that it re-scans automatically when you deploy a new version is honestly awesome for keeping things secure without extra work.

That's it! Short lab, but I learned a ton. If I ever build anything real with Lambda, Inspector is definitely staying enabled.

– Mokgadi
``` 

This reads like something I would actually write after finishing the lab – casual, personal, no emojis or badges or anything over-the-top. Just clear and useful for future me (or anyone else who stumbles on the repo).
```
