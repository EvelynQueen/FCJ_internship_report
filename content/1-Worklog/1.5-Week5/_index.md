---
title: "Week 5 Worklog"
date: "`r Sys.Date()`"
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

- Implement enhanced AWS networking using VPC Peering and Transit Gateway to support communication across multiple VPCs.
- Deploy end-to-end applications with EC2, RDS, Auto Scaling, and CloudFront for optimized delivery.
- Build serverless cost-control automation using AWS Lambda to manage EC2 instance schedules.
- Create CI/CD pipelines with AWS Developer Tools to streamline application deployment.
- Configure hybrid storage environments through AWS Storage Gateway for on-premises integration.
- Operate enterprise-level file systems using Amazon FSx and enhance application protection with AWS WAF.
- Use Tags and Resource Groups for organized governance across AWS resources.
- Strengthen skills in both the AWS Console and CLI for operational tasks.

### Tasks carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Start Date | Completion Date | Reference Material                                                                                                            |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| 2   | - **Configure VPC Peering between two VPCs:** <br>&emsp; + Initialize a CloudFormation Template to set up the base infrastructure <br>&emsp; + Build Security Groups to regulate EC2 traffic <br>&emsp; + Launch EC2 instances in each VPC for connectivity checks <br>&emsp; + Adjust Network ACLs to permit traffic between VPCs <br>&emsp; + Initiate and approve the VPC Peering request <br>&emsp; + Modify Route Tables to forward traffic between peered VPCs <br>&emsp; + Turn on Cross-Peer DNS to allow inter-VPC name resolution <br><br> - **Establish a scalable network design using AWS Transit Gateway:** <br>&emsp; + Generate a Key Pair for secure instance connections <br>&emsp; + Deploy environment resources through a CloudFormation Template <br>&emsp; + Create a Transit Gateway to serve as the central routing hub <br>&emsp; + Attach multiple VPCs to the Transit Gateway for communication <br>&emsp; + Configure Transit Gateway route entries to manage traffic paths <br>&emsp; + Update VPC Route Tables to direct traffic via the Transit Gateway       | 10/06/2025 | 10/06/2025      | VPC Peering: <br> <https://000019.awsstudygroup.com/> <br> Transit Gateway: <br> <https://000020.awsstudygroup.com/>          |
| 3   | - **Deploy WordPress on AWS Cloud:** <br>&emsp; + Prepare VPC and Subnets for network layout <br>&emsp; + Configure Security Groups for EC2 and RDS access control <br>&emsp; + Launch an EC2 instance to host the WordPress site <br>&emsp; + Deploy an RDS instance for the WordPress database <br>&emsp; + Install and set up WordPress on the EC2 server <br>&emsp; + Implement Auto Scaling to ensure availability <br>&emsp; + Perform backup and restore tasks on the RDS database <br>&emsp; + Enable CloudFront to enhance delivery and security <br><br> - **Reduce EC2 costs using Lambda automation:** <br>&emsp; + Add identification tags to EC2 instances for cost-saving automation <br>&emsp; + Create an IAM Role granting permissions to Lambda <br>&emsp; + Build a Lambda function to automatically start/stop EC2 instances <br>&emsp; + Validate the Lambda workflow for correctness                                                                                                                                                                                   | 10/07/2025 | 10/07/2025      | WordPress on AWS: <br> <https://000021.awsstudygroup.com/> <br> Lambda Optimization: <br> <https://000022.awsstudygroup.com/> |
| 4   | - **Automate deployment with a CI/CD Pipeline:** <br>&emsp; + Prepare resources required for the pipeline <br>&emsp; + Install and enable the CodeDeploy Agent on EC2 servers <br>&emsp; + Create a CodeCommit repository for application source code <br>&emsp; + Configure CodeBuild to compile and build the app <br>&emsp; + Set up CodeDeploy for automated rollout <br>&emsp; + Assemble a CodePipeline to coordinate the entire workflow <br>&emsp; + Resolve any pipeline execution issues <br><br> - **Use AWS Storage Gateway for hybrid cloud storage:** <br>&emsp; + Create an S3 Bucket for cloud-based storage <br>&emsp; + Launch an EC2 instance to host the Storage Gateway <br>&emsp; + Deploy a Storage Gateway to connect on-premises workloads with AWS <br>&emsp; + Configure File Shares for file-level access <br>&emsp; + Mount File Shares on an on-prem machine for direct access                                                                                                                                                                                  | 10/08/2025 | 10/08/2025      | CodePipeline: <br> <https://000023.awsstudygroup.com/> <br> Storage Gateway: <br> <https://000024.awsstudygroup.com/>         |
| 5   | - **Administer Amazon FSx for Windows File Server:** <br>&emsp; + Deploy the initial environment <br>&emsp; + Create both SSD and HDD Multi-AZ file systems <br>&emsp; + Set up new file shares on each file system <br>&emsp; + Evaluate performance and gather monitoring data <br>&emsp; + Enable deduplication and shadow copies for optimization and recovery <br>&emsp; + Manage sessions, open files, and user quotas <br>&emsp; + Enable Continuous Access for improved reliability <br>&emsp; + Scale throughput and storage based on needs <br>&emsp; + Remove the environment after testing <br>&emsp; + Apply AWS CLI commands to manage the file system <br><br> - **Set up AWS Web Application Firewall (WAF):** <br>&emsp; + Create an S3 Bucket and deploy a sample application <br>&emsp; + Enable AWS WAF using managed rules for threat protection <br>&emsp; + Add custom and advanced rules tailored to requirements <br>&emsp; + Test new rules for accuracy <br>&emsp; + Log and analyze incoming requests <br>&emsp; + Clean up resources to prevent additional costs | 10/09/2025 | 10/09/2025      | Amazon FSx: <br> <https://000025.awsstudygroup.com/> <br> AWS WAF: <br> <https://000026.awsstudygroup.com/>                   |
| 6   | - **Organize AWS resources with Tags and Resource Groups:** <br>&emsp; + Understand tag usage through the AWS Console <br>&emsp; + Launch an EC2 instance with tags attached <br>&emsp; + Add or remove tags on existing resources <br>&emsp; + Use tags to filter resources efficiently <br>&emsp; + Apply tags using the AWS CLI <br>&emsp; + Tag an existing EC2 instance via CLI <br>&emsp; + Add tags during resource creation with CLI <br>&emsp; + Describe tagged resources using CLI commands <br>&emsp; + Create and maintain a Resource Group for better organization <br>&emsp; + Build a tag-based Resource Group <br>&emsp; + View and manage all resources under the group                                                                                                                                                                                                                                                                                                                                                                                                     | 10/10/2025 | 10/10/2025      | Tags & Resource Groups: <br> <https://000027.awsstudygroup.com/>                                                              |

### Week 5 Achievements:

- Completed advanced networking implementations:

  - VPC Peering enabling direct communication between VPCs
  - Transit Gateway operating as a central routing hub
  - Configured routing and DNS across VPC boundaries

- Deployed and refined cloud-based full-stack applications:

  - WordPress with integrated RDS backend
  - Auto Scaling and CloudFront improving resiliency and speed
  - Lambda-driven serverless cost optimization

- Developed DevOps automation pipelines:

  - Full CI/CD automation with AWS Developer Tools
  - Deployment orchestration through CodePipeline
  - Hybrid storage integration via Storage Gateway

- Set up enterprise-grade storage and security tooling:

  - Amazon FSx Multi-AZ file systems with performance optimization
  - AWS WAF with custom security rules and thorough testing
  - Monitoring and tuning for efficiency

- Adopted structured AWS resource governance:

  - Tag strategies supporting cost and organization tracking
  - Resource Groups for consolidated management
  - Fluent usage of AWS Console and CLI

- Strengthened IaC capabilities through CloudFormation for consistent provisioning.
