# **Service Notes: System & Network Hardening**
***
**Author:** Mokgadi Selepe

***

## **System Hardening with AWS Systems Manager Patch Manager**

### **1. Patch Linux Instances Using Default Baselines**

*   Open **Systems Manager** from the AWS console.
*   Navigate to **Fleet Manager** to view Linux and Windows EC2 instances.
*   Go to **Patch Manager** under Node Management.
*   Click **Patch now** and apply the default baseline `AWS-AmazonLinux2DefaultPatchBaseline`.
*   Configuration:
    *   **Operation:** Scan and install
    *   **Reboot option:** Reboot if needed
    *   **Target selection:** Specify instance tags → `Patch Group = LinuxProd`
*   Monitor the patch job until completion.

***

### **2. Create a Custom Patch Baseline for Windows Instances**

*   In **Patch Manager**, click **Patch baselines → Create patch baseline**.
*   Details:
    *   **Name:** WindowsServerSecurityUpdates
    *   **OS:** Windows
    *   **Approval rules:**
        *   Rule 1: Products = WindowsServer2019, Severity = Critical, Classification = SecurityUpdates, Auto-approval = 3 days
        *   Rule 2: Products = WindowsServer2019, Severity = Important, Classification = SecurityUpdates, Auto-approval = 3 days
*   Link the baseline to patch group `WindowsProd`.

***

### **3. Patching Windows Instances**

*   Tag Windows EC2 instances: `Patch Group = WindowsProd`.
*   In **Patch Manager**, run **Patch now** for tagged instances.
*   Monitor execution and verify compliance.

***

### **4. Verifying Compliance**

*   Open **Patch Manager Dashboard**:
    *   Compliance summary shows all instances as **Compliant**.
    *   Drill down for details like installed patches and timestamps.

***

### **Conclusion**

*   Patched Linux instances using default baseline.
*   Created and applied custom Windows patch baseline.
*   Verified compliance for all instances.

***

## **Network Hardening with Amazon Inspector**

### **1. Activate Amazon Inspector**

*   Search for **Inspector** in AWS console.
*   Click **Activate Inspector** for your account.
*   Inspector scans EC2, ECR, and Lambda by default.

***

### **2. Reviewing Inspected Resources**

*   Go to **Findings → All findings**.
*   Review vulnerabilities (e.g., CVE-2023-132681 in `requests` package).
*   Click Vulnerability ID for details on NVD.

***

### **3. Remediating Vulnerabilities**

*   Open Lambda function in AWS console.
*   Edit `requirements.txt`:
    *   Remove version pin (e.g., `requests==2.20.0` → `requests`).
*   Deploy changes and confirm Inspector scan closes the finding.

***

### **Conclusion**

*   Enabled Amazon Inspector.
*   Reviewed and remediated vulnerabilities in Lambda functions.
*   Verified findings are closed and resources are secure.

***

## **Contact**

**<mokgadi9939@gmail.com>**
