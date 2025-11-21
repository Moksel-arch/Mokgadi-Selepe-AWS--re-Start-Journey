# **Systems Hardening with Patch Manager (AWS Systems Manager)**

Here's my personal write-up from the AWS lab on Patch Manager. I did this one right after the Inspector lab, and honestly, this felt way more "real-world" because patching is something you actually have to do all the time in production. Keeping it simple and straight to the point like the last README.

### What I did – quick version
- Patched three Amazon Linux 2 instances using the default AWS baseline.
- Built a custom patch baseline just for Windows Server 2019 security updates (Critical + Important only).
- Tagged the three Windows instances with `Patch Group = WindowsProd`, linked that group to my custom baseline.
- Ran Patch Now on both Linux and Windows groups.
- Checked the compliance dashboard → all 6 instances showing Compliant. Done.

### Steps I actually followed

#### 1. Patching the Linux instances (default baseline)
- Went into Systems Manager → Fleet Manager → saw all six instances (3 Linux, 3 Windows).
- Checked details on one Linux instance just to confirm OS, role, etc.
- Back to Patch Manager → clicked **Patch now**.
- Used the default baseline (AWS-AmazonLinux2DefaultPatchBaseline).
- Set operation to **Scan and install**, reboot if needed, targeted only instances with tag `Patch Group: LinuxProd`.
- Hit Patch now → watched the progress until all three were Successful.

Super straightforward. The default baseline just works.

#### 2. Creating a custom patch baseline for Windows
- In Patch Manager → Patch baselines → **Create patch baseline**.
- Name: `WindowsServerSecurityUpdates`
- OS: Windows
- Left default baseline unchecked (wanted full control)
- Rule 1: Product = WindowsServer2019, Severity = Critical, Classification = SecurityUpdates, Auto-approve after 3 days, Compliance = Critical
- Rule 2: Same product, Severity = Important, Classification = SecurityUpdates, Auto-approve after 3 days, Compliance = High
- Created it, then selected the baseline → Actions → Modify patch groups → added `WindowsProd`

I like that I can keep Windows patching tight – only security stuff, nothing else.

#### 3. Tagging and patching the Windows instances
- Jumped to EC2 console, selected each Windows instance one by one.
- Added tag → Key: `Patch Group`, Value: `WindowsProd` on all three.
- Back to Patch Manager → Patch now again.
- This time targeted tag `Patch Group: WindowsProd`
- Scan and install, reboot if needed → ran it.
- Clicked into the run → saw it picking up my custom baseline correctly (PatchGroup: WindowsProd showed in the output).

Watched it finish on all three Windows machines.

#### 4. Checking everything is compliant
- Patch Manager Dashboard → Compliance summary = **Compliant: 6**
- Compliance reporting tab → every instance green, zero non-compliant in Critical/Security/Other
- Drilled into one Windows node → Patch tab → saw the actual list of installed security updates with timestamps.

Everything clean, no surprises.

### Result
All six instances (Linux + Windows) fully patched and showing Compliant. Linux got whatever the default baseline pulled in, Windows only got the critical/important security updates I allowed. Exactly what I wanted.

### Why I liked this lab
Patch Manager makes patching feel almost easy. The tag + patch group combo is powerful – I can have different policies for different environments and never touch the instances directly. Also, the compliance dashboard is actually useful; I can see at a glance if anything is out of date.

Definitely turning this on everywhere I work from now on.

That's it – short, practical, and now I have my own notes if I ever need to do this again.

– Mokgadi: mokgadi9939@gmail.com
