---
layout: default
title: Implementation Patterns
nav_order: 7
description: "Common patterns and best practices for implementing Microsoft AI solutions"
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
1. **Build custom agent** in Azure AI Foundry (Agent Framework recommended, LangChain third-party alternative)
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
   - **Agent Framework (Preview/Experimental - Recommended):** Microsoft's investment direction; multi-agent orchestration (Sequential, Concurrent, Handoff, Magentic); checkpointing, workflows, consolidates SK + AutoGen
   - **LangChain (Third-party alternative):** Ecosystem integrations, community tools, Python-first development
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
- **Agent Framework (Preview/Experimental - Recommended):** Microsoft's orchestration consolidation (SK + AutoGen); multi-agent workflows, checkpointing, executor/edge patterns, sequential/concurrent/handoff/magentic orchestration
- **LangChain (Third-party alternative):** Python ecosystem, LangGraph for complex workflows, LangSmith for observability

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

## Pattern 6: Identity & Permissions Architecture

**Approach:**
1. **Determine identity model** required for compliance and audit
2. **Choose authentication pattern** based on scope requirements
3. **Implement least privilege** access controls
4. **Configure audit logging** for identity actions

**Identity Models by Technology:**

| Technology | Identity Model | User-Scoped? | Configuration | Best For |
|------------|----------------|-------------|---------------|----------|
| **M365 Copilot** | Always user identity | ✅ Guaranteed | Zero-config | Zero-config user-scoped |
| **Copilot Studio** | User OR service account | ⚠️ Configurable | Dual auth mode | Flexible auth scenarios |
| **Azure AI Foundry** | API key OR Entra ID | ⚠️ Design choice | Custom RBAC | Custom enterprise design |
| **M365 Agents SDK** | Delegated OR application | ⚠️ Developer implements | Full control | Complete auth control |

**Best For:**
- Regulated industries requiring user attribution
- Audit requirements for "who did what"
- Least privilege access enforcement
- Compliance with SOX, HIPAA, GDPR identity controls

**When NOT to Use:**
- Simple proof-of-concept scenarios
- Internal tools with trusted users
- No audit requirements

---

### M365 Copilot: Always User-Scoped

**Architecture:**
- Architecturally guaranteed: runs with signed-in user's identity
- Graph permissions: inherits user's M365 permissions (SharePoint, Exchange, Teams)
- "It only sees what I can see" = TRUE (zero configuration required)
- Actions attributed to individual users in audit logs

**Configuration:**
- No configuration needed (automatic)
- Purview audit logs capture user identity
- eDiscovery searches show per-user activity

**Ideal for:** Organizations requiring guaranteed user-scoped permissions with zero configuration

**Sources:**
- [M365 Copilot Privacy](https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-privacy) (Updated: 2024-10-15)

---

### Copilot Studio: Dual Authentication Modes

**Architecture:**
- **User authentication mode:** Agent runs with end-user's identity (delegated permissions)
- **Agent author authentication mode:** Agent runs with service account (elevated permissions)

**Critical Design Decision:**
- **User authentication:** Safe for read operations, ensures least privilege
- **Agent authentication:** Required for elevated operations (e.g., create records users can't create)
- ⚠️ **Service accounts can exceed individual user permissions** — critical for compliance review

**Configuration:**
1. Go to agent **Settings → Security → Authentication**
2. Choose:
   - **No authentication:** Anonymous access (public agents)
   - **Authenticate with Microsoft:** User identity (Entra ID)
   - **Manual authentication:** Custom auth (OAuth providers)
3. For actions/connectors:
   - Configure connection reference to use **user's identity** OR **service account**

**Guardrails for Service Account Mode:**
- Document service account permissions in compliance reviews
- Add approval workflows for write operations
- Log all actions with user context (who triggered the agent)
- Use Dataverse audit logs to track service account actions

**Ideal for:** Scenarios requiring both user-scoped reads and elevated writes (e.g., HR bots that read user data but create tickets with elevated permissions)

**Sources:**
- [Copilot Studio Authentication](https://learn.microsoft.com/en-us/microsoft-copilot-studio/configuration-authentication) (Updated: 2024-09-25)
- [Connection References](https://learn.microsoft.com/en-us/microsoft-copilot-studio/configuration-hand-off-omnichannel#connection-references) (Updated: 2024-08-30)

---

### Azure AI Foundry: Entra ID Recommended

**Architecture:**
- **API key authentication:** Bypasses user identity (uses deployment key)
- **Entra ID authentication:** Per-user RBAC (Azure AD principals)
- **Managed identities:** Passwordless authentication for Azure resources

**Recommended Pattern (Entra ID):**
1. **Disable API key authentication** in Azure AI Foundry project settings
2. **Assign Azure RBAC roles** to users/groups:
   - **Azure AI Developer:** Full project access (dev/test)
   - **Azure AI Inference User:** Inference only (production apps)
   - **Cognitive Services OpenAI User:** Azure OpenAI access
3. **Use managed identities** for service-to-service calls
4. **Implement custom claims** in application for fine-grained authorization

**Delegated vs Application Permissions:**
- **Delegated permissions (user-scoped):** App acts on behalf of signed-in user
- **Application permissions (service principal):** App acts with tenant-wide scope
- For agent scenarios: **Use delegated** when possible for least privilege

**Audit Logging:**
- Azure Monitor logs show principal ID (user or managed identity)
- Use Azure Policy to enforce "no API keys" governance

**Ideal for:** Organizations requiring custom auth patterns with explicit design (delegated for user-scoped, application for automation)

**Sources:**
- [Azure AI Foundry RBAC](https://learn.microsoft.com/en-us/azure/ai-foundry/how-to/rbac-ai-foundry) (Updated: 2024-10-20)
- [Managed Identities](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/managed-identity) (Updated: 2024-09-15)

---

### M365 Agents SDK: Custom Design

**Architecture:**
- Full developer responsibility for authentication design
- Supports any OAuth 2.0 provider via Microsoft Authentication Library (MSAL)

**Common Patterns:**

**Pattern A: Delegated Permissions (User-Scoped)**
```typescript
// User signs in, agent acts on their behalf
const msalConfig = {
  auth: {
    clientId: process.env.AAD_APP_CLIENT_ID,
    authority: `https://login.microsoftonline.com/${process.env.AAD_APP_TENANT_ID}`,
  }
};

// Token acquired with user's permissions
const tokenResponse = await msalClient.acquireTokenSilent({
  scopes: ["https://graph.microsoft.com/.default"],
  account: userAccount
});
```

**Pattern B: Application Permissions (Service Principal)**
```typescript
// Agent acts with tenant-wide scope (use cautiously)
const credential = new ClientSecretCredential(
  tenantId,
  clientId,
  clientSecret
);

// Service principal with application permissions
const token = await credential.getToken("https://graph.microsoft.com/.default");
```

**Guardrails for Custom Design:**
- **Document auth architecture** in compliance documentation
- **Use delegated permissions** when possible (least privilege)
- **Implement custom audit logging** (log user context, actions taken, permissions used)
- **Add approval workflows** for sensitive operations
- **Rotate secrets** regularly if using client secrets (prefer managed identities)

**Ideal for:** Organizations requiring complete auth control with documented architecture

**Sources:**
- [M365 Agents SDK Authentication](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/authentication) (Updated: 2024-10-22)
- [MSAL Overview](https://learn.microsoft.com/en-us/entra/identity-platform/msal-overview) (Updated: 2024-09-10)

---

### Identity Architecture Decision Matrix

| Requirement | M365 Copilot | Copilot Studio | Azure AI Foundry | M365 Agents SDK |
|-------------|--------------|----------------|------------------|-----------------|
| **Zero-config user-scoped** | ✅ Built-in | ⚠️ Configure | ❌ Design required | ❌ Design required |
| **Service account mode** | ❌ Not supported | ✅ Yes | ✅ Yes (app perms) | ✅ Yes (custom) |
| **Audit logging** | ✅ Purview automatic | ✅ Dataverse logs | ⚠️ Azure Monitor | ⚠️ Custom logging |
| **Least privilege enforcement** | ✅ Guaranteed | ⚠️ Design choice | ⚠️ Design choice | ⚠️ Design choice |
| **Compliance review effort** | Low (automatic) | Medium (document modes) | High (custom RBAC) | High (custom design) |

---

## Pattern 7: Action Safety Design Patterns

**Approach:**
1. **Classify actions by risk** (read-only, write, destructive)
2. **Implement approval workflows** for high-risk actions
3. **Add action boundaries** (allowed vs forbidden operations)
4. **Enable tracing** for audit reconstruction

**Action Risk Classification:**

| Risk Level | Examples | Approval Required | Recommended Pattern |
|------------|----------|-------------------|---------------------|
| **Low (Read)** | Search, lookup, report generation | No | Allow automatically |
| **Medium (Write)** | Create record, update status, send notification | Optional | Consider approval for sensitive data |
| **High (Destructive)** | Delete, disable resource, approve spend | Yes | Always require human-in-the-loop |

**Best For:**
- Autonomous agents with tool calling
- Enterprise scenarios with compliance requirements
- Agents that can trigger workflows or APIs
- Financial, HR, or security operations

**When NOT to Use:**
- Read-only agents (no actions)
- Simple Q&A chatbots
- Prototype/POC scenarios

---

### Guardrail Best Practices by Technology

#### M365 Copilot
- ✅ **User-in-the-loop always** (drafts content, user must execute)
- ✅ **Content moderation + prompt injection defenses** built-in
- **No additional guardrails needed** (safest by design)

**Sources:**
- [M365 Copilot Security](https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-ai-security) (Updated: 2024-10-10)

---

#### Copilot Studio
- ⚠️ **Actions can execute** (Power Automate flows, custom connectors)
- ✅ **Content moderation** blocks malicious prompts

**Recommended Guardrails:**
1. Add **"Start and wait for an approval"** action in Power Automate flows before destructive operations
2. Use **condition checks** to validate parameters (e.g., "If amount > $10,000, require approval")
3. Configure **rate limiting** at environment level
4. Enable **Dataverse audit logs** to track action execution
5. Design agent to **request approval** before executing destructive actions (e.g., "Before I delete this resource, do you approve?")

**Sources:**
- [Copilot Studio Actions](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-business-applications) (Updated: 2024-10-05)

---

#### Azure AI Foundry / Agent Service
- ⚠️ **Tool calling with autonomous planning loops** (multi-step reasoning)
- ✅ **Content safety** via Azure AI Content Safety service

**Recommended Guardrails:**
1. Implement **human-in-the-loop middleware** for high-risk tools
2. Enable **OpenTelemetry tracing** to log and review action chains
3. Use **Azure Policy** to restrict function apps/Logic Apps the agent can call
4. Implement **action boundaries** in tool definitions (e.g., mark certain tools as "approval-required")
5. Add **budget alerts** and **rate limiting** at API Management layer

**Sources:**
- [Azure AI Agent Service Transparency Note](https://learn.microsoft.com/en-us/azure/ai-foundry/responsible-ai/agents/transparency-note) (Updated: 2024-10-15)

---

#### M365 Agents SDK
- ⚠️ **Full developer responsibility** (no built-in action safety)

**Recommended Guardrails:**
1. Implement **custom approval middleware** to intercept action requests
2. Classify actions by risk level in code (read/write/destructive)
3. Add **custom telemetry** (Application Insights) to log all actions with user context
4. Implement **action allowlist** (deny-by-default for destructive operations)
5. Use **Azure Key Vault** for sensitive credentials (never hardcode)

**Sources:**
- [M365 Agents SDK Security](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/security) (Updated: 2024-10-22)

---

### Action Safety Architecture Patterns

**Pattern A: Approval Workflow (Power Automate)**
```
User Request → Agent Plans Action → [If Destructive] → Trigger Approval Flow → Manager Approves/Rejects → Execute or Cancel
```

**Pattern B: Human-in-the-Loop Middleware (Custom Code)**
```typescript
async function executeToolWithApproval(toolName: string, params: any) {
  if (isDestructive(toolName)) {
    const approval = await requestHumanApproval(toolName, params);
    if (!approval.approved) {
      return { error: "Action rejected by human reviewer" };
    }
  }
  return await executeTool(toolName, params);
}
```

**Pattern C: Read-Only Agent with Write Actions Delegated**
```
Agent → Generates plan → Presents to user → User clicks "Execute" → Authenticated API call (user's identity)
```

---

### Action Safety Decision Matrix

| Technology | Built-in Safety | Approval Mechanism | Tracing | Best For |
|------------|-----------------|-------------------|---------|----------|
| **M365 Copilot** | ✅ User-in-the-loop always | N/A (drafts only) | Purview logs | Maximum safety |
| **Copilot Studio** | ⚠️ Actions can execute | Power Automate approvals | Dataverse logs | Low-code with approvals |
| **Azure AI Foundry** | ⚠️ Autonomous execution | Custom middleware | OpenTelemetry | Pro-code with tracing |
| **M365 Agents SDK** | ❌ Custom design | Custom implementation | Custom logging | Full custom control |

---

{: .note-title }
> Related Resources
>
> - For technology comparison tables, see [Quick Reference](quick-reference.html)
> - For real-world applications of these patterns, see [Scenarios](scenarios.html)
> - For evaluation criteria, see [Evaluation Criteria](evaluation-criteria.html)

---

**Next:** [Technologies](technologies.md) - Deep dive into technical specifications
