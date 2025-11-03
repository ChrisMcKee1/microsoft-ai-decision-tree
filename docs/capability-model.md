---
layout: default
title: Five-Layer Capability Model
nav_order: 3
description: "Understanding Microsoft's AI portfolio through five capability layers"
---

# Five-Layer Capability Model

Microsoft's AI portfolio is organized into **five capability layers**. Understanding this structure helps you select the right technology for your requirements.

---

## Layer 1: Consumption (End-User AI)

Ready-to-use AI experiences for immediate productivity.

| Feature | Description | Documentation |
|---------|-------------|---------------|
| **Microsoft 365 Copilot** | Integrated assistant across Word, Excel, Teams, Outlook with tenant security | [Docs](https://learn.microsoft.com/en-us/microsoft-365-copilot/) |
| **Built-in Agents** | Researcher, Analyst, Visual Creator, Prompt Coach, Idea Coach, Writing Coach | [Docs](https://learn.microsoft.com/en-us/training/modules/explore-prebuilt-microsoft-365-copilot-agents/) |
| **Agent Store** | Discover, acquire, and manage prebuilt agents in M365 apps | Available in-app (June 2025) |

**When to use:** Broad productivity gains, existing M365 licenses, no custom development needed

---

## Layer 2: Extensibility (Enhance Existing Copilots)

Extend M365 Copilot with organizational knowledge and actions.

| Extension Type | Description | Documentation |
|----------------|-------------|---------------|
| **Graph Connectors** | Index external data into Microsoft Graph for Copilot discovery | [Docs](https://learn.microsoft.com/en-us/microsoft-365-copilot/microsoft-365-copilot-extensibility) |
| **AI Plugins** | Add actionable skills to M365 Copilot (Preview) | [Docs](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-plugins) |
| **Teams Message Extensions** | Extend Copilot with Teams-based actions | [Docs](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions) |
| **Declarative Agents** | Configure agents with instructions, knowledge sources, and actions | [Docs](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/build-declarative-agents) |

**When to use:** Extend M365 Copilot with company data, add custom skills, stay within M365 trust boundary

---

## Layer 3: Development Platforms (Build Custom Agents)

Platforms for building agents with varying levels of control and complexity.

| Technology | Description | Key Capabilities | Documentation |
|------------|-------------|------------------|---------------|
| **Copilot Studio** | Low-code to pro-code SaaS for custom agents | Managed governance, multi-channel, BYOM/BYOK | [Docs](https://learn.microsoft.com/en-us/microsoft-copilot-studio/) |
| **M365 Agents SDK** | Pro-code framework for multi-channel agents | BYO orchestrator (Semantic Kernel, LangChain, Agent Framework) | [Docs](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/) |
| **Agent Framework** | Orchestration SDK for workflow-based agents | Checkpointing, Executor/Edge patterns | [Docs](https://learn.microsoft.com/en-us/agent-framework/) |
| **Azure AI Foundry** | Code-first platform for AI models, RAG, evaluations | Works with or without Agent Service | [Docs](https://learn.microsoft.com/en-us/azure/ai-studio/) |
| **Azure AI Agent Service** | Managed PaaS for agent orchestration | Skills, memory, runtime infrastructure | [Docs](https://learn.microsoft.com/en-us/azure/ai-services/agents/) |

**When to use:** Custom business logic, multi-channel requirements, complex orchestration, Azure-native infrastructure

---

## Layer 4: Infrastructure & AI Services (Building Blocks)

Foundational services that power agents across all platforms.

| Service | Description | Key Capabilities | Documentation |
|---------|-------------|------------------|---------------|
| **Azure OpenAI Service** | Enterprise GPT models with VNet, RBAC, TPM | Managed LLM infrastructure | [Docs](https://learn.microsoft.com/en-us/azure/ai-services/openai/) |
| **Azure AI Search** | Vector/hybrid search for RAG | Semantic ranking, BYOK to Studio | [Docs](https://learn.microsoft.com/en-us/azure/search/) |
| **Azure API Management (AI Gateway)** | Centralized governance layer | Token rate limiting, model routing, chargeback, content safety, observability | [Docs](https://learn.microsoft.com/en-us/azure/api-management/genai-gateway-capabilities) |
| **Azure AI Content Safety** | Content filtering, groundedness detection | Moderation and safety controls | [Docs](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/) |
| **Prompt Flow** | GenAIOps for evaluations and orchestration | Model testing and deployment | [Docs](https://learn.microsoft.com/en-us/azure/machine-learning/prompt-flow/overview-what-is-prompt-flow) |
| **AI Builder** | Comprehensive prebuilt & custom AI models for Power Platform | Document processing (invoices, receipts, contracts), GPT text generation, sentiment analysis, entity extraction, vision (object detection, OCR), predictions | [Docs](https://learn.microsoft.com/en-us/ai-builder/) |
| **Copilot Studio Agent Flows** | Native automation workflows within Copilot Studio | Deterministic automation for agents; natural language or visual designer; billed via Copilot Studio capacity | [Docs](https://learn.microsoft.com/en-us/microsoft-copilot-studio/flows-overview) |
| **Azure Document Intelligence** | Prebuilt and custom document models | OCR and document understanding | [Docs](https://learn.microsoft.com/en-us/azure/ai-services/document-intelligence/) |
| **Azure Logic Apps** | Pro-developer workflow automation for enterprise integration and AI agents | AI agent workflows (autonomous/conversational), MCP server for exposing workflows as AI tools, 1,400+ connectors, DevOps integration | [Docs](https://learn.microsoft.com/en-us/azure/logic-apps/) |

**When to use:** Reusable infrastructure across multiple agents, advanced RAG patterns, custom evaluations, governance, enterprise workflow automation

---

## Layer 5: Specialized Copilots (Domain-Specific)

Purpose-built AI assistants for specific workflows and industries.

| Copilot | Description | Primary Use Cases | Documentation |
|---------|-------------|-------------------|---------------|
| **GitHub Copilot** | Code generation and developer productivity | AI-assisted coding | [Docs](https://github.com/features/copilot) |
| **Security Copilot** | Security operations and threat analysis | SOC automation | [Docs](https://learn.microsoft.com/en-us/security-copilot/) |
| **Dynamics 365 Copilots** | Sales, Service, Marketing, Finance agents | CRM and ERP workflows | [Docs](https://learn.microsoft.com/en-us/dynamics365/release-plan/) |
| **Microsoft Fabric** | Data/AI agents for analytics and data engineering | Data pipelines and analytics | [Docs](https://learn.microsoft.com/en-us/fabric/get-started/microsoft-fabric-overview) |
| **Azure SRE Agent (Preview)** | AI-powered site reliability engineering assistant | Incident automation, explainable RCA, proactive monitoring, natural language Azure resource insights | [Docs](https://learn.microsoft.com/en-us/azure/sre-agent/overview) |
| **GitHub Copilot Coding Agent** | Agentic multi-file editing and autonomous issue resolution | Assigned GitHub issues create PRs; workspace-wide edits; Azure MCP Server integration | [Docs](https://learn.microsoft.com/en-us/azure/developer/azure-mcp-server/how-to/github-copilot-coding-agent) |

**When to use:** Domain expertise required, integrated with specialized platforms, industry-specific workflows

---

## Integration Patterns

### BYOM (Bring Your Own Model)
Import custom models from Azure AI Foundry into Copilot Studio (Preview)

### BYOK (Bring Your Own Knowledge)
Connect Azure AI Search indices to Copilot Studio for advanced RAG (GA)

### Multi-Agent Orchestration
Compose agents across Studio, SDK, and Foundry using Agent Framework or custom orchestration

### Unified Admin Center
Manage all agents (Studio, SDK, declarative) from Microsoft 365 admin center (GA June 2025)

---

## Sources

- [M365 Copilot Extensibility](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview) (Updated: September 2025)
- [Azure AI Foundry Agent Service](https://learn.microsoft.com/en-us/azure/ai-foundry/agents/whats-new) (Updated: April 2025)
- [M365 Release Notes](https://learn.microsoft.com/en-us/copilot/microsoft-365/release-notes) (Updated: September 2025)
- [AI Builder Overview](https://learn.microsoft.com/en-us/ai-builder/overview) (Updated: 2025 Release Wave 1)
- [Copilot Studio Agent Flows Overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/flows-overview) (Updated: 2025 Release Wave 1)
- [Azure SRE Agent Overview](https://learn.microsoft.com/en-us/azure/sre-agent/overview) (Preview, Updated: 2025)
- [GitHub Copilot Coding Agent - Azure MCP Integration](https://learn.microsoft.com/en-us/azure/developer/azure-mcp-server/how-to/github-copilot-coding-agent) (Updated: 2025)

---

**Next:** [Decision Framework](decision-framework.md) - Learn the three-phase methodology for technology selection
