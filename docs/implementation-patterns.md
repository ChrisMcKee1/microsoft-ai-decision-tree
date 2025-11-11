---
layout: default
title: Implementation Patterns
nav_order: 7
description: "Common patterns and best practices for implementing Microsoft AI solutions"
---

{: .note }
These patterns represent proven approaches for implementing Microsoft AI solutions. Each pattern includes clear guidance on when to use it and when to avoid it.

---

## Pattern 1: Start in Studio, Scale with Azure

**Approach:**

1. Launch in **Copilot Studio** to capture instructions, knowledge sources, and connectors with low-code orchestration.[^studio-overview]
2. Publish to the **Microsoft 365 channel** (Teams, Outlook, Copilot Chat) to validate adoption and governance early.[^studio-publish]
3. Add approvals, analytics, and DLP controls through Power Platform admin policies while you refine prompts and topic structure.[^studio-overview]
4. Break down responsibilities into **child** and **connected agents** so specialized copilots can collaborate while you stay in the maker canvas.[^connected-agents]
5. When orchestration or private hosting requirements emerge, keep Copilot Studio as the front door while introducing **Azure AI Agent Service** plus **Agent Framework** workflows, and expose the orchestrator back through Copilot Studio or the Microsoft 365 Agents SDK.[^agentservice-overview][^agent-framework][^integrate-mcs]

**Strengths:**

- Fastest time-to-value for **low/medium complexity** use cases; aligns with makers in the Evaluation Criteria skills matrix.
- Reuses Power Platform connectors and managed capacity instead of standing up Azure infrastructure.
- Built-in analytics, transcript review, and admin approvals support early compliance conversations.
- Connected and child agents let you validate multi-agent responsibilities before handing orchestration to pro-code teams.[^connected-agents]

**Trade-offs:**

- Advanced orchestration, custom routing, or strict VNet isolation still require an Azure landing zone.[^agentservice-overview]
- Connected agents are Preview and require agents to live in the same environment; plan ALM accordingly.[^connected-agents]
- Service-account execution must be reviewed to avoid over-privileged actions (tie back to Pattern 7).
- Consumption is metered per message, so sustained high-volume scenarios should model capacity vs. Azure consumption costs before scaling.

**Signals this fits (Evaluation Criteria crosswalk):**

- Time-to-production measured in **days → weeks**.
- Teams have **makers or mixed maker/dev** skill sets.
- Budget tolerance focused on managed SaaS (Copilot Studio capacity) rather than Azure infrastructure.

**When to pivot:** Move to Pattern 2 or 4 when pro-code teams need sustained control across channels, or Pattern 5 if Agent Framework orchestration becomes the primary investment.

**Sources:**

- [Copilot Studio overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/overview-what-is-copilot-studio)[^studio-overview]
- [Add custom Copilot Studio agents to Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/publish)[^studio-publish]
- [Azure AI Agent Service overview](https://learn.microsoft.com/en-us/azure/ai-foundry/agents/overview)[^agentservice-overview]

**Status:** Recommended pattern for proofs of concept and iterative delivery
**Confidence Level:** High (official Microsoft guidance)

---

## Pattern 2: Pro-Code First, Surface in Copilot

**Approach:**

1. Design and build in **Azure AI Foundry** or Azure AI Agent Service to control model selection, prompt flow evaluations, and custom toolchains.[^agentservice-overview]
2. Implement RAG with Azure AI Search, Cosmos DB, or SQL vector features depending on data gravity.[^feature-comparison]
3. Host the agent in Azure services you already operate (Container Apps, App Service, AKS) so networking, logging, and secrets align with your landing zone standards.[^evaluation-governance]
4. Expose the experience inside Microsoft 365 through API plugins or custom engine agents created with the Microsoft 365 Agents SDK.[^api-plugins][^agentsdk-overview]

**Strengths:**

- Full control over orchestration, latency budgets, and data residency; ideal for **high/very high complexity** use cases in the Evaluation Criteria.
- Reuses existing Azure engineering investments (policy, monitoring, private endpoints).
- Flexible channel reach—web, mobile, Microsoft 365, or bespoke user interfaces—using the Agents SDK as a distribution layer.[^agentsdk-overview]

**Trade-offs:**

- Requires dedicated engineering capacity (pro developers, DevOps) and longer lead time (weeks → months).
- Azure consumption costs accumulate across hosting, vector stores, and observability; financial modeling is required up front.
- Teams must implement Responsible AI controls (content safety, approvals) themselves or integrate Azure services such as AI Content Safety.

**Signals this fits:**

- You already operate an Azure landing zone with security/compliance guardrails.
- Teams have the **pro developer** profile in Evaluation Criteria, including infrastructure ownership.
- Use case demands deterministic orchestration, custom metrics, or hybrid channel support.

**When to pivot:** If the pilot stalls due to skill or budget constraints, return to Pattern 1 to validate scope, or move to Pattern 4 when multi-channel distribution is required but you can partner with product teams for shared orchestration.

**Sources:**

- [Azure AI Agent Service overview](https://learn.microsoft.com/en-us/azure/ai-foundry/agents/overview)[^agentservice-overview]
- [Microsoft AI Feature Comparison](feature-comparison.md)[^feature-comparison]
- [Evaluation Criteria – Governance & Compliance](evaluation-criteria.md#governance--compliance)[^evaluation-governance]
- [API plugins for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-api-plugins)[^api-plugins]
- [Microsoft 365 Agents SDK overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agents-sdk-overview)[^agentsdk-overview]

**Status:** Recommended when enterprise teams lead with Azure-first architecture
**Confidence Level:** High (official Microsoft guidance + internal comparison tables)

---

## Pattern 3: Microsoft 365 Knowledge Grounding

**Approach:**

1. Add SharePoint, OneDrive, and Teams knowledge sources directly in Copilot Studio so the agent grounds answers in tenant-secured content with security trimming.[^knowledge-sharepoint]
2. Configure a **declarative agent** (Copilot Studio or Microsoft 365 Agents Toolkit) that references those knowledge sources and provides conversation starters aligned to business vernacular.[^declarative-agents]
3. Extend coverage with Microsoft Graph connectors when you need external line-of-business or third-party content indexed into Microsoft 365 Search and Copilot experiences.[^graph-connectors]
4. Optionally attach **API plugins** for light actions (create tickets, file requests) while keeping the agent primarily read-oriented.[^api-plugins]
5. Publish to Microsoft 365 Copilot or Teams to meet users where they already work; analytics and governance stay inside Microsoft 365.[^studio-publish]

**Strengths:**

- Safest path for **read-only** experiences; inherits Microsoft 365 identity, compliance, and data loss prevention controls without extra infrastructure.[^knowledge-sharepoint]
- Minimal build effort—aligns with **low complexity / low budget** profiles in Evaluation Criteria while improving search and retrieval outcomes.
- Scales rapidly because indexing, security trimming, and citations are handled by Microsoft 365 knowledge services.

**Trade-offs:**

- Limited to knowledge sources supported by Copilot Studio and Microsoft Graph connectors; large unstructured repositories may require Azure AI Search (Pattern 2).
- Declarative agents rely on prompt engineering rather than custom orchestration; cannot enforce complex workflows without escalating to Patterns 1 or 4.
- Actions via API plugins introduce consent prompts and require ongoing API management.

**Signals this fits:**

- Goal is improved knowledge discovery, policy lookup, or FAQ automation.
- Users will consume the agent inside Microsoft 365 applications.
- Governance stakeholders need confidence that the agent cannot mutate records without explicit approvals.
- Business owners want to keep delivery within the Microsoft 365 licensing boundary before investing in Azure infrastructure.

**When to pivot:** Add Pattern 1 when you need richer Power Platform actions, or Pattern 2 when integrating large non-Microsoft 365 datasets or when RAG precision/latency must be tuned outside Microsoft Search.

**Sources:**

- [Add SharePoint as a knowledge source](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-sharepoint)[^knowledge-sharepoint]
- [Add knowledge sources to declarative agents](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-lite-knowledge)[^knowledge-sources]
- [Microsoft Graph connectors overview](https://learn.microsoft.com/en-us/graph/connecting-external-content-connectors-overview)[^graph-connectors]
- [Declarative agents for Microsoft 365 Copilot overview](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent)[^declarative-agents]
- [API plugins for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-api-plugins)[^api-plugins]
- [Add custom Copilot Studio agents to Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/publish)[^studio-publish]

**Status:** Recommended for M365-centric knowledge scenarios
**Confidence Level:** High (official Microsoft guidance)

---

## Pattern 4: Multi-Channel Custom Engine Agent with M365 Agents SDK

**Approach:**

1. Scaffold a custom engine agent with the **Microsoft 365 Agents Toolkit** in Visual Studio/VS Code so you get channel adapters, debugging playground, and deployment templates out of the box.[^agents-toolkit]
2. Implement orchestration inside the agent container—prefer **Microsoft Agent Framework** (Preview) for multi-agent workflows, or plug in your existing orchestrator through the SDK’s activity pipeline.[^agent-framework][^agentsdk-overview]
3. Connect enterprise knowledge and actions by wiring Azure AI Search, Azure OpenAI, Microsoft Graph connectors, or first-party APIs behind secured tool handlers.[^agentsdk-build]
4. Configure channel reach and authentication using the Agents SDK adapters (Copilot, Teams, custom web, Direct Line) and align identity with Entra ID scopes.[^agentsdk-overview]
5. Deploy the agent to your Azure landing zone (Container Apps, App Service, AKS) and publish through the Agents Toolkit so Microsoft 365 users can discover it in Copilot while other apps call the same endpoint.[^agents-toolkit][^bring-agents]

**Strengths:**

- Full control over orchestration, tooling, telemetry, and hosting—fits **high/very high complexity** profiles in Evaluation Criteria.[^agentsdk-build]
- Single codebase can service Microsoft 365 Copilot, Teams, custom web or mobile clients using built-in channel adapters.[^agents-toolkit]
- Integrates cleanly with existing Azure DevSecOps practices (CI/CD, logging, private networking) and reusable agent components.[^agents-toolkit]

**Trade-offs:**

- Requires pro-code engineering, multi-environment CI/CD, and sustained ownership—time-to-production typically **weeks → months**.[^agentsdk-build]
- Agent Framework capabilities remain Preview; plan for API surface changes and feature flags.[^agent-framework]
- Because you bring your own orchestrator and tooling, you own Responsible AI guardrails (content safety, approvals, auditing) inside the agent container.[^agentsdk-overview]

**Signals this fits:**

- You already run orchestrators or LLM infrastructure in Azure and need to surface them inside Microsoft 365.[^agentsdk-build]
- Product teams need channel-specific behaviors (Teams meetings, custom apps) beyond what Copilot Studio supports.[^agentsdk-overview]
- Security/compliance teams require fine-grained control over networking, secrets, and approvals.[^agents-toolkit]

**When to pivot:** Use Pattern 2 if the experience will remain outside Microsoft 365, or Pattern 1/3 when low-code teams can deliver the scenario faster without custom hosting.

**Sources:**

- [Microsoft 365 Agents SDK overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agents-sdk-overview)[^agentsdk-overview]
- [Build custom engine agents with Microsoft 365 Agents SDK](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/m365-agents-sdk)[^agentsdk-build]
- [Microsoft 365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/developer/overview-m365-agents-toolkit)[^agents-toolkit]
- [Microsoft Agent Framework concepts](https://learn.microsoft.com/en-us/azure/ai-services/agents/concepts/agent-framework)[^agent-framework]
- [Bring your agents into Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/bring-agents-to-copilot)[^bring-agents]

**Status:** Recommended for enterprise-grade, pro-code agents spanning multiple channels
**Confidence Level:** High (Agents SDK GA, Agent Framework Preview)

---

## Pattern 5: Multi-Agent Workflows with Microsoft Agent Framework

**Approach:**

1. Model the orchestration in **Agent Framework Workflows** to get type-safe executors, edges, and validation before anything runs.[^agent-workflows]
2. Stand up specialized agents (Azure AI Agent Service, Azure AI Foundry, or custom ChatClient agents) and register them as workflow executors.[^agent-azure-workflow][^agent-azure-agent]
3. Choose the right orchestration pattern—Sequential, Concurrent, Handoff, Group Chat, or Magentic—and configure routing rules that match each agent’s responsibilities.[^agent-orchestrations]
4. Add reliability primitives like checkpointing, event streaming, and human-in-the-loop gates before hosting the workflow runtime.[^agent-checkpoint]
5. Expose the orchestrator through your preferred surface (M365 Agents SDK, web API, Logic Apps trigger) so downstream channels can invoke the multi-agent workflow.[^agentsdk-overview]

**Strengths:**

- Purpose-built for complex, multi-step collaboration with first-class orchestration patterns.[^agent-orchestrations]
- Strong typing, validation, and checkpointing reduce runtime surprises in long-running or regulated processes.[^agent-workflows][^agent-checkpoint]
- Works with Azure AI Agent Service or persistent Foundry agents, letting you reuse enterprise-grade agents inside coordinated workflows.[^agent-azure-workflow][^agent-azure-agent]

**Trade-offs:**

- Microsoft Agent Framework is still in **Public Preview**; expect API churn and package updates.[^agentframework-overview]
- Advanced orchestration features (for example, Magentic) remain experimental and require tolerance for pre-release quality.[^agent-orchestrations]
- Engineering teams must own hosting, monitoring, and Responsible AI guardrails across all agents in the workflow.[^agent-transparency]

**Signals this fits:**

- A single agent can’t reliably complete the workflow—each task needs a specialized agent or tool chain.[^agent-transparency]
- You need deterministic control over multi-agent routing, sequencing, or human approvals.[^agent-workflows]
- Teams already build in .NET or Python and can maintain preview SDKs.[^agentframework-overview]

**When to pivot:** Stay with Patterns 1–4 when a single agent or low-code orchestration meets the requirement; Agent Framework adds value only once coordination overhead is justified.[^agent-transparency]

**Sources:**

- [Microsoft Agent Framework overview](https://learn.microsoft.com/en-us/agent-framework/overview/agent-framework-overview)[^agentframework-overview]
- [Microsoft Agent Framework Workflows](https://learn.microsoft.com/en-us/agent-framework/user-guide/workflows/overview)[^agent-workflows]
- [Agent Framework orchestration patterns](https://learn.microsoft.com/en-us/agent-framework/user-guide/workflows/orchestrations/overview)[^agent-orchestrations]
- [Checkpointing and resuming workflows](https://learn.microsoft.com/en-us/agent-framework/tutorials/workflows/checkpointing-and-resuming)[^agent-checkpoint]
- [Agents in Workflows tutorial](https://learn.microsoft.com/en-us/agent-framework/tutorials/workflows/agents-in-workflows)[^agent-azure-workflow]
- [Azure AI Foundry Agents integration](https://learn.microsoft.com/en-us/agent-framework/user-guide/agents/agent-types/azure-ai-foundry-agent)[^agent-azure-agent]
- [Azure AI Agent Service transparency note](https://learn.microsoft.com/en-us/azure/ai-foundry/responsible-ai/agents/transparency-note#capabilities)[^agent-transparency]

**Status:** Microsoft Agent Framework (Public Preview); Azure AI Agent Service (GA)
**Confidence Level:** Medium (preview framework + GA runtime)

---

## Pattern Selection Guide

| **Pattern** | **Time to Market** | **Complexity** | **Control Level** | **Best User Experience** |
|-------------|-------------------|----------------|-------------------|--------------------------|
| **(Studio → Azure)** | Fast (days to weeks) | Start Simple → Scale Complex | Low → High | M365 Copilot, Teams |
| **Pattern 2 (Pro-Code First)** | Moderate (weeks to months) | High | Full | M365 Copilot, Custom Apps |
| **Pattern 3 (M365 Knowledge)** | Fast (days) | Low | Medium | M365 Copilot (native) |
| **Pattern 4 (Multi-Channel SDK)** | Moderate (weeks) | High | Full | 10+ channels |
| **Pattern 5 (Agent Framework)** | Moderate (weeks to months) | Very High | Full | Multi-agent workflows |

---

## Pattern Decision Tree

**Start Here:**

1. **Do you need multi-agent orchestration?**
   - Yes → **Pattern 5** (Agent Framework)
   - No → Continue to question 2

2. **Is M365 Copilot the primary user experience?**
   - Yes, knowledge retrieval only → **Pattern 3** (M365 Knowledge)[^pattern3-knowledge]
   - Yes, need declarative actions or low-code workflows → **Pattern 1** (Studio → Azure)[^pattern1-actions]
   - Yes, need custom orchestration or multi-channel pro-code → **Pattern 2** or **Pattern 4** (choose based on control level)[^pattern2-4-procode]
   - No → Continue to question 3

3. **Do you need custom orchestration control?**
   - Yes → **Pattern 4** (Multi-Channel SDK) or **Pattern 2** (Pro-Code First)
   - No → **Pattern 1** (Studio → Azure)

4. **Do you have developers available?**
   - Yes → **Pattern 2** or **Pattern 4**
   - No → **Pattern 1** (low-code path)

[^pattern1-actions]: Microsoft 365 Copilot release notes — August 19, 2025, Microsoft Learn. Updated: 2025-08-19. [https://learn.microsoft.com/en-us/copilot/microsoft-365/release-notes#august-19,-2025](https://learn.microsoft.com/en-us/copilot/microsoft-365/release-notes#august-19,-2025)
[^pattern2-4-procode]: Microsoft 365 Agents SDK overview, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agents-sdk-overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agents-sdk-overview)

---

## Pattern 6: Identity & Permissions Architecture

**Approach:**

1. **Map identity boundaries** for every surface (M365 Copilot, Copilot Studio, Azure AI Foundry, Agents SDK) so you know which services are inherently user-scoped and which require custom design.[^copilot-privacy][^studio-authentication][^foundry-rbac][^agentsdk-auth]
2. **Choose delegated vs application scopes** early, preferring delegated consent for user-driven actions and reserving service principals for automation that cannot run under a user identity.[^agentsdk-permissions][^graph-permissions]
3. **Configure authentication flows** using the native controls for each platform—Copilot Studio manual auth, Azure AI Foundry managed identities, and MSAL providers in the Agents SDK.[^studio-authentication][^foundry-managed-identity][^msal-config]
4. **Enforce least privilege and RBAC** by assigning the minimum Entra ID roles, Graph scopes, and project-level permissions required for the workload; document any elevated service accounts.[^foundry-rbac][^graph-permissions]
5. **Enable centralized auditing** in Microsoft Purview and Dataverse so prompts, responses, and service-account executions are captured for compliance reviews.[^copilot-audit][^studio-audit]

**Strengths:**


**Trade-offs:**


**Signals this fits:**


**When to pivot:** Use Patterns 1–3 for short-lived pilots with trusted users, or pause the rollout if your organization cannot yet operate service principals or Purview-based auditing.


[^copilot-privacy]: Data, privacy, and security for Microsoft 365 Copilot, Microsoft Learn. Retrieved: 2025-01-14. [https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-privacy](https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-privacy)
[^copilot-audit]: Microsoft 365 Copilot reporting options for admins, Microsoft Learn. Retrieved: 2025-01-14. [https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-reports-for-admins](https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-reports-for-admins)
[^studio-authentication]: Configure user authentication in Copilot Studio, Microsoft Learn. Retrieved: 2025-01-14. [https://learn.microsoft.com/en-us/microsoft-copilot-studio/configuration-end-user-authentication](https://learn.microsoft.com/en-us/microsoft-copilot-studio/configuration-end-user-authentication)
[^studio-audit]: Audit Copilot Studio activities in Microsoft Purview, Microsoft Learn. Retrieved: 2025-01-14. [https://learn.microsoft.com/en-us/microsoft-copilot-studio/admin-logging-copilot-studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/admin-logging-copilot-studio)
[^foundry-rbac]: Role-based access control for Azure AI Foundry (hub-focused), Microsoft Learn. Retrieved: 2025-01-14. [https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/hub-rbac-azure-ai-foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/hub-rbac-azure-ai-foundry)
[^foundry-managed-identity]: How to use Azure AI Foundry Agent Service with OpenAPI specified tools — Authenticating with managed identity, Microsoft Learn. Retrieved: 2025-01-14. [https://learn.microsoft.com/en-us/azure/ai-foundry/agents/how-to/tools/openapi-spec#authenticating-with-managed-identity-microsoft-entra-id](https://learn.microsoft.com/en-us/azure/ai-foundry/agents/how-to/tools/openapi-spec#authenticating-with-managed-identity-microsoft-entra-id)
[^agentsdk-auth]: Configure authentication in a .NET agent (Microsoft 365 Agents SDK), Microsoft Learn. Retrieved: 2025-01-14. [https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/microsoft-authentication-library-configuration-options](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/microsoft-authentication-library-configuration-options)
[^msal-config]: Configure authentication in a .NET agent (Microsoft 365 Agents SDK), Microsoft Learn. Retrieved: 2025-01-14. [https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/microsoft-authentication-library-configuration-options](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/microsoft-authentication-library-configuration-options)
[^agentsdk-permissions]: Manage permissions for Microsoft 365 Copilot agents, Microsoft Learn. Retrieved: 2025-01-14. [https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-agents-permissions](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-agents-permissions)
[^graph-permissions]: Overview of Microsoft Graph permissions, Microsoft Learn. Retrieved: 2025-01-14. [https://learn.microsoft.com/en-us/graph/permissions-overview](https://learn.microsoft.com/en-us/graph/permissions-overview)

### Identity Architecture Matrix

| Technology | Default Identity Mode | Service Accounts Supported? | Primary Configuration Controls | Audit Surface |
|------------|----------------------|-----------------------------|--------------------------------|---------------|
| **M365 Copilot** | Always runs as the signed-in user | ❌ No | Tenant privacy & data access posture | Microsoft Purview audit logs[^copilot-audit] |
| **Copilot Studio** | User or service account depending on authentication setting | ✅ Yes (manual auth) | Agent authentication mode + connection references | Microsoft Purview + Dataverse transcripts[^studio-authentication][^studio-audit] |
| **Azure AI Foundry / Agent Service** | Configurable (API key, Entra ID, managed identity) | ✅ Yes | Azure RBAC assignments + managed identity role bindings | Azure Monitor / Diagnostic logs |
| **M365 Agents SDK** | Developer-defined (delegated, app-only, managed identity) | ✅ Yes | MSAL profile configuration + Graph scopes | Custom logging + Purview via channel integration[^msal-config][^agentsdk-permissions] |

---

### Microsoft 365 Copilot: User-Scoped by Design

- Runs entirely under the requesting user’s identity and respects existing SharePoint, Exchange, and Teams permissions—“it only sees what you can see” is an architectural guarantee.[^copilot-privacy]
- All prompts and responses flow into Microsoft Purview audit logs and activity explorer, enabling retention and eDiscovery without extra configuration.[^copilot-audit]
- Best choice when compliance teams require individual attribution with zero additional setup.

---

### Copilot Studio: Configurable Delegated or Service Accounts

- Makers select **Authenticate with Microsoft** for delegated access (Teams channel only) or **Authenticate manually** to wire up Entra ID, federated credentials, or other OAuth providers.[^studio-authentication]
- Connection references decide whether each action uses the caller’s identity or a pre-authorized service account—document every elevated credential and pair destructive flows with approvals.[^studio-authentication]
- Purview auditing of maker and end-user interactions is GA (Jan 2025), and Dataverse conversation tables retain transcripts for 30+ days with configurable retention, giving you a complete audit trail.[^studio-audit]
- Ideal when you need to mix user-scoped reads with selective elevation for enterprise systems (for example, HR ticket creation under a bot account).

---

### Azure AI Foundry & Agent Service: RBAC + Managed Identity First

- Replace static API keys with Microsoft Entra authentication and assign built-in roles (Azure AI User, Azure AI Project Manager, Cognitive Services OpenAI User) to enforce least privilege.[^foundry-rbac]
- Enable the project’s system-assigned managed identity and grant it scoped access (for example, Storage Blob Data Reader) so hosted agents can call downstream services without secrets.[^foundry-managed-identity]
- Use role assignments and diagnostic logging to trace every inference or tool call back to a user principal or managed identity—required for production-grade workloads.
- Suits pro-code teams that already operate Azure landing zones and need fine-grained control.

---

### Microsoft 365 Agents SDK: Bring Your Own Authentication

- The SDK ships MSAL-based providers that can issue access tokens via delegated consent, client credentials, or managed identities; profiles are defined in configuration, not hard-coded.[^msal-config]
- Pair the SDK with Entra ID app registrations that request only the Graph scopes you need, and use the Admin Center’s Permissions tab to review delegated vs application grants.[^agentsdk-permissions][^graph-permissions]
- Implement custom logging (Application Insights, Purview activity events) to record the initiating user, token type, and downstream actions—security teams will expect this evidence.
- Choose this path when you require full control over token exchange, multi-channel adapters, and integration with existing identity middleware.

---

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

#### Pattern A: Approval Workflow (Power Automate)

```text
User Request → Agent Plans Action → [If Destructive] → Trigger Approval Flow → Manager Approves/Rejects → Execute or Cancel
```

#### Pattern B: Human-in-the-Loop Middleware (Custom Code)

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

#### Pattern C: Read-Only Agent with Write Actions Delegated

```text
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

[^studio-overview]: Microsoft Copilot Studio overview, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/microsoft-copilot-studio/overview-what-is-copilot-studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/overview-what-is-copilot-studio)
[^studio-publish]: Add custom Copilot Studio agents to Microsoft 365, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/publish](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/publish)
[^agentservice-overview]: Azure AI Agent Service overview, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/azure/ai-foundry/agents/overview](https://learn.microsoft.com/en-us/azure/ai-foundry/agents/overview)
[^connected-agents]: Add other agents (Preview), Microsoft Copilot Studio documentation. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-add-other-agents](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-add-other-agents)
[^agent-framework]: Microsoft Agent Framework concepts, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/azure/ai-services/agents/concepts/agent-framework](https://learn.microsoft.com/en-us/azure/ai-services/agents/concepts/agent-framework)
[^integrate-mcs]: Integrate with Copilot Studio using the Microsoft 365 Agents SDK, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/integrate-with-mcs](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/integrate-with-mcs)
[^feature-comparison]: See `docs/feature-comparison.md` for the detailed comparison matrices referenced in this pattern.
[^evaluation-governance]: See Governance & Compliance in `docs/evaluation-criteria.md#governance--compliance` for scoring guidance.
[^api-plugins]: API plugins for Microsoft 365 Copilot, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-api-plugins](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-api-plugins)
[^agentsdk-overview]: Microsoft 365 Agents SDK overview, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agents-sdk-overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agents-sdk-overview)
[^agents-toolkit]: Microsoft 365 Agents Toolkit overview, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/microsoft-365/developer/overview-m365-agents-toolkit](https://learn.microsoft.com/en-us/microsoft-365/developer/overview-m365-agents-toolkit)
[^agentsdk-build]: Build custom engine agents with Microsoft 365 Agents SDK, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/m365-agents-sdk](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/m365-agents-sdk)
[^agentframework-overview]: Microsoft Agent Framework overview, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/agent-framework/overview/agent-framework-overview](https://learn.microsoft.com/en-us/agent-framework/overview/agent-framework-overview)
[^agent-workflows]: Microsoft Agent Framework Workflows overview, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/agent-framework/user-guide/workflows/overview](https://learn.microsoft.com/en-us/agent-framework/user-guide/workflows/overview)
[^agent-orchestrations]: Agent Framework orchestration overview, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/agent-framework/user-guide/workflows/orchestrations/overview](https://learn.microsoft.com/en-us/agent-framework/user-guide/workflows/orchestrations/overview)
[^agent-checkpoint]: Checkpointing and resuming workflows, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/agent-framework/tutorials/workflows/checkpointing-and-resuming](https://learn.microsoft.com/en-us/agent-framework/tutorials/workflows/checkpointing-and-resuming)
[^agent-azure-workflow]: Agents in Workflows tutorial, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/agent-framework/tutorials/workflows/agents-in-workflows](https://learn.microsoft.com/en-us/agent-framework/tutorials/workflows/agents-in-workflows)
[^agent-azure-agent]: Azure AI Foundry Agents integration, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/agent-framework/user-guide/agents/agent-types/azure-ai-foundry-agent](https://learn.microsoft.com/en-us/agent-framework/user-guide/agents/agent-types/azure-ai-foundry-agent)
[^agent-transparency]: Azure AI Agent Service transparency note, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/azure/ai-foundry/responsible-ai/agents/transparency-note#capabilities](https://learn.microsoft.com/en-us/azure/ai-foundry/responsible-ai/agents/transparency-note#capabilities)
[^graph-connectors]: Microsoft Graph connectors overview (external data indexing into Microsoft 365), Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/graph/connecting-external-content-connectors-overview](https://learn.microsoft.com/en-us/graph/connecting-external-content-connectors-overview)
[^declarative-agents]: Declarative agents for Microsoft 365 Copilot overview, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent)
[^knowledge-sharepoint]: Add SharePoint as a knowledge source in Copilot Studio, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-sharepoint](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-sharepoint)
[^knowledge-sources]: Add knowledge sources to declarative agents in Microsoft 365 Copilot, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-lite-knowledge](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-lite-knowledge)
[^pattern3-knowledge]: Add SharePoint as a knowledge source in Copilot Studio, Microsoft Learn. Updated: 2025-09-15. [https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-sharepoint](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-sharepoint)
[^bring-agents]: Bring your agents into Microsoft 365 Copilot, Microsoft Learn. Retrieved: 2025-11-11. [https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/bring-agents-to-copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/bring-agents-to-copilot)
