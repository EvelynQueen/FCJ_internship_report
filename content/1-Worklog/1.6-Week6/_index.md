---
title: "Week 6 Worklog"
date: "`r Sys.Date()`"
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

- Gain skills in managing EC2 access using IAM with tag-based controls and permission boundaries.
- Set up and configure monitoring solutions such as Grafana and AWS CloudWatch.
- Utilize AWS Systems Manager for patch automation and remote command execution.
- Improve EC2 efficiency through right-sizing methods and AWS Compute Optimizer insights.
- Apply S3 data encryption with AWS KMS and configure audit logging tools.
- Review AWS cost trends and usage insights using Cost Explorer.
- Build a data pipeline and data lake with S3, Kinesis, Glue, Athena, and QuickSight.
- Use AWS CloudFormation to automate infrastructure creation.

### Tasks carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Start Date | Completion Date | Reference Material                                                                                                                   |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| 2   | - **Control EC2 access using IAM with resource tags:** <br>&emsp; + Set up an IAM user for initial preparation <br>&emsp; + Create a custom IAM Policy to define access rules <br>&emsp; + Build an IAM Role for users or services to assume <br>&emsp; + Validate the policy by switching roles and checking access <br><br> - **Introduction to basic Grafana setup:** <br>&emsp; + Create a VPC and subnet for the environment <br>&emsp; + Configure a Security Group for traffic filtering <br>&emsp; + Launch an EC2 instance to host Grafana <br>&emsp; + Create an IAM User and Role for AWS resource access <br>&emsp; + Attach the IAM Role to the EC2 instance <br>&emsp; + Install Grafana on EC2 <br>&emsp; + Build initial dashboards in Grafana                                       | 10/13/2025 | 10/13/2025      | IAM services: <br> <https://000028.awsstudygroup.com/> <br> Grafana basic: <br> <https://000029.awsstudygroup.com/>                  |
| 3   | - **Limit user permissions using IAM Permission Boundaries:** <br>&emsp; + Complete initial preparation steps <br>&emsp; + Create a boundary policy defining the maximum permissions allowed <br>&emsp; + Add a new IAM user with controlled access <br>&emsp; + Verify limits by testing the user's permissions <br><br> - **Patch management and remote execution using AWS Systems Manager:** <br>&emsp; + Set up a VPC and subnet <br>&emsp; + Launch a public Windows EC2 instance <br>&emsp; + Create and assign an IAM Role for Systems Manager <br>&emsp; + Configure Patch Manager for automated patching <br>&emsp; + Use Run Command to execute remote actions                                                                                                                            | 10/14/2025 | 10/14/2025      | IAM permission boundary: <br> <https://000030.awsstudygroup.com/> <br> AWS Systems Manager: <br> <https://000031.awsstudygroup.com/> |
| 4   | - **Apply EC2 right-sizing practices:** <br>&emsp; + Explore CloudWatch monitoring features <br>&emsp; + Create and attach an IAM Role for CloudWatch Agent <br>&emsp; + Install the CloudWatch Agent on an EC2 instance <br>&emsp; + Use AWS Compute Optimizer for EC2 improvement suggestions <br><br> - **Encrypt S3 data with AWS KMS:** <br>&emsp; + Set up the necessary IAM users, groups, roles, and policies <br>&emsp; + Create a KMS key <br>&emsp; + Build an S3 bucket and upload data <br>&emsp; + Configure AWS CloudTrail and Athena for logging analysis <br>&emsp; + Test and share encrypted S3 data                                                                                                                                                                              | 10/15/2025 | 10/15/2025      | EC2 right-sizing: <br> <https://000032.awsstudygroup.com/> <br> S3 encryption with KMS: <br> <https://000033.awsstudygroup.com/>     |
| 5   | - **Analyze AWS spending with Cost Explorer:** <br>&emsp; + View cost breakdowns by account and service <br>&emsp; + Review Savings Plans and Reserved Instance coverage <br>&emsp; + Evaluate cost elasticity patterns <br>&emsp; + Generate EC2-specific cost reports <br>&emsp; + Use Cost Explorer for detailed financial analysis <br>&emsp; + Check data transfer costs for typical architectures <br><br> - **Develop a data lake on AWS:** <br>&emsp; + Create IAM Role and Policy for permissions <br>&emsp; + Set up an S3 bucket for storage <br>&emsp; + Build a Kinesis Data Firehose stream for ingestion <br>&emsp; + Use Glue Crawler to catalog data <br>&emsp; + Perform transformations <br>&emsp; + Use Athena for data queries <br>&emsp; + Create visualizations in QuickSight | 10/16/2025 | 10/17/2025      | AWS Cost Explorer: <br> <https://000034.awsstudygroup.com/> <br> Data lake on AWS: <br> <https://000035.awsstudygroup.com/>          |
| 6   | - **Study AWS CloudWatch monitoring tools:** <br>&emsp; + Explore CloudWatch Metrics and expressions <br>&emsp; + Work with Logs, Logs Insights, and Metric Filters <br>&emsp; + Configure CloudWatch Alarms for notifications <br>&emsp; + Create CloudWatch Dashboards <br><br> - **Automate infrastructure using CloudFormation:** <br>&emsp; + Prepare IAM Users and Roles <br>&emsp; + Create a basic CloudFormation template for provisioning <br>&emsp; + Try advanced features such as Lambda-backed Custom Resources <br>&emsp; + Use Mappings, StackSets, and Drift Detection for complex deployments                                                                                                                                                                                      | 10/17/2025 | 10/17/2025      | AWS CloudWatch: <br> <https://000036.awsstudygroup.com/> <br> AWS CloudFormation: <br> <https://000037.awsstudygroup.com/>           |

### Week 6 Achievements:

- Efficiently configured EC2 access management with IAM:

  - Used tag-based access controls
  - Applied permission boundaries for restricted privileges

- Deployed monitoring and observability solutions:

  - Installed and configured Grafana dashboards
  - Set up CloudWatch metrics, logs, and alarms

- Utilized AWS Systems Manager features:

  - Automated patching with Patch Manager
  - Executed commands remotely with Run Command

- Enhanced EC2 performance and cost efficiency:

  - Configured CloudWatch Agent for detailed metrics
  - Used Compute Optimizer for EC2 improvements
  - Analyzed cost patterns with Cost Explorer

- Secured stored data with encryption:

  - Managed KMS keys for S3 encryption
  - Enabled CloudTrail and Athena for auditing

- Built a complete data lake architecture:

  - Configured Kinesis ingestion and Glue data catalog
  - Queried data with Athena and visualized results using QuickSight

- Automated resource deployment via CloudFormation:
  - Created templates for provisioning
  - Utilized advanced CloudFormation capabilities including Custom Resources and StackSets
