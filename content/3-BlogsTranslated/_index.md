---
title: "Translated Blogs"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

#### Blog I have translated:

### [Blog 1 - How Anuttacon scaled AI-enhanced gaming workloads for “Whispers from the Star”](3.1-Blog1/)

This blog explains how Anuttacon successfully implemented a scalable architecture for their AI-enhanced game “Whispers from the Star.” It covers the challenges of unpredictable traffic spikes, GPU capacity constraints, and multi-region scaling. The architecture uses stateless services, regional EKS clusters, a global manager, and optimizations for inference cold start using custom Bottlerocket AMIs, Amazon EBS Provisioned Rate for Volume Initialization, and Amazon EFS. The post provides key best practices for modern gaming workloads, including stateless design, storage optimization, and cross-region resource balancing.

### [Blog 2 - Effectively building AI agents on AWS Serverless](3.2-Blog2/)

This blog introduces agentic AI and explains how to build production-ready serverless AI agents using AWS services such as Amazon Bedrock AgentCore, AWS Lambda, and Amazon ECS. It highlights how agentic AI differs from traditional reactive AI by enabling goal-driven, autonomous behavior, multi-step reasoning, memory management, and tool integration. The blog also covers state management, authentication, portability across compute environments, and observability best practices using Strands Agents SDK.

### [Blog 3 - Simplify log rotation with Amazon S3 Express One Zone](3.3-Blog3/)

This blog demonstrates how to implement log rotation using Amazon S3 Express One Zone. It explains how to configure Log4j2 and Mountpoint to write logs directly to S3, enabling automatic log rotation without relying on local storage. The post provides a detailed walkthrough for creating AWS resources, preparing the workspace, writing a Java logging application, monitoring logs, and cleaning up. Key takeaways include high-performance logging, seamless S3 integration, and using Mountpoint to translate file operations into S3 API calls.
