---
layout: default
title: Decision Framework
nav_order: 3
description: "Three-phase decision methodology for selecting Microsoft AI technologies"
---

# Three-Phase Decision Methodology

This framework integrates Microsoft's [Business-Experience-Technology (BXT) Framework](https://learn.microsoft.com/en-us/microsoft-cloud/dev/copilot/isv/business-envisioning), [Cloud Adoption Framework AI Strategy](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/ai/strategy), and [M365 Copilot Extensibility Decision Guidance](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agents-overview).

💡 **See [Visual Framework](visual-framework.md) for workflow diagrams** that illustrate how to apply this framework as an intake process.

---

## Phase 1: Business Impact Assessment (BXT Framework)

Before evaluating technology options, validate the use case through three dimensions. **All three must score medium-high to proceed.**

### 1. Viability (Business)

- ROI beyond general productivity gains?
- Quantifiable cost savings or revenue increase?
- Strategic alignment?
- TCO vs. benefit analysis?

### 2. Desirability (Experience)

- Motivating reason to use over current alternative?
- Solves painful, frequent problem?
- Measurable adoption?
- Natural workflow fit?

### 3. Feasibility (Technology)

- Current team skillsets?
- Hire/train/partner decisions?
- Data accessible & governable?
- Infrastructure and compliance ready?

### Decision Gate

- ❌ **Any dimension scores low** → Revisit use case, defer project, or move to "Research/Incubate" quadrant
- ✅ **All dimensions score medium-high** → Proceed to Phase 2 (Technology Selection)

---

## Phase 2: Technology Groupings (Nine Critical Questions)

Apply these questions **sequentially** after passing the BXT assessment. Each question creates **technology groupings** rather than jumping to specific recommendations. The groupings feed into Phase 3 for final selection.

💡 **Important:** These questions create buckets/categories. Final technology selection happens in **Phase 3** based on scenario-specific criteria (time-to-market, complexity, budget, etc.).

---

### Question 1: User Experience Location

**Where will users interact with the AI?**

**Options:**
- **M365 Apps** (Teams, Outlook, Word, SharePoint) with tenant context
- **Custom/Multi-Channel** (Web, Mobile, WhatsApp, SMS, Email)
- **Both** (M365 + External channels)
- **API/Headless** (Backend services, no UI)

**Resulting Groupings:**
- **M365-Centric Technologies**: M365 Copilot, Copilot Studio (M365 channels), Graph Connectors, Declarative Agents
- **Multi-Channel Technologies**: M365 Agents SDK, Copilot Studio (custom channels), Azure AI Foundry, Logic Apps
- **Hybrid**: Copilot Studio (both M365 + custom), M365 Agents SDK + Azure

💡 **Cross-reference:** See [Scenarios](scenarios.md) for scenario-based examples

---

### Question 2: Build Style & Control Level

**What development approach fits your team and requirements?**

**Options:**
- **Low-Code/Visual** (Business users, makers, rapid deployment)
- **Pro-Code** (Full control, custom orchestration)
- **Hybrid** (Low-code start, scale to pro-code)
- **Enterprise Integration** (Workflow automation + AI)

**Resulting Groupings:**
- **Maker-Accessible**: Copilot Studio, AI Builder, Declarative Agents, Power Platform
- **Developer-Required**: M365 Agents SDK, Azure AI Foundry, Agent Framework, Teams AI Library
- **Integration-Focused**: Azure Logic Apps, Power Automate, Copilot Studio Agent Flows
- **Hybrid Options**: Copilot Studio (low-code → pro-code), Azure AI Foundry + Studio

💡 **Cross-reference:** See [Quick Reference](quick-reference.md) for Agent Development Approach Comparison

---

{: .warning }
> **⚠️ Common Misconception: "Low-Code is Only for Makers, Pro-Code is Only for Developers"**
>
> This is **incorrect** and leads to poor technology choices. Here's the reality:
>
> | Term | What It Actually Means | Who Should Use It |
> |------|------------------------|-------------------|
> | **Low-Code** | Less code to write, visual/declarative approach, managed platform (e.g., Copilot Studio, Power Platform) | **Makers AND Developers** — Use when speed matters and custom orchestration isn't needed |
> | **Pro-Code** | Write code in programming languages (C#, Python, JavaScript), full control, custom orchestration | **Developers only** — Use when you need custom logic beyond low-code capabilities |
>
> **✅ Correct Thinking:**
> - **"We have developers, so we CAN use low-code OR pro-code — let the use case decide"**
> - Low-code is faster for simple/moderate complexity (days/weeks vs months)
> - Pro-code gives full control for complex orchestration needs
>
> **❌ Pitfall to Avoid:**
> - **"We have developers, so we MUST use M365 SDK/Azure AI Foundry"**
> - This wastes time building custom solutions when Copilot Studio (low-code) would suffice
> - Developers should choose the **simplest tool that meets requirements**, not the most complex
>
> **Decision Drivers (in priority order):**
> 1. **Use case complexity** — Simple Q&A vs Custom multi-agent workflows?
> 2. **Time to market** — Days/weeks (low-code) vs Months (pro-code)?
> 3. **Control requirements** — Managed governance OK vs Need custom orchestration?
> 4. **Team skills** — Expands options (devs can use both) vs Limits options (makers use low-code only)

---

### Question 3: Data Grounding Pattern

**How will you ground the AI in organizational knowledge?**

{: .important }
> **Critical Distinction**: Grounding ≠ Memory ≠ Analytics  
> - **📋 Grounding (RAG)**: Just-in-time context retrieval per request (e.g., retrieve SharePoint docs)  
> - **💾 Memory**: Stored conversation history across sessions (e.g., thread storage in Cosmos DB)  
> - **📊 Analytics**: Logging interactions for review (e.g., Copilot Studio transcripts in Dataverse)  
>
> **Technology Behaviors**:  
> - **M365 Copilot**: Grounding only (M365 content per request). NO admin-extractable per-user memory. Limited analytics (Purview-governed retention).  
> - **Copilot Studio**: Grounding + Dataverse memory (variables persist). Full analytics (transcripts for admins, sessions, resolution rates).  
> - **Azure AI Agent Service**: Grounding + BYO thread storage (customer owns Cosmos DB). Custom analytics (Azure Monitor, OpenTelemetry).  
>
> 💡 **Compliance Note**: Legal/audit teams will ask: "Where is conversation history stored? How long? Who can query it?" - Answer varies by technology.

**Options:**
- **M365 Graph** (SharePoint, OneDrive, Teams, third-party via connectors)
- **Azure AI Search** (Large-scale vector + hybrid search)
- **Database** (PostgreSQL pgvector, Cosmos DB, operational data)
- **Multiple Sources** (Hybrid RAG patterns)

**Resulting Groupings:**
- **Graph-Based**: M365 Copilot + Graph Connectors, Copilot Studio with M365 data
- **Vector Search (Document-Centric)**: Azure AI Search + Azure AI Foundry, BYOK to Copilot Studio
- **Vector Search (NoSQL/Global)**: Cosmos DB (IVF, HNSW, DiskANN) + Azure AI Foundry
- **Vector Search (Relational)**: PostgreSQL pgvector + Azure AI Foundry
- **Vector Search (Enterprise SQL)**: SQL Server 2025 VECTOR + Azure AI Foundry
- **Hybrid**: Combine Graph + Azure Search + Cosmos DB/PostgreSQL + Custom connectors

{: .note }
> **📋 Ingestion Pipeline Considerations**
>
> Vector search options require an **ingestion pipeline** (chunking + vectorization):
> - **Azure AI Search**: Use [integrated vectorization](https://learn.microsoft.com/en-us/azure/search/vector-search-integrated-vectorization) (indexer + skillset with Text Split + embedding skills)
> - **Azure AI Content Understanding**: Prebuilt analyzers with [built-in chunking](https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/overview) for multimodal content (docs, images, audio, video)
> - **External Processing**: Chunk and vectorize outside Azure, then push to vector fields
> - **Graph-Based**: No pipeline needed — Graph Connectors handle ingestion automatically

💡 **Cross-reference:** See [Implementation Patterns](implementation-patterns.md) - Pattern 3: Graph-Centric Grounding

---

### Question 4: Orchestration Complexity

**What level of agent orchestration and workflow complexity?**

**Options:**
- **Simple Q&A** (Conversational, light actions, FAQ-style)
- **Workflows** (Multi-step, deterministic processes, checkpointing)
- **Multi-Agent** (Agent collaboration, handoffs, specialized agents)
- **Custom Logic** (Complex decision trees, business rules)

**Resulting Groupings:**
- **Declarative/Simple**: Copilot Studio declarative agents, M365 Copilot built-in agents
- **Workflow-Based**: Microsoft Agent Framework, Azure Logic Apps, Copilot Studio Agent Flows
- **Multi-Agent Systems**: Azure AI Agent Service (connected agents), Copilot Studio (child + connected agents)
- **Custom Orchestration**: M365 Agents SDK + Agent Framework, Azure AI Foundry custom

💡 **Cross-reference:** See [Feature Comparison](feature-comparison.md) - Workflow Orchestration Platform Comparison

---

### Question 5: Compliance & Trust Boundary

**What are your data governance and compliance requirements?**

**Options:**
- **M365 Trust Boundary** (Must stay within M365 tenant, use existing compliance posture)
- **Azure-Native** (Leverage Azure governance, VNet, RBAC, private endpoints)
- **Hybrid** (M365 + Azure with proper security architecture)
- **Cross-Cutting Governance** (Need centralized control across all AI deployments)

**Key Data Boundary Considerations (Critical for Regulated Industries):**

**"Where does my data go?"** — This is often the **first question** for healthcare/FSI/government organizations:

1. **M365 Copilot** → **M365 Tenant Boundary ONLY**
   - Prompts, responses, and data accessed through Microsoft Graph **do NOT leave M365 service boundary**
   - Data is **NOT used to train foundation models**
   - Uses Azure OpenAI (NOT OpenAI public services)
   - Inherits M365 compliance: GDPR, HIPAA, ISO 27001, FedRAMP, EU Data Boundary
   - **Ideal for:** Regulated orgs requiring strict tenant boundary with existing M365 compliance posture

2. **Copilot Studio** → **Power Platform Boundary + External System Inheritance**
   - Core conversational data stays within Power Platform environment geography
   - **⚠️ CRITICAL CAVEAT:** Custom connectors/Power Automate flows calling **external systems inherit that system's compliance posture**
   - **⚠️ CRITICAL CAVEAT:** Web search sends queries to **Bing consumer service** (leaves enterprise boundary, NOT covered by DPA)
   - **Ideal for:** Low-code agent development where Power Platform governance is sufficient and external system calls are acceptable

3. **Azure AI Foundry / Agent Service** → **Governed by YOUR Azure Landing Zone Controls**
   - Region/resource group/subscription selection
   - VNet isolation, private endpoints for ALL resources
   - Customer-managed keys (CMK) optional
   - Azure Policy integration, NSGs, managed identities
   - **Ideal for:** Customers requiring VNet isolation, private endpoints, sovereign data strategies, full Azure Policy governance

**Key Network Isolation Considerations (Critical for Zero-Trust/Air-Gapped Environments):**

**"Can I block public internet access?"** — This is the **second critical question** for air-gapped, zero-trust, or highly regulated environments:

| Technology | VNet Support | Private Endpoints | Air-Gapped | Gateway Required | Best For |
|------------|-------------|-------------------|------------|------------------|----------|
| **Azure AI Foundry / Agent Service** | ✅ Full | ✅ Yes | ✅ Yes | ❌ No | Zero-trust, air-gapped, no public egress |
| **Copilot Studio** | ⚠️ Gateway-based | ⚠️ Via gateway | ❌ No | ✅ Yes | Managed PaaS with Azure resource access |
| **M365 Agents SDK** | ✅ Self-hosted | ✅ Yes | ✅ Yes | ❌ No | Complete network control |
| **M365 Copilot** | ❌ No | ❌ No | ❌ No | ✅ For on-prem | Managed SaaS only |

💡 **See [Network Isolation Details](technologies.md#network-isolation-capabilities)** for architecture specifics, VNet integration patterns, and gateway configurations.

**Key Permissions & Identity Considerations (Critical for Audit & Least Privilege):**

**"Who can the agent act as?"** — This is the **third critical question** for audit, least privilege, and compliance:

| Technology | Identity Model | User-Scoped? | Service Account Mode | Audit Complexity | Best For |
|------------|----------------|-------------|----------------------|------------------|----------|
| **M365 Copilot** | Always user identity | ✅ Guaranteed | ❌ Not supported | Low (automatic) | Zero-config user-scoped |
| **Copilot Studio** | User OR service account | ⚠️ Configurable | ✅ Yes | Medium (document modes) | Flexible auth scenarios |
| **Azure AI Foundry** | API key OR Entra ID | ⚠️ Design choice | ✅ Yes (app perms) | High (custom RBAC) | Custom enterprise design |
| **M365 Agents SDK** | Delegated OR application | ⚠️ Developer implements | ✅ Yes (custom) | High (custom design) | Complete auth control |

**Key Distinctions:**
- **M365 Copilot:** "It only sees what I can see" = TRUE (architecturally guaranteed, zero exceptions)
- **Copilot Studio:** Service accounts can access resources beyond individual user permissions (critical for compliance review)
- **Azure AI Foundry:** Entra ID recommended over API keys (per-user RBAC, Conditional Access, MFA)
- **M365 Agents SDK:** Developer documents auth patterns (delegated for user-scoped, application for tenant-wide automation)

💡 **See [Implementation Patterns - Identity Architecture](implementation-patterns.md#pattern-6-identity--permissions-architecture)** for detailed configuration guidance, code examples, and audit logging strategies.

**Resulting Groupings:**
- **M365 Trust Boundary**: M365 Copilot, Copilot Studio (M365 channels), Graph Connectors
- **Azure-Native**: Azure AI Foundry, Azure AI Agent Service, Azure Logic Apps
- **Hybrid/Flexible**: Copilot Studio (BYOK/BYOM), M365 Agents SDK, API Management AI Gateway
- **Centralized Governance**: Azure API Management (AI Gateway for token limits, chargeback, safety)

💡 **Cross-reference:** See [Evaluation Criteria](evaluation-criteria.md) - Governance Considerations

---

## Question 6: What are your scale and cost requirements?

**Understanding cost models and rate limits is critical: Pilot testing often succeeds, but org-wide rollout can hit throttling or unbounded cost exposure.**

**Key Concepts:**

**1. Cost Predictability (Fixed vs Variable):**

**Fixed/Predictable Spend:**
- **M365 Copilot:** Per-user licensing (predictable monthly cost, no usage spikes)
- **Copilot Studio:** Prepaid capacity packs (fixed monthly spend)
- **Best for:** Internal employees, budgeted deployments, finance-driven organizations

**Variable/Usage-Based Spend:**
- **Azure AI Foundry/Agent Service:** Per-token billing (cost scales with traffic)
- **Copilot Studio:** Pay-as-you-go option (consumption-based)
- **M365 Agents SDK:** Hosting + token costs (requires custom guardrails)
- **Best for:** Customer-facing channels, unpredictable traffic, organizations with cost optimization capability

**2. Rate Limit Architecture (Shared vs Dedicated):**

**Shared Environment Quotas:**
- **Copilot Studio:** Environment-level limits shared across all agents (can throttle at scale)
- **Mitigation:** Purchase capacity packs, enable PAYG, separate high-volume agents into dedicated environments

**Dedicated Deployment Quotas:**
- **Azure AI Foundry:** Per-deployment TPM limits (regional quotas, request increases available)
- **M365 Copilot:** Microsoft-managed scaling (no user-facing throttling)
- **M365 Agents SDK:** Custom auto-scaling controls (customer designs rate limiting)

**3. Internal vs External Use:**

**Internal (Employees):**
- M365 Copilot ideal (per-user licensing matches use case)
- Copilot Studio suitable (environment quotas manageable)

**External (Customers/Public):**
- Azure AI Foundry recommended (with guardrails: intent classification, TPM limits, budget alerts)
- M365 Agents SDK suitable (custom rate limiting)
- M365 Copilot NOT designed for external use
- Copilot Studio requires capacity planning for high-volume public scenarios

**Resulting Groupings:**
- **Predictable Spend:** M365 Copilot (per-user), Copilot Studio (prepaid)
- **Variable Spend with Guardrails:** Azure AI Foundry (per-token + cost controls), Copilot Studio (PAYG)
- **Custom Cost Control:** M365 Agents SDK (requires implementation)

💡 **Cross-reference:** See [Evaluation Criteria](evaluation-criteria.md) - Scale & Performance, Cost & Licensing

---

### Question 7: Can the Agent Take Destructive Actions?

**Does your agent need to execute actions (vs just draft/answer)? What level of risk is acceptable?**

Understanding action safety is critical for regulated industries and any scenario where agent errors could have serious consequences (data deletion, resource provisioning, financial approvals).

**Sub-questions:**
1. What types of actions does the agent perform?
   - **Read-only** (search, answer questions, draft content)
   - **Write** (create tickets, send emails, update records)
   - **Destructive** (delete data, disable resources, approve spend, provision access)

2. Are destructive actions acceptable?
   - **No** → Require user-in-the-loop design (user must approve all actions)
   - **Yes, with approval** → Implement human approval workflows for high-risk actions
   - **Yes, autonomous** → Enable autonomous execution with logging and review

3. How are agent actions logged and audited?
   - **Built-in audit logs** (M365 Purview, Azure Monitor)
   - **Custom telemetry** (Application Insights, OpenTelemetry)
   - **No logging** → NOT suitable for regulated industries

**Technology Action Safety Profiles:**

**M365 Copilot (Most Conservative):**
- ✅ **User-in-the-loop always** (drafts content, user must execute)
- ✅ Cannot directly take destructive actions (delete, approve, provision)
- ✅ Built-in audit logs (Microsoft Purview)
- **Best for:** Organizations requiring strictest safety posture, no autonomous execution

**Copilot Studio (Configurable):**
- ⚠️ **Actions can execute** (Power Automate flows, custom connectors)
- ⚠️ Can perform destructive operations if configured (delete records, provision access, approve spend)
- ⚠️ **NO built-in human approval** (must add "Start and wait for an approval" action in flows)
- ✅ Content moderation blocks malicious prompts
- ✅ Built-in audit logs (Purview + analytics)
- **Best for:** Scenarios where actions are needed, but maker designs approval workflows explicitly

**Azure AI Foundry / Agent Service (Autonomous Capable):**
- ⚠️ **Tool calling with autonomous planning loops** (Logic Apps, Functions, OpenAPI, MCP)
- ⚠️ Agents can reason, plan, and execute multi-step tasks without human oversight
- ⚠️ **NO built-in human approval** (developer must implement)
- ✅ OpenTelemetry tracing to reconstruct reasoning process
- ✅ Azure Monitor logs all action executions
- **Best for:** Scenarios requiring autonomous execution with custom human-in-the-loop design and tracing
- **⚠️ Risk:** "Classic autonomous agent risk" - agent chains multiple steps, can make unintended decisions

**M365 Agents SDK (Custom Design):**
- ⚠️ **Full developer responsibility** (no built-in action safety)
- ⚠️ Can integrate with any API (including destructive operations)
- ⚠️ Developer must implement human approval workflows, action boundaries, and logging
- **Best for:** Organizations with development resources to design custom action safety

**Resulting Groupings:**
- **User-in-the-loop always:** M365 Copilot (drafts only, user executes)
- **Configurable execution with approval workflows:** Copilot Studio (maker designs approval steps)
- **Autonomous execution with logging:** Azure AI Foundry/Agent Service (requires tracing + human-in-the-loop design)
- **Custom design:** M365 Agents SDK (developer implements all guardrails)

💡 **See [Implementation Patterns - Action Safety](implementation-patterns.md#pattern-7-action-safety-design-patterns)** for guardrail best practices, approval workflow designs, human-in-the-loop middleware patterns, and tracing configurations.

💡 **Cross-reference:** See [Evaluation Criteria](evaluation-criteria.md) - Action Safety & Content Safety

---

### Question 8: Team Skills & Ownership

**Who will build and maintain the AI solution?**

**Options:**
- **Makers/Business Users** (No coding, business domain expertise)
- **Developers** (C#/Python/TypeScript, API integration)
- **AI/ML Engineers** (Model fine-tuning, evaluations, prompt engineering)
- **Enterprise Architects** (Large-scale integration, DevOps)

**Resulting Groupings:**
- **Maker-Accessible**: Copilot Studio, AI Builder, Power Platform, Declarative Agents
- **Developer-Required**: M365 Agents SDK, Azure AI Foundry, Agent Framework, Teams AI Library
- **AI/ML Engineer-Required**: Azure AI Foundry (custom models, evaluations), Azure Machine Learning
- **Enterprise Integration**: Azure Logic Apps, API Management, Power Automate

💡 **Cross-reference:** See [Evaluation Criteria](evaluation-criteria.md) - Skills Required

---

### Question 9: Does the Agent Need to Initiate Actions?

**Will the agent only respond when users ask, or does it need to monitor systems and trigger actions autonomously?**

Understanding reactive vs proactive capabilities is critical for event-driven scenarios (monitoring, alerts, automated workflows).

**Reactive (User-Initiated Only):**
- User asks question → Agent responds
- Examples: "Ask the HR bot about vacation policy", "Search knowledge base for troubleshooting guide"
- **Technologies:**
  - **M365 Copilot:** User-initiated interactions only
  - **Copilot Studio declarative agents:** User-initiated only

**Proactive (Agent-Initiated):**
- Agent monitors events → Agent triggers actions automatically
- Examples: "Alert finance team when Azure costs exceed budget", "Create incident ticket when deployment fails", "Send daily summary report at 8 AM"
- **Technologies:**
  - **Copilot Studio custom engine agents:** Proactive with Power Automate triggers (scheduled, event-driven)
  - **Azure Logic Apps:** Event-driven workflows (HTTP triggers, storage events, timers)
  - **Azure AI Foundry/Agent Service:** Event triggers with Azure Functions, Logic Apps integration
  - **M365 Agents SDK:** Custom event handling (developer implements triggers)

**Resulting Groupings:**
- **Reactive only:** M365 Copilot, Copilot Studio declarative agents
- **Proactive capable:** Copilot Studio custom engine agents (Power Automate), Logic Apps (event-driven), Azure AI Foundry (Functions/triggers), M365 Agents SDK (custom)

💡 **Cross-reference:** See [Agents for M365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agents-overview) - Declarative vs Custom Engine

---

## Phase 3: Scenario-Specific Selection

**Purpose:** Given the technology groupings from Phase 2, apply scenario-specific criteria to select the optimal tool for your specific requirements.

💡 **This phase answers: "Given my groupings, which specific technology should I choose?"**

**Apply these criteria in order:**

### 1. Time to Market Urgency

**Days (Immediate):**
- M365 Copilot (built-in agents, no setup)
- Copilot Studio templates (declarative agents)

**Weeks (Fast):**
- Copilot Studio (custom engine agents with low-code)
- Azure Logic Apps (visual designer + AI agent workflows)
- M365 Agents SDK (with Teams AI Library for Teams-only)

**Months (Custom):**
- Azure AI Foundry + custom development
- M365 Agents SDK + Agent Framework (complex orchestration)
- Azure AI Agent Service (managed PaaS for enterprise-scale)

💡 **Cross-reference:** [Scenarios](scenarios.md)

---

### 2. Managed vs. Self-Managed Preference

**Managed (SaaS/PaaS):**
- Microsoft 365 Copilot (fully managed)
- Copilot Studio (SaaS platform)
- Azure AI Agent Service (managed agent runtime)

**Self-Managed (Infrastructure Control):**
- Azure AI Foundry (you manage compute, networking)
- M365 Agents SDK (you host and deploy)
- Azure Logic Apps (Standard plan, self-hosted integration runtime)

**Hybrid:**
- Copilot Studio with BYOK/BYOM (managed platform + your infrastructure)
- Azure AI Foundry + Agent Service (code-first + managed runtime)

💡 **Cross-reference:** [Feature Comparison](feature-comparison.md) - Deployment row

---

### 3. Complexity Level

**Low Complexity (Simple Q&A, basic actions):**
- Copilot Studio declarative agents
- M365 Copilot with Graph Connectors
- AI Builder models (prebuilt document processing)

**Medium Complexity (Multi-step workflows, integrations):**
- Copilot Studio custom engine agents with BYOK/BYOM
- M365 Agents SDK with simple orchestration
- Azure Logic Apps AI agent workflows

**High Complexity (Multi-agent, custom orchestration, advanced evals):**
- Azure AI Foundry + Azure AI Agent Service
- M365 Agents SDK + Agent Framework (checkpointing, workflow orchestration)
- Custom solutions with Agent Framework

💡 **Cross-reference:** [Evaluation Criteria](evaluation-criteria.md) - Complexity table

---

### 4. Budget & Licensing Model

**Predictable Per-User:**
- M365 Copilot ($30/user/month, included in Microsoft 365 E5)

**Usage-Based (No upfront commitment):**
- Copilot Studio Pay-As-You-Go ($0.01/Copilot Credit)
- Azure AI Foundry (serverless, pay-per-token)

**Prepaid Capacity:**
- Copilot Studio prepaid packs (predictable high-volume)
- Azure OpenAI provisioned throughput (PTU)

**Azure Consumption:**
- Azure AI Foundry (token-based pricing)
- Azure AI Agent Service (compute + storage)
- Azure Logic Apps (execution-based)

💡 **Cross-reference:** [Evaluation Criteria](evaluation-criteria.md) - Budget Considerations

---

### 5. Integration Requirements

**Need Enterprise Connectors (1,400+)?**
- **Azure Logic Apps** (cloud + on-premises, MCP server, AI agent workflows)

**Need Power Platform Connectors (1,000+)?**
- **Copilot Studio** + **Power Automate** (Cloud Flows or Agent Flows)

**Need Document Processing?**
- **AI Builder** (Power Platform scenarios)
- **Azure Document Intelligence** (custom/advanced scenarios)

**Need Multi-Channel Deployment?**
- **M365 Agents SDK** (10+ channels: Web, Mobile, SMS, WhatsApp, Teams, M365 Copilot)
- **Copilot Studio** (M365 + custom channels)

💡 **Cross-reference:** [Implementation Patterns](implementation-patterns.md) - Pattern 4: Multi-Channel Custom Engine Agent

---

### 6. Orchestration-Specific Needs

**Need Checkpointing (Long-running, human-in-loop)?**
- **Microsoft Agent Framework** (Executor/Edge workflows, built-in checkpointing)
- **Azure Logic Apps** (state management, workflow designer)

**Need Multi-Agent Collaboration?**
- **Azure AI Agent Service** (connected agents, managed orchestration)
- **Copilot Studio** (child agents + connected agents, supports Fabric data agents)
- **Agent Framework** (Handoff/Magentic patterns)

**Need Workflow Automation + AI?**
- **Azure Logic Apps AI Agent Workflows** (autonomous/conversational, MCP server)
- **Copilot Studio Agent Flows** (native flows in Studio)
- **Power Automate Cloud Flows** (1,000+ connectors, long-running)

💡 **Cross-reference:** [Feature Comparison](feature-comparison.md) - Workflow Orchestration Platform Comparison

---

## Phase 3 Decision Output Template

After applying all criteria, document your selection:

**Selected Technology:** [Your Choice]

**Rationale:**
- **Phase 2 Groupings:** [List groupings from 9 questions]
- **Time to Market:** [Days/Weeks/Months + why this matters]
- **Managed vs Self-Managed:** [Preference + reasoning]
- **Complexity Level:** [Low/Medium/High + specific requirements]
- **Budget Model:** [Per-user/Usage/Consumption + constraints]
- **Integration Needs:** [Key connectors/systems required]
- **Orchestration Requirements:** [Checkpointing/Multi-agent/Workflows]

**Architecture Pattern:** [Reference [Implementation Patterns](implementation-patterns.md) Pattern 1-5]

**Trade-offs Accepted:** [What you're giving up, reference [Evaluation Criteria](evaluation-criteria.md)]

**Next Steps:** [Pilot, POC, or full deployment]

---

**Next:** [Scenarios](scenarios.md) - See real-world examples of the framework in action
