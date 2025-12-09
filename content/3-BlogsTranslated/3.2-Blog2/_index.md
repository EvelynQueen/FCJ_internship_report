---
title: "AWS Compute Blog"
date: "2025-08-14"
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

## Effectively building AI agents on AWS Serverless

> by Anton Aleksandrov and Dhiraj Mahapatro on 14 AUG 2025 in Advanced (300), Amazon API Gateway, Amazon Bedrock, AWS Lambda, Generative AI, Serverless, Technical How-to

Imagine an AI assistant that doesn’t just respond to prompts – it reasons through goals, acts, and integrates with real-time systems. This is the promise of agentic AI.

According to Gartner, by 2028 over 33% of enterprise applications will embed agentic capabilities – up from less than 1% today. While early generative AI efforts focused on GPUs and model training, agentic systems shift the focus to CPUs, orchestration, and integration with live data – the places where organizations are starting to see real return on investment (ROI).

In this post, you’ll learn how to build and run serverless AI agents on AWS using services such as Amazon Bedrock AgentCore (preview as of this post publication), AWS Lambda, and Amazon Elastic Container Service (Amazon ECS), which provide scalable compute foundations for agentic workloads. You’ll also explore architectural patterns, state management, identity, observability, and tool usage to support production-ready deployments.

## Overview

Early AI assistants were stateless and reactive – each prompt processed in isolation, with no memory of prior interactions or awareness of broader context. Gradually, AI assistants became more capable by injecting system prompts, preserving conversation history, and incorporating enterprise knowledge using Retrieval-Augmented Generation (RAG).

Despite these improvements, traditional AI assistants still lacked true autonomy. They couldn’t reason through multi-step goals, make decisions on their own, or adjust workflows dynamically based on outcomes. As a result, they worked well for simpler Q&A or predefined workflows, but struggled with dynamic, more complex, real-world tasks that require planning, using external tools, and making decisions along the way.

Agentic AI systems shift from passive content generation to autonomous, goal-driven behavior. Powered by Large Language Models (LLMs) and enhanced with memory, planning, and tool use, these systems can break down complex tasks into smaller steps, reason through each step, and take real-time actions, such as calling APIs, executing tools, or interacting with live data. By referencing the LLM within a control cycle that manages context, memory, and decision-making, these systems can choose the right tools, adapt workflows, and integrate deeply into enterprise environments, with use cases ranging from travel booking and financial analysis to DevOps automation and code debugging. This is referred to as an agentic loop.

While agentic loop is a lightweight approach to structuring these systems, other control flow paradigms, such as graph, swarm, and workflows, are also available in open-source frameworks like LangGraph.

## Introducing Strands Agents SDK

Strands Agents SDK is a code-first framework to build production-ready AI agents with minimal boilerplate. It utilizes the above-mentioned agentic loop system and abstracts common challenges like memory management, tool integration, and multi-step reasoning in a lightweight, modular Python framework. Strands SDK handles state, tool orchestration, and multi-step reasoning so agents can remember past conversations, call external APIs, enforce business rules, and adapt to changing inputs. This allows you to focus on the application’s business logic.

Because agents built with Strands SDK are essentially Python apps, they’re portable and can run across different compute options, such as Bedrock AgentCore Runtime, Lambda functions, ECS tasks, or even locally. This makes Strands Agents SDK a powerful foundation for building scalable and goal-driven AI systems. The following sections assume you’re running your AI agents built with Strands Agents SDK on Lambda functions.

## Building your first serverless AI agent

Imagine you’re building an AI-powered corporate travel assistant on AWS, and you have the following technical requirements:

- Define the system prompts, memory, and model you want to use
- Integrate tools for API calls, business logic, and knowledge bases
- Ensure authentication and observability

Strands SDK handles heavy lifting, so you can focus on building smart, responsive agents with minimal overhead. The following code snippet creates a simple agent:

```python
from strands import Agent

agent = Agent(
    system_prompt="""
You're a travel assistant that helps
employees book business trips
according to policy.""",
    model=my_model,
    tools=[get_policies, get_hotels, get_cars, book_travel]
)

response = agent("Book me a flight to NYC next Monday.")
```

## Session state management

Session state management is critical for agentic workflows. It allows agents to track goals across interactions – enabling coherent conversations, retaining context, and providing personalized experiences. Without state management, each prompt is handled in isolation, making it impossible for the agent to reference prior context or track ongoing tasks. In cloud environments, the solution is to externalize session state to persistent storage, such as Amazon Simple Storage Service (Amazon S3).

```python
session_manager = S3SessionManager(
    session_id=f"session_for_user_{user.id}",
    bucket=SESSION_STORE_BUCKET_NAME,
    prefix="agent_sessions"
)

agent = Agent(
    session_manager=session_manager
)
```

## Authentication and authorization

For enterprise AI agents to operate safely, they must know who the user is and what they are allowed to do. This goes beyond basic identity validation – AI agents often act on behalf of users, so they might need to enforce role-based access controls, support audit, and comply with corporate policies.

AWS services like Amazon Cognito, Amazon Identity and Access Management (IAM), and Amazon API Gateway provide a solid foundation for authentication and authorization. After authentication and authorization, the agent can extract identity context from a JSON Web Token (JWT) to personalize prompts and enforce rules.

```python
def handler(event: dict, ctx):
    user_id = extract_user_id(event["headers"]["Authorization"])
    user_prompt: dict = json.loads(event["body"])["prompt"]
    agent_response = agent.prompt(user_id, user_prompt)

    return {
        "statusCode": 200,
        "body": json.dumps({"text": agent_response.text})
    }
```

## Building portable Strands agents on AWS

Strands Agents SDK is compute-agnostic. Agents can run on Lambda, ECS, AgentCore Runtime, or locally. Separate your business logic from the interface layer for portability.

### Lambda handler code:

```python
def handler(event: dict, ctx):
    user_id = extract_user_id(event)
    user_prompt = json.loads(event["body"])["prompt"]
    agent_response = call_agent(user_id, user_prompt)
    return {
        "statusCode":200,
        "body": json.dumps({"text": agent_response.mesage})
    }
```

### AgentCore code:

```python
@app.entrypoint
def invoke(payload):
    user_id = extract_user_id(payload)
    user_prompt = payload.get("prompt")
    agent_response = call_agent(user_id, user_prompt)
    return {"result": agent_response.message}
```

### HTTP Handler code:

```python
@app.post("/prompt")
async def prompt(request: Request, prompt_request: PromptRequest):
    user_id=extract_user_id(request)
    user_prompt = prompt_request.prompt
    agent_response = call_agent(user_id, user_prompt)
    return {"text": agent_response.message}
```

### Local testing code:

```python
if __name__ == "__main__":
    user_id="local-testing-user"
    user_prompt="book me a trip to NYC"
    agent_response = call_agent(user_id, user_prompt)
    return agent_response.message
```

### Agent code:

```python
def call_agent(user_id, user_prompt):
    agent = Agent(
        system_prompt="You’re a travel agent…",
        model=my_model,
        session_manager = my_session_manager,
    )
    agent_response = agent(user_prompt)
    return agent_response
```

## Extending agent functionality with tools

```python
from strands import tool

@tool
def get_weather(city: str) -> str:
    weather = call_weather_api(city)
    return f"The current weather in {city} is {weather}"
```

## Integrating with remote MCP servers

```python
mcp_client = MCPClient(lambda: streamablehttp_client(
    url=mcp_endpoint,
    headers={"Authorization": f"Bearer {token}"},
))

with mcp_client:
  tools = mcp_client.list_tools_sync()
  agent = Agent(tools=tools)
```

## Monitoring and observability

```json
{
  "accumulated_usage": {
    "inputTokens": 1539,
    "outputTokens": 122,
    "totalTokens": 1661
  },
  "average_cycle_time": 0.881234884262085,
  "total_cycles": 2,
  "total_duration": 1.881234884262085
}
```

## Security considerations

- Encrypt all client-server interactions with TLS
- Validate tool access through fine-grained authorization
- Deploy MCP behind API Gateway for additional security layers
- Follow AWS Well-Architected Framework Security Pillar best practices

## Sample project

Follow instructions in this [GitHub repo](https://github.com/aws-samples/sample-serverless-mcp-servers/tree/main/strands-agent-on-lambda) to deploy a sample project implementing the practices described in this post using the [AWS Serverless](https://aws.amazon.com/serverless/) compute. The repo includes a travel agent implemented with Strands Agents SDK and a remote MCP server, both running as Lambda functions.

## Conclusion

Agentic AI enables dynamic, goal-driven workflows. By externalizing state, integrating authentication, and adding observability, agents operate securely at scale.

## Useful resources

- [Strands Agents SDK Docs](https://strandsagents.com/latest/)
- [Amazon Bedrock AgentCore User guide](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/what-is-bedrock-agentcore.html)
- [MCP Protocol Specification](https://modelcontextprotocol.io/specification/versioning)
- [Sample Serverless MCP Servers](https://github.com/aws-samples/sample-serverless-mcp-servers)
- [Serverless Land](https://www.serverlessland.com/)
