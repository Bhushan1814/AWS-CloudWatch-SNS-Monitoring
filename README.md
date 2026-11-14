# AWS CloudWatch + SNS: Production Monitoring and Alerting

## 📌 Project Overview

This project demonstrates how to implement production monitoring and automated email alerts using **Amazon CloudWatch, Amazon SNS, and Amazon EC2**.

A CloudWatch alarm monitors EC2 CPU utilization and triggers an SNS notification whenever CPU usage exceeds the configured threshold of 80%.

## 🎯 Project Objectives

- Monitor EC2 instance CPU utilization.
- Configure CloudWatch alarms.
- Create SNS topics and email subscriptions.
- Generate CPU load for testing.
- Receive automated email alerts when CPU utilization exceeds the threshold.

## 🛠️ AWS Services & Technologies

| Service | Purpose |
|---|---|
| Amazon EC2 | Hosts the Linux server |
| Amazon CloudWatch | Monitors CPU utilization |
| CloudWatch Alarm | Detects high CPU usage |
| Amazon SNS | Sends email notifications |
| Linux | Executes CPU stress commands |

## 🏗️ Architecture

```text
       EC2 Instance
       (Linux Server)
             |
             |
      CPU Utilization
             |
             v
       Amazon CloudWatch
        (CPU Monitoring)
             |
             v
       CloudWatch Alarm
       (CPU > 80%)
             |
             v
          Amazon SNS
             |
             v
       Email Notification
             |
             v
        Administrator
```

## ⚙️ Implementation Steps

### Step 1: Launch EC2 Instance

- Launch an EC2 instance.
- Instance Name: `Stress-Prod-V1`
- Select Amazon Linux.
- Configure security settings.
- Launch the instance.

**Note:** For a real production environment, configure secure SSH access rather than launching without a key pair.

### Step 2: Configure CloudWatch

1. Open AWS Management Console.
2. Navigate to CloudWatch.
3. Select Alarms.
4. Click Create alarm.
5. Select EC2 metrics.
6. Choose CPUUtilization.
7. Select your EC2 instance.

### Step 3: Configure Alarm Threshold

Configure the following:

- Metric: CPUUtilization
- Statistic: Average
- Period: 1 minute
- Threshold type: Static
- Condition: Greater than 80%

### Step 4: Configure Amazon SNS

1. Open Amazon SNS.
2. Create an SNS topic.
3. Select Standard topic.
4. Create an email subscription.
5. Enter your email address.
6. Confirm the subscription through your email.
7. Attach the SNS topic to the CloudWatch alarm notification action.

### Step 5: Generate CPU Load

Connect to your EC2 instance and execute:

```bash
sudo yum update -y
```

Install the stress utility where supported:

```bash
sudo yum install stress -y
```

Generate CPU load:

```bash
stress --cpu 2 --timeout 300
```

### Step 6: Verify Email Notification

- Open CloudWatch Alarms.
- Monitor CPU utilization.
- Wait for the alarm to enter the ALARM state.
- Check your registered email inbox.
- Verify the SNS notification.

## 📊 Expected Results

When EC2 CPU utilization exceeds 80%, CloudWatch triggers the configured alarm and Amazon SNS sends an email notification.

## 📚 Key Learnings

- AWS CloudWatch monitoring.
- EC2 performance monitoring.
- CloudWatch alarm configuration.
- SNS topic and subscription management.
- Linux CPU stress testing.
- Production monitoring and alerting concepts.

## 🔐 Security & Cost Optimization

- Use IAM roles with least-privilege permissions.
- Use secure SSH access.
- Delete unused SNS topics and alarms.
- Terminate EC2 instances after testing.
- Monitor AWS billing.

## 🚀 Future Enhancements

- Create CloudWatch dashboards.
- Configure memory monitoring using CloudWatch Agent.
- Add multiple EC2 instances.
- Integrate incident notifications with AWS Lambda.
- Implement automated recovery actions.

## 👨‍💻 Author

**Bhushan Jagtap**

Aspiring AWS Cloud / DevOps Engineer

GitHub: https://github.com/Bhushan1814

LinkedIn: https://www.linkedin.com/in/bhushansjagtap

---

⭐ If you find this project useful, feel free to explore the repository and share your feedback!
