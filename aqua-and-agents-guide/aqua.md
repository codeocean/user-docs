---
metaLinks:
  alternates:
    - https://app.gitbook.com/s/PvA82xvbvyt7rVs0IKXN/aqua-and-agents-guide/aqua
---

# Aqua

## Prerequisites

Ensure Aqua is enabled in your Code Ocean deployment by clicking the **Aqua** icon to open the chat box in the Navigation sidebar. Reach out to your Code Ocean admin if you require Aqua to be enabled.

<figure><img src="../.gitbook/assets/Screenshot 2026-01-22 at 11.55.09 AM.png" alt="" width="509"><figcaption></figcaption></figure>



## The AI Assistant for Trusted Science

Aqua is Code Ocean’s built-in AI agent, designed specifically to handle requests within the platform. Aqua combines a custom platform-specific knowledge base with two key capabilities:

1. **Reasoning power**: Aqua is built on Anthropic’s Sonnet 4 large language model (LLM).
2. **Contextual awareness**: Aqua has knowledge of what the user is seeing in the Code Ocean UI and therefore understands the context of each user request.

Aqua comes with AWS Bedrock integration, so that all AI requests and capabilities run securely within your VPC deployment.&#x20;

In addition, Aqua comes with the Code Ocean MCP already attached, allowing the agent to safely and securely perform actions on users’ behalf, with their unique permissions.

See [MCP Server](model-context-protocol-mcp.md) for more information on Code Ocean’s public MCP.&#x20;

## The Aqua Chat Interface

The Aqua chat interface provides a flexible, conversational workspace for interacting with Code Ocean.

Aqua includes **session management** tools with a sidebar that lets users view, search, create, rename, and delete chat sessions. Chat names are automatically generated to make it easy to recognize past conversations at a glance.

Users can customize how Aqua fits into their workspace using **flexible layout controls**, including options to expand or minimize the chat panel and dock it on the left or right side of the screen.

Aqua also supports **voice input** through a microphone button, allowing users to dictate prompts directly into the chat.

## How Aqua Responds to User Requests

When Aqua receives a request, it begins by reasoning through the task. To build transparency and trust, this reasoning is explicitly surfaced to the user. Aqua then returns a context-aware, richly formatted response aligned with Code Ocean’s environment and workflows. Finally, Aqua summarizes both the request and the executed actions, often adding a helpful Pro tip.&#x20;

This proactive behavior is shaped by system prompts crafted by Code Ocean, giving Aqua its distinctive personality: concise, scientifically precise, and tuned to communicate at the level of bioinformaticians and computational scientists.

<figure><img src="../.gitbook/assets/Screenshot 2025-09-16 at 11.27.24 AM.png" alt=""><figcaption></figcaption></figure>

