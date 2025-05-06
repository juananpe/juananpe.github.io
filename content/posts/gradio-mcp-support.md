---
title: "Gradio MCP Support: Building AI Tools in Just 5 Lines of Code"
date: 2025-05-06
draft: false
tags: ["MCP", "Gradio", "LLM", "AI Tools", "Model Context Protocol"]
categories: ["AI Development"]
cover:
    image: "/images/gradio-mcp-demo.png"
    alt: "Gradio MCP Support: Building AI Tools in Just 5 Lines of Code"
    caption: "Turn any Gradio app into an MCP server with one parameter"
---

## Gradio Now Supports the Model Context Protocol (MCP)

[Gradio](https://www.gradio.app/), the popular Python library for building ML interfaces, now officially supports the Model Context Protocol (MCP). This means any Gradio app can be called as a tool by Large Language Models (LLMs) like Claude and GPT-4.

## What is MCP?

The Model Context Protocol standardizes how applications provide context to LLMs. It allows models to interact with external tools such as image generators, file systems, and APIs. By providing a standardized protocol for tool-calling, MCP extends LLMs' capabilities beyond text generation.

## Building an MCP Server in Just 5 Lines of Code

Transform any Gradio application into an MCP server with just one parameter:

```python
import gradio as gr

def letter_counter(word, letter):
    """Count the occurrences of a specific letter in a word."""
    return word.lower().count(letter.lower())

demo = gr.Interface(fn=letter_counter, inputs=["text", "text"], outputs="number")
demo.launch(mcp_server=True)  # This is all you need!
```

By adding `mcp_server=True` to your `.launch()` call, Gradio automatically starts both the web interface and an MCP server.

## How It Works

Gradio converts your Python functions into MCP tools using docstrings to generate descriptions. To use your tools with an LLM client (Claude Desktop, Cursor, etc.), just add this to your client settings:

```json
{
  "mcpServers": {
    "gradio": {
      "url": "http://your-server:port/gradio_api/mcp/sse"
    }
  }
}
```

{{< figure src="/images/gradio-mcp-demo.png" alt="Gradio MCP Demo" >}}

## Key Features

1. **Automatic Tool Conversion**: Each API endpoint becomes an MCP tool
2. **Simple Configuration**: Enable via parameter (`mcp_server=True`) or environment variable
3. **File Handling**: Automatic handling of file data conversions
4. **Free Hosting**: Deploy on Hugging Face Spaces for a free hosted MCP server

## Additional Capabilities

- **Build MCP Clients**: Create chatbots that leverage external tools
- **Custom MCP Servers**: Interface with hosted Gradio apps for more control

## Getting Started

1. Install Gradio with MCP: `pip install "gradio[mcp]"`
2. Create your Gradio app
3. Launch with `mcp_server=True`
4. Configure an MCP-compatible client to use your server

Gradio's MCP support is a game-changer for AI development, allowing anyone to expose specialized functionality to AI systems through the standardized Model Context Protocol in just a few lines of code.

For more information:
- [Building an MCP Server with Gradio](https://www.gradio.app/guides/building-mcp-server-with-gradio)
- [Building an MCP Client with Gradio](https://www.gradio.app/guides/building-an-mcp-client-with-gradio)
- [What Is MCP?](https://www.anthropic.com/news/what-is-mcp)