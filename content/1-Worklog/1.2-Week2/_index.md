---
title: "Week 2 Worklog"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

- Clarify and outline the scope for the first typing-game project (essential features, microservice boundaries, and future matchmaking direction).
- Build team foundations: shared repository, starter backlog, ER modeling, selected technologies, and ownership of services.
- Finalize standardized formulas for WPM and accuracy.
- Develop an initial FastAPI microservice covering text generation, sentence creation, and chat; map out pathway for Bedrock integration.
- Configure AWS Budgets with alert notifications.
- Strengthen technical competency in: Lambda (function URL), VPC networking (subnets, gateways, connectivity), Flow Logs, and load balancing basics.
- Deploy Amazon RDS; design database schema and seed text-related datasets.
- Rebuild the text service to retrieve content from the database; measure performance against the earlier API-based method.
- Begin implementing early operational practices: clear roles, benchmarking routines, and considerations for future scalability.

### Tasks carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Start Date | Completion Date | Reference Material                                                                                                                                                                                                                                            |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - Conduct a team ideation session to outline and rank feature ideas for the main project <br>&emsp; + Move brainstorming notes from the project canvas into a structured task backlog <br>&emsp; + Research and document formulas for measuring WPM and accuracy to maintain consistency <br>&emsp; + Create the shared code repository and establish baseline folder structures for each microservice and language <br>&emsp; + Refine earlier ER diagrams and begin drafting preliminary database schemas <br>&emsp; + Formally assign ownership of each microservice to specific team members <br>                                                                                                                                                                                        | 09/15/2025 | 09/15/2025      |                                                                                                                                                                                                                                                               |
| 3   | - Configure AWS Budgets: <br>&emsp; + Review categories (Cost, Usage, RI, etc.) <br>&emsp; + Define the budget threshold for monthly cost <br>&emsp; + Set up the budget inside the AWS console <br>&emsp; + Enable SNS/email notifications <br/> - Build a small web application using AWS Lambda: <br>&emsp; + Learn essential Lambda and function URL concepts <br>&emsp; + Implement a simple “Hello World” function <br>&emsp; + Configure required IAM permissions <br>&emsp; + Activate and test the function URL endpoint <br/> - Explore FastAPI for microservices: <br>&emsp; + Follow FastAPI’s official tutorial <br>&emsp; + Prepare a local development setup <br>&emsp; + Build a proof-of-concept service <br>&emsp; + Implement initial endpoints and test using Swagger UI | 09/16/2025 | 09/16/2025      | AWS Lambda:<br/> <https://ap-southeast-1.console.aws.amazon.com/lambda> <br/> AWS Budgets:<br/> <https://us-east-1.console.aws.amazon.com/costmanagement/> <br/> FastAPI:<br/> <https://www.coursera.org/learn/packt-mastering-rest-apis-with-fastapi-1xeea/> |
| 4   | - Study key AWS networking and security concepts <br>&emsp; + Understand what an Amazon VPC is and how it isolates resources <br>&emsp; + Learn the function of public vs private subnets <br>&emsp; + Explore Internet Gateway and NAT Gateway roles <br>&emsp; + Use VPC Flow Logs to troubleshoot network activity <br>&emsp; + Compare connectivity methods: Site-to-Site VPN vs Direct Connect <br>&emsp; + Understand when to use VPC Peering vs Transit Gateway <br>&emsp; + Review Elastic Load Balancing as a method to distribute traffic across servers <br>                                                                                                                                                                                                                      | 09/17/2025 | 09/17/2025      | Module 02-(01 to 03): <br> <https://www.youtube.com/watch?v=O9Ac_vGHquM> <br> <https://www.youtube.com/watch?v=BPuD1l2hEQ4> <br> <https://www.youtube.com/watch?v=CXU8D3kyxIc>                                                                                |
| 5   | - Work with the Amazon Bedrock playground: <br>&emsp; + Review available foundation models (Claude, Titan, etc.) <br>&emsp; + Choose a model for text generation tasks <br>&emsp; + Test prompts and adjust parameters <br>&emsp; + Produce and analyze a sample output <br/> - Develop the designated microservice prototype: <br>&emsp; + Build internal logic and integrate multiple APIs for text generation <br>&emsp; + Create the main functions for random sentence generation and chat handling <br>&emsp; + Review early implementation to spot limitations and plan next iterations <br>&emsp; + Validate the technical approach <br>                                                                                                                                             | 09/18/2025 | 09/18/2025      | Amazon Bedrock:<br/><https://ap-southeast-1.console.aws.amazon.com/bedrock>                                                                                                                                                                                   |
| 6   | - Deploy and configure Amazon RDS: <br>&emsp; + Select a database engine appropriate for the project <br>&emsp; + Set core instance settings (credentials, VPC, security groups) <br>&emsp; + Launch the instance, track status, and store the endpoint securely <br/> - Build a database-backed TextService prototype: <br>&emsp; + Design a minimal schema for storing words and sentences <br>&emsp; + Write a one-time script to populate the RDS instance with initial data <br>&emsp; + Rework the TextService to use database queries rather than external APIs <br>&emsp; + Benchmark performance against the previous API-based approach <br>                                                                                                                                       | 09/19/2025 | 09/19/2025      | Aurora and RDS:<br/><https://ap-southeast-1.console.aws.amazon.com/rds>                                                                                                                                                                                       |

### Week 2 Achievements:

- Completed definition of the first typing-game scope:

  - Essential features
  - Microservice boundaries
  - Seeded backlog
  - Ownership distribution

- Documented standardized WPM and accuracy formulas.
- Initialized shared repository with baseline multi-language layout.
- Refined ER diagrams and drafted first relational schema.
- Delivered FastAPI prototype (generation, sentence assembly, chat) and validated using Swagger UI.
- Finished AWS Budgets setup with alerts.
- Strengthened AWS foundations:
  - Lambda (function URLs)
  - VPC (subnets, IGW, NAT, Flow Logs)
  - Peering vs transit gateway
  - Load balancing basics
- Explored Bedrock models; selected candidate model and validated prompting approach.
- Launched RDS instance, built schema, and loaded seed data.
- Refactored TextService to database-backed retrieval and performed initial benchmarks.
- Implemented early operational routines: service ownership, performance focus, and scalability planning.
