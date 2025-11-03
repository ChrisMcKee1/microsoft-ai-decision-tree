---
layout: default
title: Five-Layer Capability Model
nav_order: 2
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
| **Microsoft Agent Framework** | Orchestration SDK combining Semantic Kernel + AutoGen (Preview/Experimental) | Sequential, concurrent, handoff, magentic patterns; checkpointing, workflows, multi-agent orchestration | [Docs](https://learn.microsoft.com/en-us/dotnet/api/overview/azure/ai.projects.agent-readme) |
| **M365 Agents SDK** | Pro-code framework for multi-channel agents | BYO orchestrator (Agent Framework recommended, LangChain third-party) | [Docs](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/) |
| **Azure AI Foundry** | Code-first platform for AI models, RAG, evaluations | Works with or without Agent Service | [Docs](https://learn.microsoft.com/en-us/azure/ai-studio/) |
| **Azure AI Agent Service** | Managed PaaS for agent orchestration | Skills, memory, runtime infrastructure | [Docs](https://learn.microsoft.com/en-us/azure/ai-services/agents/) |
| **LangChain Ecosystem (Third-party)** | OSS framework for LLM applications (Python/JS) | **LangChain**: Azure integrations, prompt flow; **LangGraph**: agent workflows, state management; **LangSmith**: tracing & observability | [LangChain Docs](https://learn.microsoft.com/en-us/azure/machine-learning/prompt-flow/how-to-integrate-with-langchain) \| [LangGraph Docs](https://learn.microsoft.com/en-us/azure/developer/javascript/ai/langchain-agent-on-azure) \| [LangSmith Docs](https://learn.microsoft.com/en-us/azure/ai-foundry/how-to/develop/trace-agents-sdk) |

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
| **Azure AI Content Understanding (Preview)** | Multimodal content processing with generative AI | Document, image, audio, video analysis; zero-shot extraction; grounding & confidence scoring; RAG-ready | [Docs](https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/document/overview) |
| **Prompt Flow** | GenAIOps for evaluations and orchestration | Model testing and deployment | [Docs](https://learn.microsoft.com/en-us/azure/machine-learning/prompt-flow/overview-what-is-prompt-flow) |
| **AI Builder** | Comprehensive prebuilt & custom AI models for Power Platform | Document processing (invoices, receipts, contracts), GPT text generation, sentiment analysis, entity extraction, vision (object detection, OCR), predictions | [Docs](https://learn.microsoft.com/en-us/ai-builder/) |
| **Copilot Studio Agent Flows** | Native automation workflows within Copilot Studio | Deterministic automation for agents; natural language or visual designer; billed via Copilot Studio capacity | [Docs](https://learn.microsoft.com/en-us/microsoft-copilot-studio/flows-overview) |
| **Azure Document Intelligence** | Prebuilt and custom document models | OCR and document understanding | [Docs](https://learn.microsoft.com/en-us/azure/ai-services/document-intelligence/) |
| **Azure Logic Apps** | Pro-developer workflow automation for enterprise integration and AI agents | AI agent workflows (autonomous/conversational), MCP server for exposing workflows as AI tools, 1,400+ connectors, DevOps integration | [Docs](https://learn.microsoft.com/en-us/azure/logic-apps/) |
| **Azure Cosmos DB** | Globally distributed NoSQL database with AI capabilities | Vector search (IVF, HNSW, DiskANN), AI agent memory system, integrated vector database | [Docs](https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/vector-search) |
| **Azure Database for PostgreSQL** | Fully managed PostgreSQL with AI extensions | azure_ai extension (OpenAI + Cognitive Services), pgvector for vector search, in-database embeddings | [Docs](https://learn.microsoft.com/en-us/azure/postgresql/flexible-server/generative-ai-azure-overview) |
| **SQL Server 2025 (Preview)** | Enterprise database with native AI capabilities | VECTOR data type (float32/float16), vector functions & indexes (DiskANN), external AI model management, Copilot in SSMS | [Docs](https://learn.microsoft.com/en-us/sql/sql-server/what-s-new-in-sql-server-2025) |
| **Microsoft Fabric** | Unified analytics platform with AI capabilities | **Platform:** Lakehouse (Delta tables), Warehouse (T-SQL), OneLake (unified storage), SQL analytics endpoint, Azure AI Foundry integration. **AI Layer:** Copilot in Fabric (data science, factory, warehouse, Power BI, Real-Time Intelligence), Fabric Data Agents (Preview) | [Docs](https://learn.microsoft.com/en-us/fabric/fundamentals/microsoft-fabric-overview) |

**When to use:** Reusable infrastructure across multiple agents, advanced RAG patterns, custom evaluations, governance, enterprise workflow automation, vector storage & search, AI-powered data analytics

---

## Layer 5: Specialized Copilots (Domain-Specific)

Purpose-built AI assistants for specific workflows and industries.

| Copilot | Description | Primary Use Cases | Documentation |
|---------|-------------|-------------------|---------------|
| **GitHub Copilot** | Code generation and developer productivity | AI-assisted coding | [Docs](https://github.com/features/copilot) |
| **Security Copilot** | Security operations and threat analysis | SOC automation | [Docs](https://learn.microsoft.com/en-us/security-copilot/) |
| **Dynamics 365 Copilots** | Sales, Service, Marketing, Finance agents | CRM and ERP workflows | [Docs](https://learn.microsoft.com/en-us/dynamics365/release-plan/) |
| **Microsoft Fabric Data Agents (Preview)** | Conversational AI agents for analytics data | Transform enterprise data into Q&A systems; integrate with Copilot Studio, Azure AI Agent Service, Power BI Copilot | [Docs](https://learn.microsoft.com/en-us/fabric/data-science/concept-data-agent) |
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

**Layer 1 & 2:**
- [M365 Copilot Extensibility](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview) (Updated: September 2025)
- [M365 Release Notes](https://learn.microsoft.com/en-us/copilot/microsoft-365/release-notes) (Updated: September 2025)

**Layer 3:**
- [Azure AI Foundry Agent Service](https://learn.microsoft.com/en-us/azure/ai-foundry/agents/whats-new) (Updated: April 2025)
- [Microsoft Agent Framework Overview](https://learn.microsoft.com/en-us/dotnet/api/overview/azure/ai.projects.agent-readme) (Updated: 2025)
- [Agent Framework with M365 SDK](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/semantic-kernel-agent-framework) (Updated: 2025)
- [LangChain with Azure Machine Learning (Third-party)](https://learn.microsoft.com/en-us/azure/machine-learning/prompt-flow/how-to-integrate-with-langchain) (Updated: 2025)
- [LangGraph Tutorial with Azure AI Search (Third-party)](https://learn.microsoft.com/en-us/azure/developer/javascript/ai/langchain-agent-on-azure) (Updated: 2025)
- [LangSmith Tracing for Agents (Third-party)](https://learn.microsoft.com/en-us/azure/ai-foundry/how-to/develop/trace-agents-sdk) (Updated: 2025)

**Layer 4:**
- [Azure AI Content Understanding Document Solutions](https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/document/overview) (Preview, Updated: 2025)
- [Azure Cosmos DB Vector Search for NoSQL](https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/vector-search) (GA, Updated: 2025)
- [Azure Database for PostgreSQL - Azure AI Extension](https://learn.microsoft.com/en-us/azure/postgresql/flexible-server/generative-ai-azure-overview) (GA, Updated: 2025)
- [SQL Server 2025 - What's New](https://learn.microsoft.com/en-us/sql/sql-server/what-s-new-in-sql-server-2025) (Preview, Updated: November 2025)
- [Microsoft Fabric - Copilot Overview](https://learn.microsoft.com/en-us/fabric/fundamentals/copilot-fabric-overview) (GA, Updated: 2025)
- [AI Builder Overview](https://learn.microsoft.com/en-us/ai-builder/overview) (Updated: 2025 Release Wave 1)
- [Copilot Studio Agent Flows Overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/flows-overview) (Updated: 2025 Release Wave 1)

**Layer 5:**
- [Azure SRE Agent Overview](https://learn.microsoft.com/en-us/azure/sre-agent/overview) (Preview, Updated: 2025)
- [GitHub Copilot Coding Agent - Azure MCP Integration](https://learn.microsoft.com/en-us/azure/developer/azure-mcp-server/how-to/github-copilot-coding-agent) (Updated: 2025)

---

**Next:** [Decision Framework](decision-framework.md) - Learn the three-phase methodology for technology selection
