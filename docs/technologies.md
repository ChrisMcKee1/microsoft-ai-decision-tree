---
layout: default
title: Microsoft AI Technologies
nav_order: 8
description: "Complete reference for Microsoft's AI technology portfolio"
---

# Microsoft AI Technologies Reference

This section provides a comprehensive overview of Microsoft's AI technology stack, from end-user productivity tools to infrastructure services.

---

## Core AI Platforms

### Microsoft 365 Copilot
**Description:** Integrated AI assistant across M365 apps (Word, Excel, Teams, Outlook) with tenant context and Graph security.  
**Official Docs:** [Microsoft 365 Copilot Overview](https://learn.microsoft.com/en-us/microsoft-365-copilot/)

**Key Features:**
- Tenant-aware AI across M365 apps
- Built-in Graph security and compliance
- No custom development required
- $30/user/month licensing

**When to use:** Broad productivity gains, existing M365 licenses, no custom development needed

---

### Copilot Studio
**Description:** Graphical, low-code platform for building agents and agent flows with managed governance, ALM, and multi-channel deployment. Supports declarative agents (extend M365 Copilot) and custom engine agents (bring your own orchestration). Available as both standalone web app and Teams app.  
**Official Docs:** [Copilot Studio Documentation](https://learn.microsoft.com/en-us/microsoft-copilot-studio/)  
**Implementation Guide:** [aka.ms/CopilotStudioImplementationGuide](https://aka.ms/CopilotStudioImplementationGuide)

**Key Features:**
- **Low-code to pro-code agent development:** No-code (Copilot Studio Lite), low-code (full experience), or pro-code integration
- **1,400+ Power Platform connectors:** Seamless Microsoft and third-party service integration
- **Event Triggers (GA):** Autonomous agents responding to SharePoint, OneDrive, Planner, Recurrence events
- **Declarative agents:** Extend M365 Copilot with instructions, knowledge, actions (individual/departmental use)
- **Custom engine agents (GA):** Full control over orchestration, models, and workflows (complex scenarios, group collaboration, multi-channel)
- **Multi-channel deployment:** M365 Copilot, Teams, Web, Mobile, Facebook, WhatsApp (via Azure Bot Service)
- **BYOK (GA):** Azure AI Search integration, SharePoint/OneDrive (security-trimmed), Graph Connectors
- **BYOM (Preview):** Azure AI Foundry model integration
- Managed ALM via Power Platform solutions (in-product pipelines, Azure DevOps, GitHub Actions)

**NLU (Natural Language Understanding) Options:**
- **Generative AI Orchestration (Default):** LLM-driven multi-intent recognition, automatic topic/action selection, slot-filling, unified responses combining topics + actions + knowledge (up to ~128 triggerable items, ~5 chained messages per item)
- **Classic Orchestration (NLU):** Original NLU for simpler needs; 5-20 trigger phrases per topic, RegEx/List entities, no entity annotations required (⚠️ latency increases with excess training data)
- **Classic Orchestration (NLU+):** High-precision enterprise option; large-scale topics/entities, extensive training samples, entity annotations, precompiled model for consistent performance (⚠️ requires Dynamics 365 Contact Center license for voice/chat channels)
- **Azure CLU Integration:** Link existing Azure Conversational Language Understanding models for advanced entity extraction, more languages (requires Azure subscription + manual model synchronization)

**Topic & Orchestration Architecture:**
- **Topics:** Conversational thread portions authored on visual canvas with nodes (send message, ask question, conditional logic)
- **Generative Orchestration:** Agent selects best combination of topics/actions/knowledge at runtime based on descriptions and user queries
- **Classic Orchestration:** Trigger phrases drive topic selection via NLU, deterministic conversation flows
- **Multi-Agent Systems (Preview):** Child agents (lightweight, embedded) and connected agents (independent, reusable across solutions, Fabric data agents supported)
- **Autonomous Agents:** Event-driven triggers (SharePoint file changes, Planner task updates, recurrence schedules) with proactive actions

**Performance Characteristics:**
- **Optimized for:** Speed to market, managed operations, built-in governance, connector ecosystem integration
- **Managed orchestration layer:** Provides convenience (ALM, multi-channel, governance) with managed SaaS infrastructure
- **Power Automate integration:** 120-second flow execution limit, 100-second return requirement to Copilot Studio; HTTP Request node offers lower latency for simple calls
- **Latency profile:** Suitable for <1s response scenarios; for <100ms requirements, consider Azure AI Foundry

**Context Window (GPT-5 Preview):**
- **GPT-5 chat/reasoning:** Up to 400k tokens (model capacity)
- **Effective context:** Varies based on agent configuration, orchestration features, and system variables
- **Trade-off:** Managed platform convenience vs full model context (Foundry provides full context but requires infrastructure management)

**Knowledge Sources (BYOK):**
- **Internal:** SharePoint/OneDrive (security-trimmed), Dataverse tables, Documents (uploaded to Dataverse), Graph Connectors, Azure AI Search
- **External:** Public websites (Bing-indexed), Web Search (Grounding with Bing Search), Bing Custom Search
- **Generative Answers:** Combines knowledge sources with LLM responses, citations, moderation

**Multi-Channel Deployment:**
- **M365:** Teams, M365 Copilot, SharePoint
- **Web/Mobile:** Custom website, demo website, mobile apps
- **Social/Messaging:** Facebook, WhatsApp, SMS
- **Contact Center:** Dynamics 365 Omnichannel (live chat hand-off to agents), voice IVR integration
- **Other:** Azure Bot Service channels (Slack, Telegram, etc.)

**Licensing:**
- **Prepaid capacity:** Copilot Credit packs (predictable high-volume, pooled tenant-wide)
- **Pay-as-you-go:** $0.01/Copilot Credit (Azure subscription, consumption-based)
- **Quotas:** 8,000 RPM (general messages), 50-100+ RPM (gen AI, scales with message packs)

**When Copilot Studio is the Right Tool:**
- **Declarative agents:** Individual/team productivity in M365 context, faster implementation (days), user workflows within M365 apps (SharePoint, OneDrive, Teams via @mentions)
- **Custom engine agents:** Complex workflows with custom orchestration, specific business logic, group collaboration in Teams channels, multi-system integrations, proactive messaging/event-driven workflows, multi-channel deployment (beyond M365), migrating existing conversational bots
- Leveraging Power Platform's 1,400+ connectors and event triggers
- Prefer Microsoft-managed infrastructure and built-in governance
- Team includes makers and developers; no deep AI/ML expertise required

**Sources:**
- [Copilot Studio Fundamentals](https://learn.microsoft.com/en-us/microsoft-copilot-studio/fundamentals-what-is-copilot-studio) (Updated: 2024-10-15)
- [Agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agents-overview) (Updated: 2024-11-05)
- [Implementation Guide](https://aka.ms/CopilotStudioImplementationGuide) (PDF Version 2.0)
- [Event Triggers Overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-triggers-about) (Updated: 2024-09-20)

---

### Azure AI Foundry
**Description:** Code-first platform for AI models, prompt flow, evaluations, RAG, and safety features. Works with or without Azure AI Agent Service.  
**Official Docs:** [Azure AI Foundry Portal](https://learn.microsoft.com/en-us/azure/ai-studio/)

**Key Features:**
- Code-first AI development
- Model catalog (Azure OpenAI, open-source models)
- Prompt flow for orchestration
- Evaluation and safety tools
- RAG (Retrieval-Augmented Generation) patterns
- Azure consumption pricing

**Performance Characteristics:**
- **Optimized for:** Latency-sensitive applications, full architectural control, custom implementations
- **Direct model API access:** Minimal orchestration overhead for sub-100ms response scenarios
- **Custom optimization:** Full control over caching, batching, PTU provisioning, infrastructure
- **Latency profile:** Suitable for real-time, high-throughput scenarios; requires performance tuning expertise

**Context Window (GPT-5):**
- **GPT-5-codex/pro:** 400k tokens (272k input, 128k output)
- **GPT-5-chat:** 128k tokens
- **Full model context:** No SaaS orchestration layer consumption
- **Trade-off:** Full context available but requires self-managed infrastructure and deployment

**When Azure AI Foundry is the Right Tool:**
- Latency-sensitive applications (<100ms response requirements)
- Need full control over architecture and optimization
- Custom AI patterns beyond platform capabilities
- Custom integrations outside standard connector ecosystem
- Team has Azure infrastructure and AI engineering expertise
- High-throughput scenarios requiring PTU provisioning

**Sources:**
- [Azure AI Foundry Documentation](https://learn.microsoft.com/en-us/azure/ai-studio/)
- [Performance and Latency Guide](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/how-to/latency)
- [GPT-5 Quotas and Limits](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/quotas-limits#gpt-5-series)
- [Model Choice Guide](https://learn.microsoft.com/en-us/azure/ai-foundry/foundry-models/how-to/model-choice-guide)
- [Foundry Models - GPT-5](https://learn.microsoft.com/en-us/azure/ai-foundry/foundry-models/concepts/models-sold-directly-by-azure#gpt-5)

---

### Azure AI Agent Service
**Description:** Managed PaaS for agent orchestration, skills management, and runtime infrastructure within Azure AI Foundry. Supports connected agents (multi-agent systems), 12+ built-in tools, full RBAC + VNet + BYO storage.  
**Official Docs:** [Azure AI Agent Service](https://learn.microsoft.com/en-us/azure/ai-services/agents/)

**Key Features:**
- Managed agent runtime infrastructure
- Connected agents (multi-agent systems)
- Memory and state management
- Full RBAC, VNet, private endpoints

**Built-in Tools (Knowledge):**
- **Azure AI Search:** Ground agents with indexed data, chat with your data
- **File Search:** RAG with proprietary documents (Azure Blob Storage, local files). Uses vector stores (up to 10,000 files), automatic chunking/embedding (text-embedding-3-large), hybrid search (keyword + semantic), reranking
- **Grounding with Bing Search:** Access real-time web information
- **Grounding with Bing Custom Search (Preview):** Enhanced responses with selected web domains
- **Microsoft Fabric (Preview):** Integrate with Fabric Data Agents for data analysis capabilities
- **SharePoint (Preview):** Chat with private SharePoint documents, OBO authentication for security-trimmed access, leverages M365 Copilot API built-in indexing
- **Licensed Data:** Proprietary data via licensed API keys (TripAdvisor, Morningstar, LexisNexis, LEGALFLY, etc.)

**Built-in Tools (Action):**
- **Function Calling:** Custom stateless functions
- **Azure Functions:** Intelligent, event-driven serverless code execution
- **Azure Logic Apps:** 1,400+ connector-based workflows
- **Code Interpreter:** Write and run Python code in sandboxed environment (data handling, visuals)
- **OpenAPI 3.0 Specified Tool:** Connect to external APIs via OpenAPI spec
- **Model Context Protocol (Preview):** Access tools hosted on existing MCP endpoints
- **Deep Research (Preview):** Multi-step web-based research with o3-deep-research model + Bing Search
- **Browser Automation (Preview):** Real-world browser tasks via natural language with Playwright Workspaces
- **Computer Use (Preview):** UI interaction via specialized computer-use-preview model, interprets raw pixel screenshots, virtual keyboard/mouse control
- **Image Generation (Preview):** Generate and edit images as part of conversations and multi-step workflows

**Agent Setup Options:**
- **Basic Setup:** Microsoft-managed search and storage (files stored in MS-managed storage, vector stores in MS-managed search)
- **Standard Setup:** BYO Azure AI Search + Blob Storage (files in your Blob, vector stores in your AI Search), private networking, no public egress by default

**When to use:** Managed agent orchestration at PaaS layer, scalable agent infrastructure, multi-agent systems, comprehensive built-in tool ecosystem, prefer Azure-managed RAG infrastructure

---

### AI Builder
**Description:** Power Platform AI services for document processing, vision, and data extraction. Callable from agents and Power Automate.  
**Official Docs:** [AI Builder Documentation](https://learn.microsoft.com/en-us/ai-builder/)

**Key Features:**
- Prebuilt AI models (document processing, vision, text analysis)
- Custom AI model training
- Power Platform integration
- Callable from Copilot Studio agents
- Power Automate integration

**Capabilities:**
- Document processing (invoices, receipts, contracts, business cards)
- Text generation and analysis (GPT, sentiment, entity extraction)
- Vision (object detection, OCR, image classification)
- Predictions (classification, regression)

**When to use:** Document understanding in Power Platform solutions, prebuilt AI capabilities, no-code AI

---

## Pro-Code Development Frameworks

### Azure Logic Apps
**Description:** Pro-developer workflow automation platform for enterprise integration and AI agent orchestration. Supports autonomous and conversational AI agent workflows (Preview) with Azure OpenAI and Azure AI Foundry integration. Can be configured as remote MCP servers to expose workflows as tools for LLMs and AI agents. 1,400+ connectors for building agent tools across cloud and on-premises systems.  
**Status:** Agent Workflows (Preview), MCP Server (Preview), Core Platform (GA)  
**Official Docs:** [Azure Logic Apps Documentation](https://learn.microsoft.com/en-us/azure/logic-apps/) | [Agent Workflows](https://learn.microsoft.com/en-us/azure/logic-apps/agent-workflows-concepts) | [MCP Server](https://learn.microsoft.com/en-us/azure/logic-apps/set-up-model-context-protocol-server-standard)

**Key Features:**
- 1,400+ connectors (cloud + on-premises)
- Visual workflow designer + code
- AI agent workflows (autonomous & conversational)
- MCP server capabilities (expose workflows as AI tools)
- State management and checkpointing
- DevOps integration (GitHub Actions, Azure DevOps)

**When to use:** Enterprise integration + AI agents, workflow automation with LLM integration, exposing enterprise systems as AI tools

---

### Microsoft 365 Agents SDK & Toolkit
**Description:** Pro-code framework for building multi-channel custom engine agents. Model-agnostic and orchestrator-agnostic (bring your own: Agent Framework recommended, LangChain third-party alternative). Deploys to M365 Copilot, Teams, Web, Mobile, SMS, Email, and 10+ external channels. Bot Framework successor (BF support ends Dec 31, 2025).  
**Status:** GA (C#, JavaScript, Python)  
**Official Docs:** [M365 Agents SDK](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/) | [Bot Framework Migration](https://aka.ms/bfmigrationguidance)

**Key Features:**
- Multi-channel deployment (10+ platforms)
- Model-agnostic (Azure OpenAI, OpenAI, Anthropic, custom)
- Orchestrator-agnostic (Agent Framework recommended, LangChain third-party, custom)
- Bot Framework successor
- Group productivity scenarios (Teams channels/meetings)
- Proactive messaging

**Supported Channels:**
- M365 Copilot
- Microsoft Teams
- Web, Mobile
- SMS, Email
- WhatsApp, Slack, and more

**When to use:** Multi-channel agents, full control over orchestration, Bot Framework migration, group productivity

---

### Microsoft Agent Framework
**Description:** Microsoft's next-generation orchestration framework for building multi-agent workflows (replaces Semantic Kernel agents in maintenance mode). Features: 5 orchestration patterns (Sequential, Concurrent, Handoff, Group Chat, Magentic), runtime for agent lifecycle management, message routing between agents, human-in-the-loop support. Works with M365 Agents SDK (BYO orchestrator model) or standalone. **Microsoft's investment direction for multi-agent orchestration.**  
**Status:** Preview/Experimental (C#, Python, Java) - **Active development, will GA soon**  
**Official Docs:** [Microsoft Agent Framework](https://learn.microsoft.com/en-us/agent-framework/) | [Agent Orchestration](https://learn.microsoft.com/en-us/semantic-kernel/frameworks/agent/agent-orchestration/)

**Key Features:**
- **5 Orchestration Patterns:** Sequential (pipelines), Concurrent (parallel analysis), Handoff (dynamic routing), Group Chat (collaborative problem solving), Magentic (complex multi-agent tasks)
- **Runtime:** Actor lifecycle management, message routing, independent orchestration executions
- **Modular Components:** Specialized agents for specific tasks with collaboration support
- **Human-in-the-Loop:** Human agents can participate in orchestration workflows
- **M365 Agents SDK Integration:** Recommended orchestrator for M365 SDK (BYO model)
- **Replaces Semantic Kernel Agents:** Semantic Kernel in maintenance mode (security patches only, no new features)

**When to use:** Multi-agent workflows requiring coordination, specialized task delegation, complex collaborative problem-solving, human-agent collaboration. **Use this instead of Semantic Kernel for new projects.**

**Sources:**
- [Microsoft Agent Framework](https://learn.microsoft.com/en-us/agent-framework/)
- [Agent Orchestration Patterns](https://learn.microsoft.com/en-us/semantic-kernel/frameworks/agent/agent-orchestration/)
- [Using with M365 Agents SDK](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/using-semantic-kernel-agent-framework)

---

## "Agent Framework" Terminology Clarification

The term "agent framework" refers to two distinct technologies:

**1. Microsoft Agent Framework (Orchestration SDK)**  
Open-source library for workflow-based orchestration. Public Preview. Use for: Executor/Edge workflows, checkpointing, M365 Agents SDK integration.

**2. Azure AI Agent Service (Managed PaaS)**  
Managed service for agent orchestration within Azure AI Foundry. GA. Use for: Managed infrastructure, Azure-hosted agents, scalable runtime.

**Quick Decision:**
- M365 productivity agents → M365 Agents SDK + Agent Framework
- Azure-hosted agents → Azure AI Foundry + AI Agent Service  
- Bot Framework migration → M365 Agents SDK
- Workflow orchestration + checkpointing → Agent Framework

---

## Technology Selection Quick Guide

| Your Need | Recommended Technology | Why? |
|-----------|------------------------|------|
| End-user productivity (no dev) | Microsoft 365 Copilot | Built-in, tenant-aware, immediate value |
| Custom agents (low-code) | Copilot Studio | Managed platform, fast deployment, governance |
| Custom agents (pro-code) | M365 Agents SDK or Azure AI Foundry | Full control, any model, any orchestrator |
| Managed agent runtime | Azure AI Agent Service | PaaS for agent infrastructure, multi-agent support |
| Enterprise workflow + AI | Azure Logic Apps | 1,400+ connectors, MCP server, AI agent workflows |
| Document processing | AI Builder | Prebuilt models, Power Platform integration |
| Workflow orchestration | Microsoft Agent Framework | Checkpointing, type-safe workflows, multi-agent patterns |

---

## Network Isolation Capabilities

Understanding network isolation options is critical for zero-trust architectures, air-gapped environments, and regulated industries requiring private networking.

### Azure AI Foundry & Agent Service

**VNet Support:** ✅ Full private networking support

**Key Capabilities:**
- VNet integration with container injection (platform APIs communicate within customer VNet)
- Private endpoints for all resources (Storage, AI Search, Cosmos DB, Foundry resource)
- Network Security Groups (NSGs) for traffic isolation
- **Standard Setup with Private Networking:** No public egress by default
- Customer-managed keys (CMK) optional
- Azure landing zone controls (Azure Policy, RBAC)

**Ideal for:** Zero-trust environments, air-gapped deployments, sovereign data strategies, full Azure Policy governance

**Sources:**
- [Configure Private Link](https://learn.microsoft.com/en-us/azure/ai-foundry/how-to/configure-private-link)
- [Virtual Networks for Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/agents/how-to/virtual-networks)

---

### Copilot Studio

**VNet Support:** ⚠️ Gateway-based (does NOT execute in customer VNet)

**Key Capabilities:**
- **On-premises data gateway** (for on-premises systems)
- **VNet data gateway** (GA, for Azure resources) — Microsoft-managed, supports private endpoints to Azure resources
- Requires Managed Environment in Power Platform + VNet support enabled
- External connectors inherit external system's network security posture

**Limitations:**
- Power Platform is a managed service (agent runtime NOT in customer VNet)
- Not suitable for fully air-gapped environments without gateway setup

**Ideal for:** Managed PaaS scenarios with Azure resource access via VNet gateway

**Sources:**
- [VNet Data Gateway](https://learn.microsoft.com/en-us/power-platform/admin/vnet-support-overview)
- [Managed Environments](https://learn.microsoft.com/en-us/power-platform/admin/managed-environment-overview)

---

### M365 Agents SDK

**VNet Support:** ✅ Full control (self-hosted)

**Key Capabilities:**
- When self-hosted in Azure: Full VNet integration, private endpoints, NSG controls
- Customer controls all networking decisions
- Supports air-gapped Azure deployments
- Hosting platform determines network security (Azure App Service, Container Apps, AKS, on-premises)

**Ideal for:** Organizations requiring custom network control, air-gapped support, or hybrid on-premises/cloud deployments

**Sources:**
- [M365 Agents SDK Overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agents-sdk-overview)

---

### M365 Copilot

**VNet Support:** ❌ No custom VNet support

**Key Capabilities:**
- Fully managed SaaS (no VNet integration available)
- Requires gateway architecture for private on-premises data access
- Inherits M365 tenant network security

**Ideal for:** Organizations accepting Microsoft-managed SaaS networking model

**Sources:**
- [M365 Copilot Security](https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-ai-security)

---

### Network Isolation Decision Matrix

| Technology | VNet Support | Private Endpoints | Air-Gapped | Gateway Required | Best For |
|------------|-------------|-------------------|------------|------------------|----------|
| **Azure AI Foundry** | ✅ Full | ✅ Yes | ✅ Yes | ❌ No | Zero-trust, air-gapped, sovereign data |
| **Azure AI Agent Service** | ✅ Full | ✅ Yes | ✅ Yes | ❌ No | Managed PaaS with private networking |
| **Copilot Studio** | ⚠️ Gateway-based | ⚠️ Via gateway | ❌ No | ✅ Yes | Managed PaaS with Azure resource access |
| **M365 Agents SDK** | ✅ Self-hosted | ✅ Yes | ✅ Yes | ❌ No | Custom network control |
| **M365 Copilot** | ❌ No | ❌ No | ❌ No | ✅ For on-prem | Managed SaaS only |

---

**Next:** [Feature Comparison](feature-comparison.md) - Side-by-side capability matrices
