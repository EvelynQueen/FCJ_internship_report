---
title: "AWS Compute Blog"
date: "2025-08-14"
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

## Xây dựng hiệu quả AI agents trên AWS Serverless

**Tác giả:** Anton Aleksandrov và Dhiraj Mahapatro
**Ngày đăng:** 14/08/2025  
**Chuyên mục:** Advanced (300), Amazon API Gateway, Amazon Bedrock, AWS Lambda, Generative AI, Serverless, Technical How-to

## Giới thiệu

Hãy tưởng tượng một AI assistant không chỉ phản hồi theo prompt – mà còn có khả năng suy luận dựa trên mục tiêu, hành động và tích hợp với các hệ thống real-time. Đây chính là lời hứa của agentic AI.

Theo Gartner, đến năm 2028 hơn 33% enterprise applications sẽ tích hợp khả năng agentic - tăng mạnh từ mức dưới 1% hiện nay. Trong khi những nỗ lực generative AI ban đầu tập trung vào GPU và việc huấn luyện mô hình, thì agentic systems chuyển trọng tâm sang CPU, orchestration, và integration với dữ liệu live – những nơi mà các tổ chức bắt đầu thấy rõ ROI (Return on Investment).

Trong blog này, bạn sẽ học cách xây dựng và vận hành serverless AI agents trên AWS bằng cách sử dụng các dịch vụ như Amazon Bedrock AgentCore (preview), AWS Lambda, và Amazon Elastic Container Service (Amazon ECS), cung cấp nền tảng compute có khả năng scale cho workloads agentic. Bạn cũng sẽ khám phá architectural patterns, state management, identity, observability, và cách sử dụng tools để hỗ trợ triển khai production-ready.

## Tổng quan

CCác AI assistant ban đầu là stateless và reactive – mỗi prompt được xử lý tách biệt, không có bộ nhớ về các tương tác trước đó hoặc nhận thức về bối cảnh rộng hơn. Dần dần, AI assistant trở nên thông minh hơn nhờ injection system prompts, lưu lại conversation history, và tích hợp enterprise knowledge thông qua Retrieval-Augmented Generation (RAG). Được minh họa trong hình bên dưới.

Tuy nhiên, chúng vẫn thiếu autonomy thực sự: không thể suy luận qua các mục tiêu nhiều bước, tự đưa ra quyết định, hoặc điều chỉnh workflow động dựa trên kết quả. Do đó, chúng hoạt động tốt trong Q&A hoặc workflow định sẵn, nhưng gặp khó khăn với nhiệm vụ phức tạp yêu cầu planning, dùng external tools, và decision-making.

Hệ thống Agentic AI chuyển từ việc tạo nội dung thụ động sang hành vi tự chủ, hướng tới mục tiêu (autonomous, goal-driven behavior). Được hỗ trợ bởi Large Language Models (LLMs) và tăng cường với memory, planning, và tool use, các hệ thống này có thể phân tách các tác vụ phức tạp thành các bước nhỏ hơn, lý luận qua từng bước, và thực hiện các hành động thời gian thực, chẳng hạn như calling APIs, executing tools, hoặc interacting with live data. Bằng cách tham chiếu LLM trong một control cycle quản lý context, memory, và decision-making, các hệ thống này có thể chọn công cụ phù hợp, điều chỉnh workflows, và tích hợp sâu vào môi trường doanh nghiệp, với các trường hợp sử dụng từ travel booking và financial analysis đến DevOps automation và code debugging. Điều này được gọi là agentic loop. Trong hệ thống này, agent dựa vào LLM’s reasoning output để thực thi tools, ghi nhận tool results, và cung cấp những kết quả này cho LLM như updated context (như minh họa trong sơ đồ dưới đây). Chu trình này lặp đi lặp lại cho đến khi LLM instructs the agent trả final output cho người gọi.

Trong khi agentic loop là một phương pháp nhẹ (lightweight approach) để cấu trúc các hệ thống này, các control flow paradigms khác, chẳng hạn như graph, swarm, và workflows, cũng có sẵn trong các open-source frameworks như LangGraph.

## Giới thiệu Strands Agents SDK

Strands Agents SDK là một code-first framework để xây dựng các AI agents sẵn sàng triển khai ( production-ready) với lượng boilerplate tối thiểu. Nó sử dụng hệ thống agentic loop đã đề cập ở trên và trừu tượng hóa các thách thức phổ biến như memory management, tool integration, và multi-step reasoning trong một lightweight, modular Python framework. Strands SDK quản lý state, tool orchestration, và multi-step reasoning để các agents có thể ghi nhớ các cuộc trò chuyện trước, gọi external APIs, thực thi business rules, và thích ứng với các changing inputs. Điều này cho phép bạn tập trung vào business logic của ứng dụng.

Vì các agents được xây dựng bằng Strands SDK về cơ bản là các ứng dụng Python, chúng có thể portable và chạy trên nhiều compute options khác nhau, chẳng hạn như Bedrock AgentCore Runtime, Lambda functions, ECS tasks, hoặc thậm chí locally. Điều này làm cho Strands Agents SDK trở thành một nền tảng mạnh mẽ để xây dựng các hệ thống AI scalable và goal-driven. Các phần tiếp theo giả định rằng bạn đang chạy các AI agents được xây dựng bằng Strands Agents SDK trên Lambda functions.

## Xây dựng AI agent serverless đầu tiên

Ví dụ: bạn xây dựng AI-powered corporate travel assistant trên AWS. Yêu cầu kỹ thuật:

1. Định nghĩa system prompts, memory và model
2. Tích hợp tools cho API calls, business logic, knowledge bases
3. Đảm bảo authentication và observability

Strands SDK xử lý phần phức tạp, bạn tập trung logic ứng dụng. Code snippet minh họa agent travel:

```python
from strands import Agent

agent = Agent(
    system_prompt=
      """You're a travel assistant that helps
         employees book business trips
         according to policy.""",
    model=my_model,
    tools=[get_policies, get_hotels, get_cars, book_travel]
)

response = agent("Book me a flight to NYC next Monday.")
```

Vậy là xong. Agent của bạn giờ đã có personality, memory, và khả năng sử dụng external tools. Lớp Agent trong Strands SDK trừu tượng hóa agentic logic, chẳng hạn như duy trì conversation history, xử lý LLM interactions, điều phối tools và external knowledge sources, và chạy toàn bộ agentic loop.

## Quản lý session state

Quản lý session state là yếu tố then chốt cho agentic workflows. Nó cho phép agents theo dõi mục tiêu xuyên suốt các tương tác – giúp cuộc hội thoại mạch lạc, duy trì context, và mang lại trải nghiệm cá nhân hóa. Nếu không có state management, mỗi prompt sẽ được xử lý tách biệt, khiến agent không thể tham chiếu lại context trước đó hoặc theo dõi các tác vụ đang diễn ra. Trong môi trường cloud, nơi ứng dụng cần stateless và có khả năng scale, giải pháp là externalize session state sang persistent storage, chẳng hạn như Amazon Simple Storage Service (Amazon S3). Cách này cho phép bất kỳ instance nào của agent cũng có thể khôi phục conversation history khi cần, mang lại trải nghiệm stateful liền mạch cho người dùng, trong khi bản thân agentic app vẫn stateless để đảm bảo khả năng mở rộng và tính linh hoạt.

AI agents được xây dựng với Strands lưu conversation history trong property agent.messages (xem documentation). Để hỗ trợ môi trường compute stateless, bạn có thể externalize agent state, lưu nó sau mỗi tương tác và khôi phục trước lần tiếp theo. Điều này duy trì tính liên tục giữa các invocations trong khi vẫn giữ các agent instance ở trạng thái stateless. Trong các agentic applications có nhận diện người dùng (user-aware), bạn sẽ muốn lưu state cho từng user, thường gắn với unique ID của người dùng. Ví dụ dưới đây minh họa cách thực hiện với class S3SessionManager có sẵn khi chạy agent trong môi trường stateless như Lambda function:

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

Khi sử dụng Bedrock AgentCore, hãy dùng primitive AgentCore Memory (serverless, fully managed) để quản lý sessions và long-term memory. Nó cung cấp context phù hợp cho models, đồng thời giúp agents học hỏi từ các tương tác trước đó. Bạn có thể tích hợp session manager của Strands hoạt động với AgentCore Memory tương tự như với S3SessionManager.

## Authentication và Authorization

Để enterprise AI agents hoạt động an toàn, chúng phải biết user là ai và user được phép làm gì. Điều này vượt xa việc xác thực danh tính cơ bản – bởi AI agents thường hành động thay mặt người dùng, nên chúng có thể cần thực thi role-based access controls (RBAC), hỗ trợ audit, và tuân thủ corporate policies.

Các dịch vụ AWS như Amazon Cognito, Amazon Identity and Access Management (IAM), và Amazon API Gateway cung cấp nền tảng vững chắc cho authentication và authorization. Ví dụ: bạn có thể dùng Cognito để xác thực user thông qua user pools hoặc federated identity providers, kết hợp với API Gateway và Lambda authorizer để kiểm tra quyền truy cập trước khi chuyển request đến agent (như minh họa trong sơ đồ ở phần trước). IAM policies định nghĩa agent được phép thực hiện những hành động nào. Sau khi user đã được authenticated và authorized, agent có thể trích xuất identity context (ví dụ từ JSON Web Token – JWT) để cá nhân hóa prompt, thực thi rules, hoặc hạn chế hành động động theo bối cảnh.

Ví dụ code sau minh họa cách lấy identity của user từ Authorization header và truyền nó vào agent:

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

Identity context có thể trở thành một phần trong execution loop của agent. Ví dụ: agent có thể kiểm tra department của user trước khi đặt chuyến đi, hoặc hạn chế truy cập vào sensitive tools nếu user không có quyền thích hợp. Việc tích hợp authentication từ sớm không chỉ tăng cường bảo mật, mà còn mở khóa các tính năng cá nhân hóa và audit, giúp agent enterprise-ready ngay từ ngày đầu.

Khi sử dụng Bedrock AgentCore, primitive AgentCore Identity cho phép AI agents truy cập an toàn vào AWS services và third-party tools – hoặc thay mặt người dùng, hoặc dưới danh tính riêng của agent với pre-authorized user consent. Nó cung cấp các provider OAuth 2.0 được quản lý cho cả inbound và outbound authentication. Trong giai đoạn preview, AgentCore Identity hỗ trợ các identity provider như Amazon Cognito, Auth0 by Okta, Microsoft Entra ID, GitHub, Google, Salesforce, và Slack. Tham khảo samples để biết chi tiết triển khai.

## Xây dựng Strands agents portable trên AWS

Strands Agents SDK là compute-agnostic. Các agent bạn xây dựng thực chất là Python applications chuẩn, có thể chạy trên bất kỳ loại compute nào.

Để đảm bảo portability và maintainability, bạn nên tách business logic của agent khỏi interface layer. Cách tiếp cận này cho phép bạn tái sử dụng cùng một core agent code trên nhiều môi trường khác nhau — dù được gọi thông qua API Gateway và Lambda functions, truy cập qua Application Load Balancer và Amazon ECS, chạy trên AgentCore Runtime, hay thậm chí được thực thi trực tiếp local trong quá trình development.

Lambda handler code:

```python
def handler(event: dict, ctx):
     user_id = extract_user_id(event)
     user_prompt = json.loads(event["body"])["prompt"]
     agent_response = call_agent(user_id, user_prompt)
     return {
          "statusCode":200,
          "body": json.dumps({
               "text": agent_response.mesage
          })
     }
```

AgentCore code:

```python
@app.entrypoint
def invoke(payload):
     user_id = extract_user_id(payload)
     user_prompt = payload.get("prompt")
     agent_response = call_agent(user_id, user_prompt)
     return {"result": agent_response.message}
```

HTTP Handler code:

```python
@app.post("/prompt")
async def prompt(request: Request, prompt_request: PromptRequest):
    user_id=extract_user_id(request)
    user_prompt = prompt_request.prompt
    agent_response = call_agent(user_id, user_prompt)
    return {"text": agent_response.message}
```

Local testing:

```python
if __name__ == "__main__":
     user_id="local-testing-user"
     user_prompt="book me a trip to NYC"
     agent_response = call_agent(user_id, user_prompt)
     return agent_response.message
```

Agent code:

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

## Mở rộng chức năng agent với Tools

Một điểm mạnh then chốt của agentic systems là khả năng invoke tools để thực hiện hành động hoặc truy xuất dữ liệu real-time, cho phép agents tương tác với thế giới bên ngoài chứ không chỉ đơn thuần tạo văn bản. Strands Agents SDK bao gồm các built-in tools và cho phép bạn định nghĩa custom tools của riêng mình, dưới dạng in-process Python functions hoặc external tools có thể truy cập qua HTTP sử dụng Model Context Protocol (MCP). Các tools này có thể fetch data, gọi APIs, hoặc trigger workflows, và có thể được đăng ký để agent sử dụng trong quá trình suy luận và thực thi.

Snippet dưới đây minh họa cách tạo một in-process tool. Tham khảo tài liệu để xem thêm nhiều ví dụ khác.

```python
from strands import tool

@tool
def get_weather(city: str) -> str:
    weather = call_weather_api(city)
    return f"The current weather in {city} is {weather}"
```

### Tích hợp với MCP servers

Model Context Protocol (MCP) là một open standard giúp decouple agents khỏi tools bằng cách sử dụng client-server model. Thay vì nhúng trực tiếp logic của tool vào trong agent, agent của bạn sẽ trở thành một MCP client kết nối tới một hoặc nhiều MCP servers – mỗi server sẽ expose tools, resources, và reusable prompts.

Việc chạy remote MCP servers đặc biệt hữu ích khi các tools trải rộng nhiều business domains hoặc được cung cấp bởi third-party vendors, tương tự như cách microservices tách biệt trách nhiệm giữa các team và hệ thống. Sự tách biệt này cho phép mỗi domain team tự quản lý tool của họ một cách độc lập, đồng thời expose một interface consistent và standardized cho các agents. Nó cũng cho phép reuse, versioning, và centralized governance mà không cần tightly coupling logic vào agent. Bằng cách decouple tools khỏi agents, MCP mở khóa khả năng composability, scalability, và sự phát triển dài hạn của hệ sinh thái.

Snippet sau minh họa cách cấu hình một MCP client để kết nối đến remote MCP Server, lấy danh sách tools, và tích hợp các tools đó với một agent:

```python
mcp_client = MCPClient(lambda: streamablehttp_client(
    url=mcp_endpoint,
    headers={"Authorization": f"Bearer {token}"},
))

with mcp_client:
  tools = mcp_client.list_tools_sync()
  agent = Agent(tools=tools)
```

Khi sử dụng Bedrock AgentCore, bạn có thể vận hành MCP ở scale thông qua AgentCore Gateway. Nó cung cấp cách thức dễ dàng và an toàn để developer xây dựng, triển khai, khám phá, và kết nối đến remote tools như trên ở quy mô lớn. Với AgentCore Gateway, developer có thể convert APIs, Lambda functions, và existing services thành các công cụ MCP-compatible, và expose chúng tới agents thông qua Gateway endpoints chỉ với một vài dòng code.

## Monitoring and observability

Observability là yếu tố thiết yếu khi vận hành AI agents. Ngoài các traditional metrics như uptime và latency, agentic systems còn đưa ra những chiều đo telemetry mới, chẳng hạn như LLM latency, token consumption, và tracing reasoning cycles. Các metrics mới này cực kỳ quan trọng để hiểu rõ cả hiệu năng lẫn chi phí của hệ thống agentic.

Khi deploy agents bằng các dịch vụ AWS như Bedrock AgentCore, Lambda, hoặc ECS, bạn sẽ thừa hưởng các khả năng observability tích hợp sẵn, ví dụ như tích hợp liền mạch với Amazon CloudWatch cho metrics, logs, và distributed tracing. Điều này đơn giản hóa việc theo dõi invocation counts, errors, request duration, và concurrency, như minh họa trong hình dưới – những yếu tố cần thiết để vận hành các ứng dụng agentic đáng tin cậy và có khả năng scale.

Ngoài ra, Strands Agents SDK cung cấp các tính năng agent observability built-in. Nó sử dụng OpenTelemetry (OTEL) để tự động trace mỗi tương tác của agent, bao gồm spans cho LLM calls, tool usage, và context updates. Nó cũng export các metrics chi tiết như token counts, tool execution times, và decision cycle durations. Các metrics này có thể được gửi tới bất kỳ backend nào tương thích với OTEL, mang lại khả năng quan sát real-time, chi tiết về cách agents suy luận, hành động, và thích nghi. Snippet dưới đây minh họa built-in token usage metrics:

```json
  accumulated_usage": {
    "inputTokens": 1539,
    "outputTokens": 122,
    "totalTokens": 1661
  },
  "average_cycle_time": 0.881234884262085,
  "total_cycles": 2,
  "total_duration": 1.881234884262085,
  ... redacted ...
```

Tìm hiểu thêm về observability và evaluation của Strands agents trong sample code này.

Khi sử dụng Bedrock AgentCore, primitive AgentCore Observability giúp bạn log và thu thập metrics cũng như traceability từ các primitive khác của AgentCore như runtime, memory, và gateway, như mô tả trong tutorial.

## Security considerations

Bạn nên xây dựng secure communication và các access control layers khi deploy AI agents tích hợp với remote MCP servers. Tất cả các tương tác client-server phải được mã hóa bằng TLS, lý tưởng nhất là mutual TLS (mTLS) để xác thực hai chiều. Quyền truy cập vào tools cần được xác thực thông qua authorization checks với fine-grained permissions nhằm thực thi nguyên tắc least privilege access. Deploy MCP servers phía sau API Gateway cung cấp thêm nhiều lớp bảo mật như DDoS protection, WAF, và centralized authentication. Hãy sử dụng khả năng API Gateway logging để ghi lại caller identity và execution outcomes. Việc sử dụng các trusted, versioned MCP repositories giúp bảo vệ chống lại supply chain attacks và đảm bảo consistent tool governance trên các team. Vì các giao thức như MCP đang phát triển rất nhanh, bạn luôn nên dùng phiên bản mới nhất để giảm thiểu rủi ro security vulnerabilities.

Ngoài ra, bạn nên tận dụng security best practices được mô tả trong AWS Well-Architected Framework Security Pillar, chẳng hạn như: thực thi strict IAM role scoping, tích hợp với identity providers để có user context, mã hóa toàn bộ dữ liệu in transit và at rest, và sử dụng VPC endpoints cùng PrivateLink để giới hạn network exposure. Để bảo vệ chống lại prompt injection attacks, hãy sanitize inputs và đảm bảo duy trì comprehensive audit logs cho compliance và governance.

## Sample project

Hãy làm theo hướng dẫn trong [GitHub repo](https://github.com/aws-samples/sample-serverless-mcp-servers/tree/main/strands-agent-on-lambda) này để deploy một sample project triển khai các practices được mô tả trong bài viết, sử dụng [AWS Serverless](https://aws.amazon.com/serverless/) compute. Repo bao gồm một travel agent được implement bằng Strands Agents SDK và một remote MCP server, cả hai đều chạy dưới dạng Lambda functions.

## Kết luận

Agentic AI vượt ra ngoài các tương tác prompt-response đơn giản để cho phép dynamic, goal-driven workflows. Trong bài viết này, bạn đã học cách xây dựng các agents có khả năng scalable và production-ready trên AWS bằng cách sử dụng Strands Agents SDK cùng các dịch vụ serverless như Lambda và Amazon ECS.

Bằng cách externalizing state, tích hợp authentication, và bổ sung observability, các agents có thể vận hành một cách an toàn và có khả năng mở rộng. Với khả năng hỗ trợ cả in-process và remote tools thông qua MCP, bạn có thể tách biệt rõ ràng các trách nhiệm và xây dựng những hệ thống composable, enterprise-ready. Bạn có thể kết hợp các patterns này để triển khai AI agents thông minh, linh hoạt, phù hợp tự nhiên với modern cloud và event-driven architectures.

## Tài nguyên hữu ích

- [Strands Agents SDK Docs](https://strandsagents.com/latest/)
- [Amazon Bedrock AgentCore User guide](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/what-is-bedrock-agentcore.html)
- [MCP Protocol Specification](https://modelcontextprotocol.io/specification/versioning)
- [Sample Serverless MCP Servers](https://github.com/aws-samples/sample-serverless-mcp-servers)
- [Serverless Land](https://www.serverlessland.com/)
