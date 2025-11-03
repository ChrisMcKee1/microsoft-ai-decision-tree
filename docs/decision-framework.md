---
layout: default
title: Decision Framework
nav_order: 4
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

## Phase 2: Technology Groupings (Six Critical Questions)

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

**Options:**
- **M365 Graph** (SharePoint, OneDrive, Teams, third-party via connectors)
- **Azure AI Search** (Large-scale vector + hybrid search)
- **Database** (PostgreSQL pgvector, Cosmos DB, operational data)
- **Multiple Sources** (Hybrid RAG patterns)

**Resulting Groupings:**
- **Graph-Based**: M365 Copilot + Graph Connectors, Copilot Studio with M365 data
- **Vector Search**: Azure AI Search + Azure AI Foundry, BYOK to Copilot Studio
- **Transactional/Real-time**: PostgreSQL pgvector + Azure AI Foundry
- **Hybrid**: Combine Graph + Azure Search + Custom connectors

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
- **Custom Orchestration**: M365 Agents SDK + Semantic Kernel/LangChain, Azure AI Foundry custom

💡 **Cross-reference:** See [Feature Comparison](feature-comparison.md) - Workflow Orchestration Platform Comparison

---

### Question 5: Compliance & Trust Boundary

**What are your data governance and compliance requirements?**

**Options:**
- **M365 Trust Boundary** (Must stay within M365 tenant, use existing compliance posture)
- **Azure-Native** (Leverage Azure governance, VNet, RBAC, private endpoints)
- **Hybrid** (M365 + Azure with proper security architecture)
- **Cross-Cutting Governance** (Need centralized control across all AI deployments)

**Resulting Groupings:**
- **M365 Trust Boundary**: M365 Copilot, Copilot Studio (M365 channels), Graph Connectors
- **Azure-Native**: Azure AI Foundry, Azure AI Agent Service, Azure Logic Apps
- **Hybrid/Flexible**: Copilot Studio (BYOK/BYOM), M365 Agents SDK, API Management AI Gateway
- **Centralized Governance**: Azure API Management (AI Gateway for token limits, chargeback, safety)

💡 **Cross-reference:** See [Evaluation Criteria](evaluation-criteria.md) - Governance Considerations

---

### Question 6: Team Skills & Ownership

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
- Custom solutions with Semantic Kernel or LangChain

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
- **Phase 2 Groupings:** [List groupings from 6 questions]
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

**Next:** [Quick Reference](quick-reference.md) - Fast technology lookup by need
