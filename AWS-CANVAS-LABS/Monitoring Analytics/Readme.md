# Monitoring Analytics with AWS

Hi, this is my project on setting up monitoring for an EC2 web server using AWS services. The goal was to learn how to watch my applications and infrastructure to keep them running smoothly and follow best practices for security and compliance.

## Project Overview

In cloud setups, it's really important to monitor everything so systems stay up and secure. In this project, I used Amazon CloudWatch, AWS Systems Manager, and AWS Config to build a good monitoring system for my EC2 instance.

I collected system metrics, watched application logs in real time, and checked if my infrastructure follows the rules automatically.

## Architecture

Here's a simple diagram showing how the CloudWatch agent gets installed and configured:


## What I Did

### 1. Installing the CloudWatch Agent

I used AWS Systems Manager Run Command to install the CloudWatch agent on my Linux web server EC2 instance.

- I ran the command document AWS-ConfigureAWSPackage to install AmazonCloudWatchAgent (latest version).
- Then, I saved a config file in Parameter Store called Monitor-Web-Server. This config told the agent to collect Apache access and error logs, plus metrics like CPU, disk, memory, and swap.
- After that, I ran another command AmazonCloudWatch-ManageAgent to apply the config from Parameter Store and restart the agent.

Now the agent is running and sending logs to CloudWatch Logs and metrics to CloudWatch Metrics.

Here are some screenshots from the installation process:


### 2. Monitoring Application Logs with CloudWatch Logs

I generated some 404 errors on the web server by visiting bad URLs like /start.

In CloudWatch Logs, I saw the logs coming in to groups like HttpAccessLog and HttpErrorLog.

Then I created a metric filter to count 404 errors and an alarm that triggers if there are 5 or more in a minute. I set it to send email via SNS.

When I made more 404s, the alarm went off and I got an email.

This way, I can alert on log issues without changing any code.

### 3. Monitoring Instance Metrics with CloudWatch



I checked the basic EC2 metrics in the console, then went to CloudWatch Metrics to see the extra ones from the agent, like detailed memory and disk usage that you can't get from outside the instance.

### 4. Creating Real-Time Notifications

Diagram for events:

I made a CloudWatch Events rule to watch for EC2 instances stopping or terminating, and send a notification to SNS (email).

When I stopped my instance, I got an email right away with the details.

Screenshots:

### 5. Data Visualization (Dashboards)

I created a custom dashboard in CloudWatch to show graphs like CPU utilization.


### 6. Monitoring for Infrastructure Compliance with AWS Config

I turned on AWS Config and added rules:

- One to require a "project" tag on resources.
- Another to check that EBS volumes are attached.

It evaluated my resources and showed which ones were compliant and which weren't.

This helps keep everything following company rules automatically.

This project taught me a lot about AWS monitoring tools! Feel free to check out the screenshots for more details.
