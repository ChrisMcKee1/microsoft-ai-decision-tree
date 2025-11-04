---
layout: default
title: Quick Reference
nav_order: 10
description: "Fast lookup table for Microsoft AI technologies"
---

# Quick Reference: Technology by Need

{: .note }
This page provides fast-lookup tables for common scenarios. For detailed decision logic, see the [Decision Framework](decision-framework.html).

---

## Technology by User Experience

| **Where Users Interact** | **Recommended Technologies** | **Use When** |
|---------------------------|------------------------------|--------------|
| **Microsoft 365 Apps** | M365 Copilot + Declarative Agents, Graph Connectors | Users primarily in Word, Excel, Teams, Outlook |
| **Microsoft Teams Only** | Copilot Studio, M365 Agents SDK | Teams-centric communication and collaboration |
| **Custom Web/Mobile App** | Azure AI Foundry, Azure AI Agent Service | Building standalone applications |
| **Multiple Channels** | M365 Agents SDK, Azure Bot Service | Need consistent experience across 10+ channels |
| **Power Platform** | Copilot Studio, AI Builder | Integrated with Power Apps/Power Automate |
| **Enterprise Workflows** | Azure Logic Apps AI Agents (Preview), MCP Server | Workflow automation with AI capabilities |
| **Developer Tools** | GitHub Copilot Extensions | IDE and development workflow integration |

**Sources:**
- [M365 Copilot Extensibility](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/) (Updated: 2024-10-10)
- [Azure AI Foundry Scenarios](https://learn.microsoft.com/en-us/azure/ai-services/agents/overview) (Updated: 2024-10-25)

**Confidence Level:** High (all technologies GA except Logic Apps AI Agents Preview)

---

## Agent Development Approach Comparison

| **Approach** | **Declarative Agents** | **Custom Engine Agents** |
|--------------|------------------------|--------------------------|
| **Definition** | Pre-built orchestration; configure instructions, knowledge, actions | Bring your own orchestrator (Agent Framework Preview recommended, LangChain third-party) |
| **Best For** | Simple → Moderate complexity; fast time-to-market | Complex workflows; multi-agent systems; custom reasoning |
| **Development Model** | Low-code (Copilot Studio) or Pro-code (M365 Agents Toolkit) | Pro-code only; full control over logic |
| **Orchestration** | Microsoft-managed orchestration (GPT-based) | You control orchestration framework and model selection |
| **M365 Integration** | Native M365 Copilot integration | Can integrate via M365 Agents SDK |
| **Typical Timeline** | Days to weeks | Weeks to months |
| **Skill Level** | Makers (low-code) or Developers (pro-code) | Developers required |

**Sources:**
- [Declarative Agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-declarative-agents) (Updated: 2024-10-15)
- [Custom Engine Agents Overview](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-custom-engine-agent) (Updated: 2024-10-18)

**Confidence Level:** High (official Microsoft guidance)

---

## Custom Engine Agent Tool Comparison

| **Tool** | **Copilot Studio** | **Teams AI Library** | **M365 Agents SDK** |
|----------|---------------------|----------------------|---------------------|
| **Primary Use Case** | Low-code custom engine agents | Bot Framework migration path | Multi-channel pro-code agents |
| **Orchestration Options** | Agent Framework Preview recommended, LangChain third-party | Teams AI Library framework | Agent Framework Preview recommended, LangChain third-party |
| **Deployment Channels** | Teams, M365 Copilot | Teams-focused | 10+ channels (Teams, Slack, web chat, etc.) |
| **Developer Experience** | Visual designer + code | Code-first | Code-first with Toolkit in VS Code |
| **Target Audience** | Makers and developers | Bot Framework developers | Professional developers |
| **Licensing Model** | Per-user subscription | Included with M365 | Included with Azure Bot Service |
| **Status** | GA | GA | GA |

**Sources:**
- [Copilot Studio Custom Engine Agents](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-custom-engine-agent) (Updated: 2024-10-18)
- [Teams AI Library Overview](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/teams-conversational-ai/teams-conversation-ai-overview) (Updated: 2024-07-31)
- [M365 Agents SDK](https://learn.microsoft.com/en-us/microsoft-365/dev/m365-agents-sdk/overview) (Updated: 2024-10-22)

**Confidence Level:** High (all GA, official Microsoft documentation)

---

## Data Grounding Pattern by Source

| **Data Source Type** | **Recommended Approach** | **Technologies** |
|----------------------|--------------------------|------------------|
| **SharePoint/OneDrive** | Graph Connectors | Microsoft Graph Connectors SDK, Copilot Studio connectors |
| **External Structured Data** | Graph Connectors or Azure AI Search | Graph Connectors (M365-centric) or Azure AI Search (Azure-native) |
| **Unstructured Documents** | Vector search with chunking | Azure AI Search, Azure OpenAI Embeddings |
| **Real-Time Transactional Data** | API-based grounding | API Plugins, Function Calling |
| **Multimodal Content** | Azure AI Content Understanding (Preview) | Process documents, images, audio, video with reasoning |
| **Database Vectors** | AI-capable databases | Cosmos DB (GA), PostgreSQL (GA), SQL Server 2025 (Preview) |
| **Microsoft Fabric Platform** | Direct data access | Lakehouse (Delta tables), Warehouse (T-SQL), OneLake (ADLS Gen2 APIs), SQL analytics endpoint |
| **Microsoft Fabric via Agent** | Conversational data layer | Fabric Data Agents (Preview) with Copilot Studio or Azure AI Agent Service |

**Sources:**
- [Microsoft Graph Connectors](https://learn.microsoft.com/en-us/graph/connecting-external-content-connectors-overview) (Updated: 2024-09-20)
- [Azure AI Search for RAG](https://learn.microsoft.com/en-us/azure/search/retrieval-augmented-generation-overview) (Updated: 2024-10-12)
- [Azure AI Content Understanding](https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/overview) (Updated: 2024-10-28)
- [Microsoft Fabric Platform](https://learn.microsoft.com/en-us/fabric/fundamentals/microsoft-fabric-overview) (Updated: 2025-11-03)
- [Fabric AI Foundry Integration](https://learn.microsoft.com/en-us/azure/ai-foundry/faq) (Updated: 2025-11-03)

**Confidence Level:** High for GA technologies, Medium for Preview (Fabric Data Agents, Content Understanding)

---

## Memory & Analytics by Technology

{: .note }
**Common Customer Confusion**: Grounding (RAG) ≠ Memory ≠ Analytics

| Technology | 📋 Grounding (RAG) | 💾 Memory / Thread Storage | 📊 Analytics / Transcripts | Admin Access | Retention Control |
|------------|-------------------|------------------------------|----------------------------|--------------|-------------------|
| **M365 Copilot** | ✅ M365 content per request | ❌ NO per-user memory extractable by admins | ⚠️ Limited (Copilot activity history) | ⚠️ Purview-governed (not arbitrary reading) | ✅ Microsoft Purview policies |
| **Copilot Studio** | ✅ M365 data, Dataverse, connectors | ⚠️ Dataverse variables (memory-like persistence, tenant data) | ✅ Full (sessions, handoffs, resolution rates, transcripts) | ✅ Admins can view/download transcripts | ✅ Configurable (default 30 days, bulk delete jobs) |
| **Azure AI Agent Service** | ✅ Azure AI Search, Cosmos DB, Fabric, tools | ✅ BYO thread storage (customer owns Cosmos DB or Microsoft-managed) | ⚠️ Custom (Azure Monitor metrics, OpenTelemetry) | ✅ Customer controls RBAC | ✅ Customer defines (delete via API) |
| **M365 Agents SDK** | ✅ Custom (developer implements) | ⚠️ Custom (developer implements thread storage) | ⚠️ Custom (Application Insights, custom logging) | ⚠️ Custom (developer implements) | ⚠️ Custom (developer implements) |

**Key Compliance Questions:**
- **Where is conversation history stored?** → M365 Copilot (user mailbox), Copilot Studio (Dataverse), Agent Service (customer Cosmos DB), SDK (custom)
- **How long is it retained?** → M365 Copilot (Purview policies), Copilot Studio (30 days default), Agent Service (customer defines), SDK (custom)
- **Who can query chat logs?** → M365 Copilot (eDiscovery only), Copilot Studio (admins with Transcript Viewer role), Agent Service (customer RBAC), SDK (custom)
- **Can we scrub PII?** → Agent Service (customer responsible), Studio (admin deletes transcripts), M365 Copilot (user deletes activity history)

**Sources:**
- [M365 Copilot Privacy](https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-privacy) (Updated: 2024-10-15)
- [Copilot Studio Transcript Controls](https://learn.microsoft.com/en-us/microsoft-copilot-studio/admin-transcript-controls) (Updated: 2024-09-25)
- [Cosmos DB Agent Service Integration](https://learn.microsoft.com/en-us/azure/cosmos-db/gen-ai/azure-agent-service) (Updated: 2024-10-20)

**Confidence Level:** High (all technologies GA)

---

## Orchestration Complexity Decision Matrix

| **Complexity Level** | **Characteristics** | **Recommended Technologies** |
|----------------------|---------------------|------------------------------|
| **Simple (Q&A)** | Single-turn conversations, basic RAG | Declarative Agents (Copilot Studio or M365 Agents Toolkit) |
| **Moderate (Task Execution)** | Multi-turn, 1-5 actions, simple branching | Declarative Agents with API plugins, Azure AI Agent Service |
| **Complex (Workflows)** | Sequential workflows, conditional logic | Declarative Agents + Power Automate, Agent Framework workflows |
| **Advanced (Multi-Agent)** | Agent-to-agent delegation, parallel execution | Copilot Studio multi-agent, Azure AI Agent Service, Agent Framework |
| **Expert (Custom Reasoning)** | Custom orchestration logic, model selection | Custom Engine Agents (Agent Framework Preview recommended, LangChain third-party) |

**Sources:**
- [Agent Framework Orchestration Patterns](https://learn.microsoft.com/en-us/azure/ai-services/agents/concepts/agent-framework) (Updated: 2024-10-20)
- [Copilot Studio Multi-Agent Scenarios](https://learn.microsoft.com/en-us/microsoft-copilot-studio/copilot-ai-plugins) (Updated: 2024-10-05)

**Confidence Level:** High (official patterns documented)

---

## Budget & Timeline Quick Guide

| **Scenario** | **Fastest Path** | **Most Cost-Effective (Long-Term)** |
|--------------|------------------|-------------------------------------|
| **Extend M365 Copilot (Knowledge Only)** | Graph Connectors (days) | Graph Connectors (no additional cost) |
| **Extend M365 Copilot (Knowledge + Actions)** | Declarative Agent (Copilot Studio, 1-2 weeks) | Declarative Agent (M365 Agents Toolkit, 2-4 weeks) |
| **Custom Multi-Channel Agent** | M365 Agents SDK with templates (2-4 weeks) | Azure AI Foundry (consumption-based, 4-8 weeks) |
| **Multi-Agent Orchestration** | Copilot Studio (low-code, 2-4 weeks) | Azure AI Agent Service (managed, 4-8 weeks) |
| **Enterprise Workflow Automation** | Azure Logic Apps AI Agents Preview (1-2 weeks) | Azure AI Foundry + Agent Framework (4-8 weeks) |

**Key Budget Considerations:**
- **M365-Centric:** Per-user licensing (Copilot Studio, M365 Copilot)
- **Azure-Native:** Consumption-based (Azure OpenAI tokens, AI Search queries, compute)
- **Hybrid:** Mix of per-user and consumption models

**Sources:**
- [Copilot Studio Pricing](https://www.microsoft.com/en-us/microsoft-copilot/microsoft-copilot-studio#Plans) (Updated: 2024-10-01)
- [Azure AI Services Pricing](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/) (Updated: 2024-10-15)

**Confidence Level:** Medium (pricing models subject to change)

---

## Governance Decision Quick Reference

| **Requirement** | **M365 Trust Boundary** | **Azure Workload Boundary** |
|-----------------|-------------------------|------------------------------|
| **Data Residency** | M365 tenant region | Azure region selection |
| **Identity Management** | Entra ID (automatic) | Entra ID + Azure RBAC |
| **Approval Workflows** | M365 admin center (Integrated Apps) | Azure custom workflows |
| **Audit Logging** | Purview + M365 audit logs | Azure Monitor + Log Analytics |
| **Data Classification** | Purview DLP policies | Azure Policy + custom tagging |
| **Deployment Control** | IT admin approval (tenant-wide settings) | Azure DevOps, CI/CD pipelines |

**Best For:**
- **M365 Trust Boundary:** Organizations with strong M365 governance already in place
- **Azure Workload Boundary:** Organizations requiring granular control, custom policies, or Azure-native compliance

**Sources:**
- [M365 Copilot Data Security](https://learn.microsoft.com/en-us/microsoft-365-copilot/microsoft-365-copilot-privacy) (Updated: 2024-09-25)
- [Azure AI Services Compliance](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/security) (Updated: 2024-10-10)

**Confidence Level:** High (official Microsoft compliance documentation)

---

{: .note-title }
> Quick Navigation
>
> - For decision logic behind these recommendations, see [Decision Framework](decision-framework.html)
> - For detailed architecture patterns, see [Implementation Patterns](implementation-patterns.html)
> - For real-world examples, see [Scenarios](scenarios.html)
