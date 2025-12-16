# Service Notes - AWS Monitoring Setup

**Date:** December 16, 2025  
**Service/Environment:** EC2 Web Server (Linux) with Apache  
**Performed by:** Me  

These are my notes from setting up monitoring and basic compliance checks for the web server instance. Everything was done in the AWS console.

### 1. CloudWatch Agent Installation
- Used AWS Systems Manager Run Command to install the latest AmazonCloudWatchAgent on the web server instance.
- Created a configuration file in SSM Parameter Store named "Monitor-Web-Server".
- Configured it to collect:
  - Apache access log (/var/log/httpd/access_log)
  - Apache error log (/var/log/httpd/error_log)
  - System metrics: CPU, memory, disk, swap
- Applied the configuration using the AmazonCloudWatch-ManageAgent command document.
- Agent is now running and successfully sending logs to CloudWatch Logs and metrics to CloudWatch Metrics.

### 2. Application Log Monitoring
- Confirmed logs are streaming into CloudWatch Logs (groups: HttpAccessLog and HttpErrorLog).
- Created a metric filter to count HTTP 404 errors.
- Set up a CloudWatch Alarm:
  - Triggers when 404 count ≥ 5 in 1 minute
  - Sends notification to SNS topic (email subscription)
- Tested by generating multiple 404 requests - alarm triggered correctly and email was received.

### 3. Instance Metrics Monitoring
- Basic EC2 metrics (CPU, network, disk I/O) are available by default.
- With the CloudWatch agent, additional detailed metrics are now visible:
  - Memory utilization and free memory
  - Detailed disk space (used %, free space per filesystem)
- All metrics can be viewed in CloudWatch console under CWAgent namespace.

### 4. Real-Time Event Notifications
- Created a CloudWatch Events rule named "Instance_Stopped_Terminated".
- Watches for EC2 instance state changes to "stopped" or "terminated".
- Target: Existing SNS topic (email notification).
- Tested by stopping the web server instance - received immediate email notification with event details.

### 5. CloudWatch Dashboard
- Built a custom dashboard with key graphs:
  - CPU utilization
  - Memory usage
  - Disk usage
  - Network in/out
  - Custom 404 error count
- Dashboard provides quick overview of server health.

### 6. Compliance Monitoring with AWS Config
- Enabled AWS Config in the account.
- Added two managed rules:
  - required-tags: Enforces presence of "project" tag on all resources
  - ec2-volume-inuse-check: Ensures all EBS volumes are attached to instances
- Evaluation completed:
  - Web server instance compliant with tag rule
  - Some other resources flagged as non-compliant (missing tags)
  - One detached EBS volume flagged
- Will use these results to clean up and tag resources properly.

### Summary
Monitoring is now fully set up. The web server sends logs and detailed metrics to CloudWatch, alerts on errors and instance state changes, and compliance is being tracked automatically.

This gives good visibility into performance, quick alerts for issues, and helps maintain proper resource tagging and configuration.

Screenshots of each step are saved in the repo if I need to refer back or show someone else.
