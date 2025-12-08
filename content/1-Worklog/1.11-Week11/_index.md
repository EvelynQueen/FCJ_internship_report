---
title: "Week 11 Worklog"
date: "`r Sys.Date()`"
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

- Participate in an AWS community session to explore advanced cloud features and recommended practices.
- Construct a serverless text-processing service using DynamoDB schema design and IAM role configuration.
- Implement database lookup functions supporting pagination and conditional filters.
- Build an in-memory cache system and validate API request inputs.
- Integrate Amazon Bedrock Agent to produce AI-generated paragraph content.
- Set up monitoring and debugging utilities for serverless environments.
- Create GraphQL APIs through AWS AppSync with DynamoDB-based resolvers.

### Tasks carried out this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Start Date | Completion Date | Reference Material                                                                                                                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| 2   | - **Joined the “AWS Cloud Mastery Series #2” workshop**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | 11/17/2025 | 11/17/2025      |
| 3   | - **Set up AWS serverless foundation for text service:** <br>&emsp; + Created DynamoDB table `wordsntexts` using a string partition key for storing word and paragraph data <br>&emsp; + Configured IAM role permissions for `dynamodb:Scan`, `dynamodb:Query`, and CloudWatch log access <br>&emsp; + Built the initial Lambda handler and established `boto3` client instances for DB operations <br><br> - **Developed database retrieval routines:** <br>&emsp; + Implemented `fetch_words_from_db` utilizing scan operations with `LastEvaluatedKey` to manage pagination <br>&emsp; + Implemented `fetch_paragraph_from_db` with filter expressions based on content classification and length fields                                                                                                                                                                                                                                | 11/18/2025 | 11/18/2025      |
| 4   | - **Added caching and data-processing logic:** <br>&emsp; + Created an in-memory global cache dictionary with 300-second TTL to lower scan frequency <br>&emsp; + Built `get_random_words` to serve data from cache or DynamoDB with randomized selection <br>&emsp; + Built `get_paragraph` to enforce valid length ranges (1–3) and convert content strings into word arrays <br><br> - **Implemented API validation and response shaping:** <br>&emsp; + Added a custom `Decimal_encoder` class for JSON-safe serialization of DynamoDB numerics <br>&emsp; + Added validation for query params `type` and `count`, handling `TypeError` and `ValueError` cases <br>&emsp; + Unified JSON responses with consistent HTTP status codes and headers                                                                                                                                                                                       | 11/19/2025 | 11/19/2025      |
| 5   | - **Integrated Amazon Bedrock Agent for generative features:** <br>&emsp; + Expanded IAM policies to include `bedrock:InvokeAgent` and linked Agent ID `HUEBUXSALX` <br>&emsp; + Initialized the `bedrock-agent-runtime` client and implemented `invoke_agent` with session tracking <br>&emsp; + Added logic for processing streamed payloads and reassembling decoded byte fragments <br><br> - **Performed prompt engineering and model testing:** <br>&emsp; + Crafted prompts ensuring the Agent outputs exactly three paragraphs separated by blank lines <br>&emsp; + Evaluated several backend models to maintain predictable formatting for downstream splitting <br>&emsp; + Implemented parsing logic to segment the generated text                                                                                                                                                                                             | 11/20/2025 | 11/20/2025      |
| 6   | - **Monitoring and debugging serverless workloads via CloudWatch and X-Ray** <br>&emsp; + Reviewed CloudWatch Lambda logs to detect and address runtime issues <br>&emsp; + Created tailored metrics to capture application-specific performance indicators <br>&emsp; + Set up CloudWatch Alarms to notify on critical thresholds <br>&emsp; + Enabled AWS X-Ray tracing to study service paths and recognize latency hotspots <br><br> - **Constructing GraphQL APIs through AWS AppSync and DynamoDB resolvers** <br>&emsp; + Prepared AppSync project and connected DynamoDB as the primary datasource <br>&emsp; + Implemented resolvers for Create and Read operations for single items <br>&emsp; + Added Update and Delete resolvers to manage lifecycle modifications <br>&emsp; + Executed Query and Scan operations for bulk data interactions <br>&emsp; + Built multi-layered resolvers for nested or complex data structures | 11/21/2025 | 11/21/2025      | CloudWatch and X-Ray Monitoring: <br> <https://000085.awsstudygroup.com/> <br> AppSync GraphQL APIs: <br> <https://000086.awsstudygroup.com/> |

### Week 11 Achievements:

- Took part in the “AWS Cloud Mastery Series #2” program to deepen understanding of advanced AWS features.

- Built serverless infrastructure for a typing-practice text generation service:

  - Designed DynamoDB table `wordsntexts` using a string partition key to store roughly 64,726 word/paragraph entries.
  - Set up IAM execution role to enable DynamoDB Scan/Query actions and CloudWatch logging.
  - Configured a Lambda function (128 MB RAM, 15-second timeout) with active `boto3` DB connection objects.

- Implemented database interaction modules:

  - Produced `fetch_words_from_db` with Scan + `LastEvaluatedKey`-based pagination.
  - Created `fetch_paragraph_from_db` with filter expressions for length categories (short: 10–25, medium: 25–60, long: 60+ words).

- Improved performance and request processing:

  - Deployed an in-memory TTL (300 seconds) caching system to reduce scan load for an expected ~500 requests/hour.
  - Added `get_random_words` and `get_paragraph` using random sampling and controlled length bounds (1–3).
  - Introduced the `Decimal_encoder` to serialize DynamoDB numbers reliably.
  - Implemented strict validation for `type` and `count` parameters to avoid errors.
  - Standardized API responses with consistent status codes and headers.

- Integrated Amazon Bedrock Agent for generating paragraphs:

  - Updated IAM rules to include `bedrock:InvokeAgent` and linked Agent ID `HUEBUXSALX`.
  - Configured `bedrock-agent-runtime` invocation with session handling.
  - Created logic for reconstructing streamed byte responses.
  - Built structured prompts ensuring production of three separated paragraphs for future challenge features.
  - Added text-splitting logic for safe post-processing.

- Configured monitoring and diagnostics for serverless systems:

  - Reviewed CloudWatch logs for error tracing.
  - Added custom metrics for application performance tracking.
  - Set CloudWatch alarms on critical thresholds (latency, error rate).
  - Enabled X-Ray to visualize service map and bottlenecks.

- Developed AWS AppSync GraphQL APIs:
  - Prepared environment and linked DynamoDB as datasource.
  - Created CRUD resolvers (Create/Read/Update/Delete).
  - Added Scan and Query resolvers for large-scale lookups.
  - Designed complex nested resolvers for structured datasets.
