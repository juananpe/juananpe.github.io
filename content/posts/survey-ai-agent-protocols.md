---
title: "A Survey of AI Agent Protocols: Framework and Future"
date: 2025-05-05T10:00:00Z
draft: false
tags:
  [
    "ai-agents",
    "llm",
    "agent-protocols",
    "agent-frameworks",
    "ai-ecosystem",
  ]
---

A recent research paper from Shanghai Jiao Tong University and the ANP Community provides the first comprehensive analysis of existing agent protocols, offering a systematic two-dimensional classification that distinguishes between context-oriented versus inter-agent protocols and general-purpose versus domain-specific protocols.

The paper highlights a critical issue in the rapidly evolving landscape of LLM agents: the lack of standardized protocols for communication with external tools or data sources. This standardization gap makes it difficult for agents to work together effectively or scale across complex tasks, ultimately limiting their potential for tackling real-world problems.

The researchers propose a layered architecture for the agent internet ecosystem consisting of three main layers: the Agent Internet (infrastructure layer), the Protocol Layer, and the Application Layer. This structure provides a foundation for understanding how different components interact across the emerging agent ecosystem.

{{< figure src="/images/agent-internet-ecosystem.png" alt="Agent Internet Ecosystem Layered Architecture" >}}

The paper also includes a timeline showing the development of LLMs, agent frameworks, agent protocols, and popular applications from 2019 through 2025, demonstrating the rapid evolution of this field. Notable protocols like MCP (Anthropic), A2A (Google), ANP (ANP Community), and Agora (University of Oxford) are categorized by their development stage and application scenarios.

{{< figure src="/images/ai-agents-protocol-timeline.png" alt="AI Domain Development Timeline" >}}

When evaluating agent protocols, the researchers identify several critical dimensions:

1. **Efficiency**: Focusing on latency, throughput, and resource utilization
2. **Scalability**: Ensuring stable performance as networks and tools expand
3. **Security**: Implementing authentication, access control, and data safeguards
4. **Reliability**: Maintaining consistent and fault-tolerant communication
5. **Extensibility**: Allowing evolution without disrupting existing systems
6. **Operability**: Ease of implementation and integration
7. **Interoperability**: Enabling seamless communication across diverse platforms

A particularly illuminating example from the paper demonstrates how different protocols handle the same task—planning a five-day trip from Beijing to New York—highlighting the architectural differences between approaches like MCP (single agent invoking all tools), A2A (complex inter-agent collaboration), ANP (cross-domain inter-agent protocol), and Agora (language to protocol generation).

{{< figure src="/images/agent-protocols-comparison.png" alt="Agent Protocols Comparison Use Case" >}}

While the field of agent protocols is still in its early days, this research provides a valuable framework for understanding current approaches and the characteristics necessary for next-generation protocols that will enable more sophisticated agent collaboration and collective intelligence.

You can find the full Twitter thread by Omar Saravia discussing this paper here:
[https://x.com/omarsar0/status/1918723145923453022](https://x.com/omarsar0/status/1918723145923453022)

The complete research paper "A Survey of AI Agent Protocols" is available on arXiv:
[https://arxiv.org/abs/2504.16736](https://arxiv.org/abs/2504.16736)