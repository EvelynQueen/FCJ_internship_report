---
title: "Week 4 Worklog"
date: "'r Sys.Date() '"
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

- Gain practical experience configuring Amazon RDS, including VPC networking, security controls, and backup procedures.
- Learn how to deploy scalable applications using Auto Scaling Groups paired with Application Load Balancers.
- Improve understanding of monitoring best practices through CloudWatch metrics, logs, alarms, and dashboards.
- Study enterprise-grade hybrid DNS architectures using Route 53 Resolver.
- Strengthen AWS CLI command usage for automated operations across S3, EC2, IAM, and VPC.
- Build CI/CD pipelines using AWS development tools such as CodeCommit, CodeBuild, CodeDeploy, and CodePipeline.
- Implement automated backup workflows with AWS Backup and lifecycle rules.
- Practice deploying containerized applications with Docker, including registry usage and AWS integration.
- Explore VM migration workflows involving VM import/export between on-premises and AWS.
- Develop serverless solutions using AWS Lambda and API Gateway with proper IAM integration.
- Learn how to consolidate and analyze security findings using AWS Security Hub with cross-service data.

### Tasks carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Start Date | Completion Date | Reference Material                                                                                                                                                                       |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - **Relational Database Management with Amazon RDS:** <br>&emsp; + Build a VPC, configure security groups for both EC2 and RDS, and prepare a DB subnet group. <br>&emsp; + Launch an EC2 instance and create an RDS database instance. <br>&emsp; + Deploy a sample app on EC2 and connect it to the RDS database. <br>&emsp; + Execute backup and restore processes for the RDS instance. <br>&emsp; + Remove all created resources during cleanup. <br><br> - **Deploying a Scalable Web Application using Auto Scaling:** <br>&emsp; + Build the required networking components (VPC, subnets, and security groups). <br>&emsp; + Prepare an EC2 Launch Template for standardized instance provisioning. <br>&emsp; + Configure a Target Group and ALB to distribute traffic. <br>&emsp; + Create and manage an Auto Scaling Group with multiple scaling policies. <br>&emsp; + Cleanup all AWS resources after testing. <br><br> - **Monitoring AWS Resources using CloudWatch:** <br>&emsp; + Review various AWS service metrics using search and math expressions. <br>&emsp; + Use CloudWatch Logs Insights to analyze log data. <br>&emsp; + Build a Metric Filter to extract relevant information. <br>&emsp; + Configure CloudWatch Alarms with threshold-based triggers. <br>&emsp; + Construct a customized dashboard for visual monitoring. <br>&emsp; + Remove all monitoring resources after completion. | 29/09/2025 | 29/09/2025      | Amazon RDS: <br> <https://000005.awsstudygroup.com/> <br> Auto Scaling Group: <br> <https://000006.awsstudygroup.com/> <br> CloudWatch Metrics: <br> <https://000008.awsstudygroup.com/> |
| 3   | - **Hybrid DNS with Route 53 Resolver:** <br>&emsp; + Deploy base infrastructure using a CloudFormation template. <br>&emsp; + Launch a Microsoft Active Directory server to mimic on-prem DNS. <br>&emsp; + Create a Route 53 Resolver outbound endpoint to forward VPC DNS queries. <br>&emsp; + Set Resolver rules to direct traffic to correct DNS endpoints. <br>&emsp; + Build an inbound endpoint for on-prem to query VPC resources. <br>&emsp; + Test cross-environment DNS resolution and clean up afterward. <br><br> - **Managing AWS Resources with the CLI:** <br>&emsp; + Install and configure AWS CLI with credentials and region. <br>&emsp; + Use CLI commands to inspect and view services such as S3, SNS, and IAM. <br>&emsp; + Perform S3 bucket and object operations from the command line. <br>&emsp; + Build core VPC components (Internet Gateway, etc.) via CLI. <br>&emsp; + Launch, inspect, and terminate EC2 instances using CLI only. <br>&emsp; + Clean up all CLI-created resources.                                                                                                                                                                                                                                                                                                                                                                                                 | 30/09/2025 | 30/09/2025      | Route 53 Resolver: <br> <https://cloudjourney.awsstudygroup.com/> <br> AWS CLI: <br> <https://000011.awsstudygroup.com/>                                                                 |
| 4   | - **CI/CD Pipeline Automation:** <br>&emsp; + Set up a CodeCommit repository for application source code. <br>&emsp; + Configure a CodeBuild project for compiling, testing, and packaging. <br>&emsp; + Prepare CodeDeploy configurations and deployment groups. <br>&emsp; + Create a full CI/CD workflow using CodePipeline. <br>&emsp; + Test full automation by pushing updates and validating deployment. <br>&emsp; + Clean up all pipeline resources. <br><br> - **Automated EC2 Backups using AWS Backup:** <br>&emsp; + Deploy infrastructure using a CloudFormation stack. <br>&emsp; + Configure a backup plan with lifecycle and retention. <br>&emsp; + Enable notifications for backup status. <br>&emsp; + Test backup and restoration workflows. <br>&emsp; + Delete all resources including backups and CloudFormation stacks.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | 01/10/2025 | 01/10/2025      | AWS IAM Identity Center: <br> <https://000012.awsstudygroup.com/> <br> AWS Backup: <br> <https://000013.awsstudygroup.com/>                                                              |
| 5   | - **Deploy Docker Applications on AWS:** <br>&emsp; + Configure VPC, IAM roles, and required infrastructure. <br>&emsp; + Launch an RDS instance for application data. <br>&emsp; + Prepare an EC2 instance with Docker dependencies. <br>&emsp; + Deploy and test the application using Docker. <br>&emsp; + Redeploy the solution using Docker Compose for multi-container setups. <br>&emsp; + Push the Docker image to ECR or Docker Hub. <br>&emsp; + Clean up infrastructure afterward. <br><br> - **VM Migration to/from AWS:** <br>&emsp; + Export an on-prem VM environment. <br>&emsp; + Upload the VM image to S3. <br>&emsp; + Import the VM into AWS to produce a new AMI. <br>&emsp; + Launch EC2 instances based on the imported AMI. <br>&emsp; + Export EC2 VMs back to S3. <br>&emsp; + Remove created resources after completion.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | 02/10/2025 | 02/10/2025      | Docker on AWS: <br> <https://000015.awsstudygroup.com/> <br> VM Import/Export: <br> <https://000014.awsstudygroup.com/>                                                                  |
| 6   | - **Serverless Deployment using Lambda and API Gateway:** <br>&emsp; + Prepare Lambda deployment package with all necessary dependencies. <br>&emsp; + Create an IAM execution role with proper trust relationships. <br>&emsp; + Deploy the Lambda function and configure runtime settings. <br>&emsp; + Build an HTTP API with API Gateway to invoke Lambda. <br>&emsp; + Deploy and test the API using the public endpoint. <br>&emsp; + Remove Lambda, API Gateway, and IAM resources afterward. <br><br> - **Security Monitoring with AWS Security Hub:** <br>&emsp; + Activate Security Hub to aggregate insights from multiple security services. <br>&emsp; + Review dashboards to view alerts and findings. <br>&emsp; + Prioritize detections across GuardDuty, Inspector, and Macie. <br>&emsp; + Examine summarized security insights through charts and tables.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 03/10/2025 | 03/10/2025      | AWS Lambda: <br> <https://000016.awsstudygroup.com/> <br> AWS Security Hub: <br> <https://000018.awsstudygroup.com/>                                                                     |

### Week 4 Achievements:

- Completed end-to-end Amazon RDS configuration and management:

  - VPC networking and security setup
  - Subnet grouping and EC2-RDS connectivity
  - Application deployment with database integration
  - Backup and restoration workflows

- Successfully deployed scalable architecture with Auto Scaling:

  - Full networking design (VPC, subnets, SGs)
  - EC2 Launch Template standardization
  - ALB + Target Group traffic routing
  - Auto Scaling Group with multiple scaling policies

- Built multi-layer AWS monitoring systems with CloudWatch:

  - Metric exploration using advanced expressions
  - Log Insights for log querying
  - Alarm setups with thresholds
  - Custom dashboard creation

- Designed hybrid DNS infrastructure with Route 53 Resolver:

  - CloudFormation-based environment provisioning
  - Active Directory integration
  - Outbound/inbound endpoint configuration
  - Bidirectional name resolution validation

- Improved AWS CLI automation skills:

  - CLI configuration with credentials
  - Resource management across S3, SNS, IAM
  - S3 bucket/object operations
  - Full EC2 lifecycle management via CLI

- Developed CI/CD pipelines with AWS developer tools:

  - Git repository setup using CodeCommit
  - Build automation with CodeBuild
  - Deployment orchestration using CodeDeploy
  - Full pipeline coordination with CodePipeline

- Applied automated backup strategies with AWS Backup:

  - CloudFormation infrastructure deployment
  - Backup plan with lifecycle policies
  - Notification setup
  - Disaster recovery verification

- Deployed containerized apps using Docker:

  - AWS infrastructure configuration
  - RDS-backed application setup
  - Docker and Docker Compose deployment
  - Image push to ECR

- Executed VM migration processes:

  - On-prem VM export
  - S3-based VM transfer
  - AMI creation through import
  - EC2 deployment from imported images

- Built serverless applications with Lambda + API Gateway:

  - Lambda packaging and execution role creation
  - Function setup and API integration
  - Public endpoint testing

- Enabled organization-wide security monitoring through Security Hub:
  - Multi-service alert aggregation
  - Dashboard usage for security review
  - Prioritization of findings across GuardDuty, Inspector, Macie
  - Summary-based risk evaluation
