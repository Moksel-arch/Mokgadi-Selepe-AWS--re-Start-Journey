# **Monitoring Infrastructure**

- Lab goal:


learn how to keep an eye on my apps and infrastructure so they stay reliable and meet the company’s rules.

Project Overview:
- In modern cloud environments, observability and compliance are critical for maintaining system uptime and security posture. This project focuses on implementing a robust monitoring solution for EC2 infrastructure.

- Using Amazon CloudWatch, AWS Systems Manager, and AWS Config, I architected a solution to capture system-level metrics, analyze application logs in real-time, and automatically audit infrastructure for compliance deviations.

Architecture

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/10438157-1d71-4d31-b595-338caec41f12" />

What I did – Installing the CloudWatch agent:

- I opened AWS Systems Manager and chose Run Command to install the CloudWatch agent on an EC2 instance.
- I selected the pre‑written command AWS‑ConfigureAWSPackage with these settings:
    - Action: Install
    - Name: AmazonCloudWatchAgent
    - Version: latest
- I targeted the Web Server instance (Linux) and ran the command. The status changed to Success, and I checked the output to confirm the agent was installed.

- Next, I stored a configuration file in Parameter Store so the agent knows what to collect:
    - Parameter name: Monitor‑Web‑Server
    - It includes two log files (/var/log/httpd/access_log and /var/log/httpd/error_log) and several system metrics (CPU, disk, memory, swap).
- I created the parameter and then used another Run Command with the document AmazonCloudWatch‑ManageAgent:
    - Action: configure
    - Mode: ec2
    - Config source: ssm (Parameter Store)
    - Config location: Monitor‑Web‑Server
    - Restart agent: yes
- I ran the command against the same Web Server instance. When it finished successfully, the CloudWatch agent was up and running, sending the specified logs to CloudWatch Logs and the metrics to CloudWatch Metrics.

That’s it – the agent is now collecting web‑server logs and system metrics and shipping them to CloudWatch.

***1: Installing the CloudWatch agent*

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/b4165083-c6d4-49b1-83b0-2c4463fb9b7e" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/1734ec5e-b472-45c7-b3c4-ef9985a660c6" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/58af6768-f64d-4be1-b2f3-178bd5f3b259" />

---


I opened the web server, saw the test page, then typed /start and got a 404 error – that’s exactly the log data I needed.

- I switched to CloudWatch Logs and found the HttpAccessLog and HttpErrorLog groups.
- I opened the HttpAccessLog stream, saw the 404 entry for /start, and confirmed the logs were flowing in.

Next I created a metric filter:

- Pattern [ip, id, user, timestamp, request, status_code=404, size] to count 404s.
- Named it 404Errors with a metric value of 1.

Then I built an alarm:

- Trigger if 404Errors ≥ 5 in 1 minute.
- Set up a new SNS topic, entered my email, confirmed the subscription.

Finally I generated a few more 404 requests (e.g., /start2, /start3…) and waited a minute. The alarm turned red, and I got an email with the subject “ALARM: 404 Errors”.

All of this shows how CloudWatch Logs can ship, filter, and alert on application log data without any code changes.

***2: Monitoring application logs using CloudWatch Logs*

<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/6bc096ca-398e-4874-97d3-ead6ba90d0b3" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/4f7144a0-20b8-488a-9cca-edf414c2c227" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/33ff4cee-86a4-4d6c-97d3-b78d4b7b5a5f" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/7368b83b-1759-4d1a-ac4c-2cc11e7b04f2" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/0f8008b6-f1f5-4085-a684-627e87afa37c" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/36119b78-fb5a-4a47-9128-c2c3b1d7d8a1" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/73d790aa-1440-4565-9c58-3ecc1aab31be" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/29f9f7da-9097-42f0-a7cd-183c9e545b18" />
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/2e13c089-446c-43e8-b948-879ddfe1d09c" />

---

