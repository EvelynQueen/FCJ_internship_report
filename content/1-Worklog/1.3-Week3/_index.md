---
title: "Week 3 Worklog"
date: "'r Sys.Date() '"
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

- Complete essential AWS hands-on labs (Site-to-Site VPN, EC2 basics).
- Advance through and finish all four modules of the AWS Cloud Technical Essentials course.
- Improve familiarity with AWS Console and CLI usage (setup, key handling, region/service exploration).
- Coordinate with product/design teams to review and document TypeRush Figma UI/UX for upcoming development.
- Assess storage solutions and finalize a scalable NoSQL direction for TextService data.
- Prototype and incorporate MongoDB (environment preparation, data seeding, service restructuring, validation).
- Establish consistent communication flow with members of the First Cloud Journey team.

### Tasks carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Start Date | Completion Date | Reference Material                                                                                                         |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | -------------------------------------------------------------------------------------------------------------------------- |
| 2   | - **Lab 03:** AWS Site-to-Site VPN: <br>&emsp; + Build a complete Site-to-Site VPN setup, including a fresh VPC, an EC2 instance acting as a customer gateway, a Virtual Private Gateway, and the VPN connection. <br>&emsp; + Configure and validate tunnel connectivity. <br><br> - **Lab 04:** Amazon EC2 Fundamentals: <br>&emsp; + Launch and access both Windows Server and Amazon Linux EC2 instances. <br>&emsp; + Deploy a sample “AWS User Management” application on each instance to practice basic CRUD tasks. <br>&emsp; + Explore core EC2 features such as resizing instance types, working with EBS snapshots, and generating custom AMIs.                                                                                                                                                                                                                                                              | 09/22/2025 | 09/22/2025      | VPN Lab (Lab 03): <br> <https://000003.awsstudygroup.com/> <br> EC2 Lab (Lab 04): <br> <https://000004.awsstudygroup.com/> |
| 3   | - Begin AWS Cloud Technical Essentials course, completing two modules: <br>&emsp; + **Module 1:** Cloud Foundations & IAM <br>&emsp;&emsp; - Explain cloud computing and its benefits. <br>&emsp;&emsp; - Compare cloud workloads with on-premises setups. <br>&emsp;&emsp; - Create an AWS account and review the different ways to interact with services. <br>&emsp;&emsp; - Describe the AWS Global Infrastructure (Regions, Availability Zones). <br>&emsp;&emsp; - Study and apply IAM best practices. <br>&emsp; + **Module 2:** Compute & Networking <br>&emsp;&emsp; - Understand EC2 architecture components. <br>&emsp;&emsp; - Distinguish between VMs and containers. <br>&emsp;&emsp; - Explore advantages of serverless technology. <br>&emsp;&emsp; - Learn foundational networking concepts and VPC features. <br>&emsp;&emsp; - Create a VPC.                                                          | 09/23/2025 | 09/23/2025      | AWS Cloud Technical Essentials: <br> <https://www.coursera.org/learn/aws-cloud-technical-essentials>                       |
| 4   | - Collaborate and Document TypeRush Figma UI/UX: <br>&emsp; + Join a cross-team design review to analyze the latest Figma layouts. <br>&emsp; + Break down each major screen (login/signup, gameplay UI, results summary, settings) to understand component hierarchy, interaction logic, and state variations. <br>&emsp; + Prepare initial questions regarding feasibility and implementation concerns for engineering. <br>&emsp; + Begin mapping key design elements into early front-end component requirements or user stories. <br><br> - Discuss TextService Storage Architecture with Team Lead & Validate NoSQL Decision: <br>&emsp; + Meet with team lead to evaluate the ideal storage approach for words/sentences. <br>&emsp; + Present comparison between SQL and NoSQL solutions based on structure and expected usage patterns. <br>&emsp; + Confirm choosing NoSQL due to flexibility and scalability. | 09/24/2025 | 09/24/2025      |                                                                                                                            |
| 5   | - Integrate and Validate MongoDB in TextService Prototype: <br>&emsp; + Set up MongoDB environment using Docker. <br>&emsp; + Update seeding script to insert words and sentences into MongoDB collections. <br>&emsp; + Revise service logic to retrieve data from MongoDB instead of the previous source. <br>&emsp; + Fully test the updated service to confirm successful read/write operations.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | 09/25/2025 | 09/25/2025      |                                                                                                                            |
| 6   | - Complete Modules 3 & 4 of AWS Cloud Technical Essentials: <br>&emsp; + **Module 3:** Storage & Databases <br>&emsp;&emsp; - Differentiate file, block, and object storage. <br>&emsp;&emsp; - Understand S3 concepts and create a bucket. <br>&emsp;&emsp; - Explain how Amazon EBS functions with EC2. <br>&emsp;&emsp; - Explore AWS database offerings. <br>&emsp;&emsp; - Learn DynamoDB basics and make a table. <br>&emsp; + **Module 4:** Monitoring & High Availability <br>&emsp;&emsp; - Understand monitoring benefits and CloudWatch usage. <br>&emsp;&emsp; - Optimize for cost/performance. <br>&emsp;&emsp; - Explain Elastic Load Balancing. <br>&emsp;&emsp; - Compare vertical vs horizontal scaling. <br>&emsp;&emsp; - Configure a highly available setup.                                                                                                                                         | 09/26/2025 | 09/26/2025      | AWS Cloud Technical Essentials: <br> <https://www.coursera.org/learn/aws-cloud-technical-essentials>                       |

### Week 3 Achievements:

- AWS Infrastructure Labs:

  - Built a complete Site-to-Site VPN (VPC, customer-gateway EC2, virtual private gateway, tunnel testing)
  - Completed EC2 fundamentals (Windows/Linux instances, CRUD demo deployment, snapshots, custom AMIs)

- Completed the entire AWS Cloud Technical Essentials course (Foundations/IAM, Compute/Networking, Storage/Databases, Monitoring/HA)

- AWS Console & CLI Proficiency:

  - Account setup, credentials/config organization
  - Region/service navigation
  - Key pair management and resource review

- TypeRush UI/UX Documentation:

  - Reviewed major Figma screens and flows
  - Recorded component states and feasibility considerations
  - Drafted initial component requirements/user stories

- TextService Storage Architecture:

  - Compared SQL vs NoSQL for storing text-based data
  - Selected NoSQL for improved flexibility and scalability

- MongoDB Integration Prototype:
  - Created Docker-based MongoDB environment
  - Updated seeding script to store documents
  - Refactored service to query MongoDB
  - Verified full read/write data flow
