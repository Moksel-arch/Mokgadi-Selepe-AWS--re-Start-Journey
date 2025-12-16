# Monitoring Analytics with AWS

Hi, this is my project on setting up monitoring for an EC2 web server using AWS services. The goal was to learn how to watch my applications and infrastructure to keep them running smoothly and follow best practices for security and compliance.

## Project Overview

In cloud setups, it's really important to monitor everything so systems stay up and secure. In this project, I used Amazon CloudWatch, AWS Systems Manager, and AWS Config to build a good monitoring system for my EC2 instance.

I collected system metrics, watched application logs in real time, and checked if my infrastructure follows the rules automatically.

## Architecture

Here's a simple diagram showing how the CloudWatch agent gets installed and configured:

![Architecture for installing CloudWatch Agent](https://github.com/user-attachments/assets/10438157-1d71-4d31-b595-338caec41f12)

## What I Did

### 1. Installing the CloudWatch Agent

I used AWS Systems Manager Run Command to install the CloudWatch agent on my Linux web server EC2 instance.

- I ran the command document AWS-ConfigureAWSPackage to install AmazonCloudWatchAgent (latest version).
- Then, I saved a config file in Parameter Store called Monitor-Web-Server. This config told the agent to collect Apache access and error logs, plus metrics like CPU, disk, memory, and swap.
- After that, I ran another command AmazonCloudWatch-ManageAgent to apply the config from Parameter Store and restart the agent.

Now the agent is running and sending logs to CloudWatch Logs and metrics to CloudWatch Metrics.

Here are some screenshots from the installation process:

![Screenshot 1](https://github.com/user-attachments/assets/b4165083-c6d4-49b1-83b0-2c4463fb9b7e)

![Screenshot 2](https://github.com/user-attachments/assets/1734ec5e-b472-45c7-b3c4-ef9985a660c6)

![Screenshot 3](https://github.com/user-attachments/assets/58af6768-f64d-4be1-b2f3-178bd5f3b259)

### 2. Monitoring Application Logs with CloudWatch Logs

Diagram for log monitoring and alerts:

![Log monitoring architecture](https://github.com/user-attachments/assets/6bc096ca-398e-4874-97d3-ead6ba90d0b3)

I generated some 404 errors on the web server by visiting bad URLs like /start.

In CloudWatch Logs, I saw the logs coming in to groups like HttpAccessLog and HttpErrorLog.

Then I created a metric filter to count 404 errors and an alarm that triggers if there are 5 or more in a minute. I set it to send email via SNS.

When I made more 404s, the alarm went off and I got an email.

This way, I can alert on log issues without changing any code.

Screenshots:

![Log screenshot 1](https://github.com/user-attachments/assets/4f7144a0-20b8-488a-9cca-edf414c2c227)

![Log screenshot 2](https://github.com/user-attachments/assets/33ff4cee-86a4-4d6c-97d3-b78d4b7b5a5f)

(and more similar ones)

### 3. Monitoring Instance Metrics with CloudWatch

Diagram for metrics:

![Metrics architecture](https://github.com/user-attachments/assets/5572d12b-2af4-4190-84d7-522857c36988)

I checked the basic EC2 metrics in the console, then went to CloudWatch Metrics to see the extra ones from the agent, like detailed memory and disk usage that you can't get from outside the instance.

### 4. Creating Real-Time Notifications

Diagram for events:

![Events architecture](https://github.com/user-attachments/assets/bf80f70b-bb0d-45cc-b6d3-79d1df96e7c5)

I made a CloudWatch Events rule to watch for EC2 instances stopping or terminating, and send a notification to SNS (email).

When I stopped my instance, I got an email right away with the details.

Screenshots:

![Events screenshot](https://github.com/user-attachments/assets/a8df0797-06ce-42f0-be1b-d59baf60e0c3)

### 5. Data Visualization (Dashboards)

I created a custom dashboard in CloudWatch to show graphs like CPU utilization.

Screenshots:

![Dashboard creation](https://github.com/user-attachments/assets/f88a2498-1347-48d0-8aed-de9fa3bee472)

![CPU graph example](https://github.com/user-attachments/assets/da6e3736-53fe-401c-82f4-82b5cc5d12d8)

![Another dashboard view](https://github.com/user-attachments/assets/77089c7c-5ec1-472a-9ef4-496cf1d5b2b7)

### 6. Monitoring for Infrastructure Compliance with AWS Config

I turned on AWS Config and added rules:

- One to require a "project" tag on resources.
- Another to check that EBS volumes are attached.

It evaluated my resources and showed which ones were compliant and which weren't.

This helps keep everything following company rules automatically.

This project taught me a lot about AWS monitoring tools! Feel free to check out the screenshots for more details.
