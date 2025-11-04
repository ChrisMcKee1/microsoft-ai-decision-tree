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
**Description:** Low-code to pro-code SaaS platform for building custom agents with managed governance, ALM, and multi-channel deployment. Supports both conversational (reactive) and autonomous (event-triggered) agents. Custom engine agents GA (May 2025), Event Triggers GA (March 2025), BYOM from Azure AI Foundry (Preview), BYOK Azure AI Search (GA).  
**Official Docs:** [Copilot Studio Documentation](https://learn.microsoft.com/en-us/microsoft-copilot-studio/)

**Key Features:**
- Low-code to pro-code agent development
- **Event Triggers (GA March 2025):** Autonomous agents that respond to events without user input (SharePoint, OneDrive, Planner, Recurrence)
- Managed governance and ALM
- Multi-channel deployment (M365, Teams, Web, Mobile)
- BYOK (Bring Your Own Knowledge) - Azure AI Search integration (GA)
- BYOM (Bring Your Own Model) - Azure AI Foundry integration (Preview)
- Pay-as-you-go ($0.01/Copilot Credit) or prepaid packs

**When to use:** Custom agents with managed infrastructure, fast time-to-value, low-code to pro-code flexibility, autonomous event-driven workflows

**Sources:**
- [Event Triggers Overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-triggers-about) (GA March 2025)
- [Copilot Studio Fundamentals](https://learn.microsoft.com/en-us/microsoft-copilot-studio/fundamentals-what-is-copilot-studio)

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

**When to use:** Custom AI applications, full control over models and infrastructure, advanced evaluations

---

### Azure AI Agent Service
**Description:** Managed PaaS for agent orchestration, skills management, and runtime infrastructure within Azure AI Foundry. GA (May 2025). Supports connected agents (multi-agent systems), MCP tools, full RBAC + VNet + BYO storage.  
**Official Docs:** [Azure AI Agent Service](https://learn.microsoft.com/en-us/azure/ai-services/agents/)

**Key Features:**
- Managed agent runtime infrastructure
- Skills/tool calling management
- Memory and state management
- Connected agents (multi-agent systems)
- MCP (Model Context Protocol) tool support
- Full RBAC, VNet, private endpoints

**When to use:** Managed agent orchestration at PaaS layer, scalable agent infrastructure, multi-agent systems

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
