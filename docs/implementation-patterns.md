---
layout: default
title: Implementation Patterns
nav_order: 6
description: Proven architecture patterns for Microsoft AI solutions
---

# Common Implementation Patterns

{: .note }
These patterns represent proven approaches for implementing Microsoft AI solutions. Each pattern includes clear guidance on when to use it and when to avoid it.

---

## Pattern 1: Start in Studio, Scale with Azure

**Approach:**
1. **Prototype** in Copilot Studio (declarative agent, Graph Connectors for data)
2. **Validate** use case with business users in Teams or M365 Copilot
3. **Identify scaling needs** (custom orchestration, multi-agent, enterprise data sources)
4. **Migrate orchestration** to Azure AI Agent Service or Azure AI Foundry
5. **Keep M365 surface** using M365 Agents SDK to deploy back to M365 channels

**Best For:**
- Fast time-to-market with business validation
- Makers starting projects that may need developer scale
- Organizations unsure of final complexity requirements

**When NOT to Use:**
- Complex orchestration known upfront
- Multi-agent systems required from day 1
- Heavy Azure-native data integration needed immediately

**Sources:**
- [Copilot Studio to Azure AI Foundry Migration](https://learn.microsoft.com/en-us/azure/ai-services/agents/how-to/copilot-studio-migration) (Updated: 2024-10-15)

**Status:** Recommended pattern for POCs
**Confidence Level:** High (official Microsoft guidance)

---

## Pattern 2: Pro-Code First, Surface in Copilot

**Approach:**
1. **Build custom agent** in Azure AI Foundry (Semantic Kernel, Agent Framework, or LangChain)
2. **Develop with Azure AI Search** for RAG, Azure OpenAI for LLM
3. **Deploy as Azure service** (Container Apps, App Service, or Kubernetes)
4. **Expose as M365 Copilot extension** using API plugins or custom engine agent
5. **(Optional) Surface in Teams** via M365 Agents SDK

**Best For:**
- Developers with existing Azure expertise
- Complex requirements (multi-agent, custom models, specialized orchestration)
- Need full control over infrastructure and deployment
- Scenarios requiring Azure-native data integration

**Sources:**
- [Azure AI Foundry Agent Development](https://learn.microsoft.com/en-us/azure/ai-services/agents/overview) (Updated: 2024-10-25)
- [Custom Engine Agents for M365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-custom-engine-agent) (Updated: 2024-10-18)

**Status:** Recommended for enterprise scenarios
**Confidence Level:** High (documented architecture pattern)

---

## Pattern 3: Graph-Centric Grounding

**Approach:**
1. **Index external data** with Graph Connectors (SharePoint, external systems)
2. **Deploy declarative agent** (Copilot Studio or M365 Agents Toolkit)
3. **Configure instructions** to reference indexed knowledge
4. **Add API plugins** for transactional actions (optional)
5. **Publish to M365 Copilot** for organization-wide discovery

**Best For:**
- Knowledge retrieval scenarios (FAQs, policy lookup, document search)
- M365-centric organizations
- Read-only data grounding (no transactional writes)
- Fast deployment with minimal code

**Sources:**
- [Microsoft Graph Connectors Overview](https://learn.microsoft.com/en-us/graph/connecting-external-content-connectors-overview) (Updated: 2024-09-20)
- [Declarative Agents with Graph Connectors](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-declarative-agents) (Updated: 2024-10-15)

**Status:** Recommended for M365 knowledge scenarios
**Confidence Level:** High (native M365 integration)

---

## Pattern 4: Multi-Channel Custom Engine Agent with M365 Agents SDK

**Approach:**
1. **Choose orchestration framework:**
   - **Option A (Microsoft Agent Framework):** Use for multi-agent orchestration patterns (Sequential, Concurrent, Handoff, Magentic)
   - **Option B (Semantic Kernel):** Use for custom agent logic, memory management, planning
   - **Option C (LangChain):** Use for ecosystem integrations, community tools, Python-first development
2. **Develop agent** with M365 Agents SDK Toolkit in VS Code
3. **Integrate Azure services:**
   - Azure OpenAI for LLM
   - Azure AI Search for RAG (or Graph Connectors for M365 data)
   - Azure Key Vault for secrets
   - Application Insights for telemetry
4. **Deploy to Azure Bot Service** (enables 10+ channels: Teams, Slack, web chat, etc.)
5. **Publish to M365 Copilot** (optional, for organization-wide discovery)
6. **Configure governance:** Entra ID authentication, Azure RBAC, monitoring

**Integration Options:**
- **Semantic Kernel:** Full control over orchestration, memory, planning, function calling
- **Agent Framework:** Pre-built orchestration patterns, multi-agent delegation, state management
- **LangChain:** Python ecosystem, LangGraph for complex workflows, LangSmith for observability

**Best For:**
- Developers requiring full control over orchestration
- Multi-channel deployment (beyond just Teams or M365 Copilot)
- Complex agent logic with custom reasoning
- Azure-native data and service integration
- Organizations with existing Bot Framework investments

**When NOT to Use:**
- Simple Q&A scenarios (use declarative agents instead)
- Makers without coding skills (use Copilot Studio)
- Tight timeline with limited developer resources

**Sources:**
- [M365 Agents SDK Overview](https://learn.microsoft.com/en-us/microsoft-365/dev/m365-agents-sdk/overview) (Updated: 2024-10-22)
- [Microsoft Agent Framework](https://learn.microsoft.com/en-us/azure/ai-services/agents/concepts/agent-framework) (Updated: 2024-10-20)
- [Semantic Kernel Documentation](https://learn.microsoft.com/en-us/semantic-kernel/overview/) (Updated: 2024-10-18)
- [LangChain Integration with Azure](https://learn.microsoft.com/en-us/azure/developer/python/get-started-app-chat-template?tabs=github-codespaces) (Updated: 2024-10-10)

**Status:** Recommended for enterprise custom agents
**Confidence Level:** High (all components GA)

---

## Pattern 5: Workflow Orchestration with Agent Framework

**Approach:**
1. **Identify workflow patterns** needed:
   - **Sequential:** Agents execute in order (Agent A → Agent B → Agent C)
   - **Concurrent:** Agents execute in parallel, results merged
   - **Handoff:** Agents transfer context and control dynamically
   - **Magentic:** Agents self-organize based on task requirements
2. **Build agents** using Azure AI Foundry or Azure AI Agent Service
3. **Implement orchestration** with Microsoft Agent Framework
4. **Deploy orchestrator** to Azure (Container Apps, AKS, or App Service)
5. **Surface results** in M365 Copilot, Teams, or custom apps

**Best For:**
- Multi-agent systems with clear delegation patterns
- Workflows requiring parallel execution
- Scenarios with specialized agents (e.g., Research Agent, Writing Agent, Review Agent)
- Organizations needing managed multi-agent infrastructure

**When NOT to Use:**
- Single-agent scenarios
- Simple sequential tasks (use Power Automate or Logic Apps instead)
- Low-code requirements (use Copilot Studio multi-agent)

**Sources:**
- [Agent Framework Orchestration Patterns](https://learn.microsoft.com/en-us/azure/ai-services/agents/concepts/agent-framework) (Updated: 2024-10-20)
- [Azure AI Agent Service Multi-Agent Systems](https://learn.microsoft.com/en-us/azure/ai-services/agents/how-to/multi-agent) (Updated: 2024-10-28)

**Status:** Recommended for complex multi-agent scenarios
**Confidence Level:** High (Agent Framework GA, Azure AI Agent Service Preview)

---

## Pattern Selection Guide

| **Pattern** | **Time to Market** | **Complexity** | **Control Level** | **Best User Experience** |
|-------------|-------------------|----------------|-------------------|--------------------------|
| **Pattern 1 (Studio → Azure)** | Fast (days to weeks) | Start Simple → Scale Complex | Low → High | M365 Copilot, Teams |
| **Pattern 2 (Pro-Code First)** | Moderate (weeks to months) | High | Full | M365 Copilot, Custom Apps |
| **Pattern 3 (Graph-Centric)** | Fast (days) | Low | Medium | M365 Copilot (native) |
| **Pattern 4 (Multi-Channel SDK)** | Moderate (weeks) | High | Full | 10+ channels |
| **Pattern 5 (Agent Framework)** | Moderate (weeks to months) | Very High | Full | Multi-agent workflows |

---

## Pattern Decision Tree

**Start Here:**

1. **Do you need multi-agent orchestration?**
   - Yes → **Pattern 5** (Agent Framework)
   - No → Continue to question 2

2. **Is M365 Copilot the primary user experience?**
   - Yes → **Pattern 3** (Graph-Centric, if read-only) or **Pattern 1** (if actions needed)
   - No → Continue to question 3

3. **Do you need custom orchestration control?**
   - Yes → **Pattern 4** (Multi-Channel SDK) or **Pattern 2** (Pro-Code First)
   - No → **Pattern 1** (Studio → Azure)

4. **Do you have developers available?**
   - Yes → **Pattern 2** or **Pattern 4**
   - No → **Pattern 1** (low-code path)

---

{: .note-title }
> Related Resources
>
> - For technology comparison tables, see [Quick Reference](quick-reference.html)
> - For real-world applications of these patterns, see [Scenarios](scenarios.html)
> - For evaluation criteria, see [Evaluation Criteria](evaluation-criteria.html)
