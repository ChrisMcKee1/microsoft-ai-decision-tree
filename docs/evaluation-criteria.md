---
layout: default
title: Evaluation Criteria
nav_order: 6
description: "Framework for evaluating complexity, skills, budget, and governance"
---

# Evaluation Criteria
{: .no_toc }

Assess your situation before selecting Microsoft AI technologies.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Purpose

Use this framework to evaluate your organization's readiness and requirements before choosing Microsoft AI technologies.

---

## Evaluation Framework

### 1. Technical Complexity Assessment

**Question:** How complex is your use case?

| Complexity Level | Characteristics | Recommended Technologies |
|-----------------|-----------------|--------------------------|
| **Low** | Simple Q&A, existing knowledge base, single data source | M365 Copilot, Graph Connectors, Declarative Agents |
| **Medium** | Multiple data sources, workflow automation, approvals | Copilot Studio, AI Builder, Power Automate |
| **High** | Custom models, multi-agent orchestration, custom evaluation | Azure AI Foundry, M365 Agents SDK, Agent Framework |
| **Very High** | Multi-step reasoning, complex state management | Azure AI Foundry + Agent Framework, custom pipelines |

**Key Indicators:**
- Data sources: 1 (low) vs 5+ (high)
- Workflow: Linear (low) vs branching/parallel (high)
- Reasoning: Simple lookup (low) vs multi-step inference (high)
- Evaluation: User feedback (low) vs custom metrics (high)

---

### 2. Skills & Resources

**Question:** What skills do you have?

| Skill Level | Resources | Time | Recommended |
|-------------|-----------|------|-------------|
| **Makers** | No devs, 1-3 people | 10-20 hrs/week | Copilot Studio, AI Builder |
| **Makers + Dev** | Occasional dev help | 20-30 hrs/week | Studio + custom actions |
| **Pro Developers** | Full dev team | 40+ hrs/week | M365 SDK, Azure AI Foundry |
| **Data Scientists** | ML expertise | 40+ hrs/week | Azure AI Foundry, custom models |

---

### 3. Budget Assessment

| Budget | Setup | Ongoing | Technologies |
|--------|-------|---------|--------------|
| **< $500/mo** | Minimal | M365 licenses | M365 Copilot, Graph Connectors |
| **$500-$2K/mo** | Low | Messages, credits | Copilot Studio, AI Builder |
| **$2K-$10K/mo** | Medium | Azure services | Azure AI Foundry, M365 SDK |
| **$10K+/mo** | High | Enterprise scale | Full Azure AI stack |

---

### 4. Time to Production

| Timeline | Feasibility | Approach | Tradeoffs |
|----------|-------------|----------|-----------|
| **Days** | Simple only | M365 + Graph Connectors | Limited customization |
| **1-2 Weeks** | Low-code | Copilot Studio templates | Medium customization |
| **1-2 Months** | Custom agents | Studio + custom actions | Good balance |
| **3-6 Months** | Complex | Azure AI Foundry | Full customization |

---

### 5. Governance & Compliance

| Level | Constraints | Approach | Why |
|-------|-------------|----------|-----|
| **High** | M365 tenant boundary only, strict DLP, no training on data | M365 Copilot | M365 trust boundary, strictest governance |
| **Medium-High** | Data sovereignty, RBAC, external connector controls, gateway for private access | Copilot Studio + DLP | Configurable, **external connectors inherit compliance** |
| **High (Azure)** | VNet isolation, private endpoints, CMK, no public egress | Azure AI Foundry/Agent Service | Azure landing zone controls, sovereign data |
| **High (Custom)** | Self-hosted, custom VNet, air-gapped support | M365 Agents SDK | Customer controls all networking |
| **Low** | Minimal, hosting platform dependent | Agent Framework | Maximum flexibility |

**Critical Considerations - Data Boundary:**
- **M365 Copilot:** Data NEVER leaves M365 tenant boundary. No training on tenant data. Inherits M365 compliance (GDPR, HIPAA, FedRAMP).
- **Copilot Studio:** ⚠️ External connectors (custom APIs, non-Microsoft systems) **inherit external system's compliance posture**. Web search leaves enterprise boundary (NOT covered by DPA). Compliance certifications: HIPAA, FedRAMP, SOC, ISO, PCI DSS. Power Platform DLP policies (environment/tenant-level) control connector access, custom connector endpoints (pattern matching), autonomous agent triggers.
- **Azure AI Foundry/Agent Service:** Full Azure controls (VNet, private endpoints, CMK, Azure Policy). Governed by YOUR Azure landing zone. Content Safety service provides configurable filtering (Hate, Violence, Sexual, Self-Harm at Low/Medium/High severity), groundedness detection, prompt shields (jailbreak/indirect attacks).

**Critical Considerations - Network Isolation:**
- **Azure AI Foundry/Agent Service:** ✅ Full private networking support. Standard Setup with Private Networking = no public egress by default. Supports air-gapped environments.
- **Copilot Studio:** ⚠️ Does NOT execute in customer VNet. Requires on-premises data gateway (for on-prem systems) OR VNet data gateway (GA, for Azure resources). Not suitable for fully air-gapped without gateway setup.
- **M365 Agents SDK:** ✅ Self-hosted = customer controls networking. Supports VNet integration, private endpoints, air-gapped Azure deployments. Full responsibility for network security.
- **M365 Copilot:** ❌ No custom VNet support (fully managed SaaS). Requires gateway architecture for on-prem data access.

**Critical Considerations - Permissions & Identity Model:**
- **M365 Copilot:** ✅ Always user-scoped. "It only sees what I can see" = TRUE (architecturally guaranteed). Actions attributed to individual users.
- **Copilot Studio:** ⚠️ Dual auth mode: User authentication (user-scoped) OR Agent author authentication (service account). Service accounts can exceed individual user permissions. **Critical for actions that write data.**
- **Azure AI Foundry:** ⚠️ API key (bypasses user identity) OR Entra ID (per-user RBAC, managed identities). **Entra ID recommended for production** (user attribution, least privilege).
- **M365 Agents SDK:** ⚠️ Custom auth design: Delegated permissions (user-scoped) OR Application permissions (service principal, tenant-wide scope). **Requires documented auth architecture for audit.**

**Critical Considerations - Action Safety & Content Safety:**
- **M365 Copilot:** ✅ User-in-the-loop always (drafts only, user executes). Cannot take destructive actions. ✅ Content moderation + prompt injection defenses built-in.
- **Copilot Studio:** ⚠️ Actions can execute (Power Automate flows, custom connectors). No built-in human approval. **Add approval workflows for destructive actions.** ✅ Content moderation blocks malicious prompts.
- **Azure AI Foundry/Agent Service:** ⚠️ Tool calling with autonomous planning loops. No built-in approval. **Implement human-in-the-loop + OpenTelemetry tracing.** ✅ Content safety via Azure AI Content Safety service.
- **M365 Agents SDK:** ⚠️ Custom design (developer responsibility). No built-in action safety or approval. **Implement custom guardrails.** Content safety depends on implementation.

**Critical Considerations - Proactive Capabilities (Question 9):**
- **Reactive only:** M365 Copilot, Copilot Studio declarative agents (user-initiated interactions only)
- **Proactive capable:** Copilot Studio custom engine agents (Power Automate triggers), Logic Apps (event-driven), Azure AI Foundry (Functions/triggers), M365 Agents SDK (custom)

---

### 6. Memory, Analytics & Conversation History

**Question for Legal/Audit Teams:**

Understanding where conversation data is stored and who can access it is **critical** for regulated industries (healthcare, finance, legal).

**Key Questions to Answer:**
- Where is conversation history stored?
- How long is it retained?
- Who can access it?
- Can we scrub PII from transcripts?
- Does this meet our compliance requirements (HIPAA, GDPR, SOX)?

**Technology Comparison:** See [Quick Reference - Memory & Analytics](quick-reference.md#memory--analytics-by-technology) for detailed comparison table.

**Critical Distinctions:**
- **M365 Copilot:** Grounding ONLY (NO per-user memory extractable by admins). Activity history in user mailbox (Purview-governed).
- **Copilot Studio:** Grounding + Dataverse memory variables. Full transcript access for admins (critical for regulated review).
- **Azure AI Agent Service:** BYO thread storage (customer Cosmos DB). Customer responsible for retention, PII scrubbing.
- **M365 Agents SDK:** Custom implementation (developer implements everything).

💡 **Cross-reference:** See [Decision Framework Q3](decision-framework.md#question-3-data-grounding-pattern) - Grounding vs Memory vs Analytics distinction

---

### 7. Scale & Performance

**Understanding Performance Trade-Offs:**

Performance optimization varies by platform and use case. Choose based on your priorities:

| Dimension | Copilot Studio | Azure AI Foundry | Decision Driver |
|-----------|----------------|------------------|-----------------|
| **Development Velocity** | Days to weeks (low-code platform) | Weeks to months (custom code) | Speed to market vs full customization |
| **Connector Ecosystem** | 1,400+ Power Platform connectors | Custom API integrations | Pre-built integrations vs custom control |
| **Runtime Latency** | <1s (managed orchestration) | <100ms (direct API access) | Response time requirements |
| **Operational Overhead** | Low (Microsoft-managed SaaS) | Higher (self-managed PaaS) | Operational preferences |
| **Context Window** | 400k (platform-managed)^1^ | 400k (full model access) | Context vs convenience trade-off |
| **Throughput Scaling** | Requests per minute (RPM)-based (message billing) | Tokens per minute (TPM)-based (provisioned capacity) | Cost model preferences |

^1^ Effective context in Copilot Studio varies by configuration; full model context available in Azure AI Foundry with infrastructure management responsibility.

**Scenario-Based Selection:**

**Choose Copilot Studio when:**

- Speed to market is critical (rapid iteration, quick delivery)
- Leveraging Power Platform's 1,400+ built-in connectors and triggers
- Prefer managed infrastructure (SaaS convenience)
- Response times <1s are acceptable
- Built-in governance and ALM are priorities
- Team includes makers and developers
- **Testing:** [Power CAT Copilot Studio Kit](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/kit-overview) for automated agent validation (response match, topic match, generative answers, multi-turn scenarios)

**Choose Azure AI Foundry when:**

- Latency <100ms is required (real-time applications)
- Need full architectural control and optimization
- High-throughput scenarios (PTU provisioning)
- **Testing:** [Prompt flow evaluations](https://learn.microsoft.com/en-us/azure/ai-foundry/how-to/evaluate-generative-ai-app) with built-in metrics (groundedness, relevance, coherence) or custom evaluators
- Custom patterns beyond platform capabilities
- Custom integrations outside standard connector ecosystem
- Team has Azure and AI engineering expertise

**Complementary Use:**

Many organizations use both platforms - Copilot Studio for rapid deployment with rich connector integration, Azure AI Foundry for performance-critical custom applications. The platforms serve complementary needs, not competitive choices.

#### Scale Planning by User Volume

| Scale | Users | Requests/Day | Copilot Studio Fit | Azure AI Foundry Fit |
|-------|-------|--------------|-------------------|---------------------|
| **Small** | <100 | <1K | ✅ Ideal (rapid deployment) | ⚠️ May be over-engineered |
| **Medium** | 100-1K | 1K-50K | ✅ Strong (with capacity planning) | ✅ Strong (with cost optimization) |
| **Large** | 1K-10K | 50K-500K | ⚠️ Monitor quotas carefully | ✅ Ideal (PTU provisioning) |
| **Enterprise** | 10K+ | 500K+ | ⚠️ Requires premium capacity | ✅ Ideal (enterprise scale) |

#### Rate Limits & Cost Model Trade-Offs

**Copilot Studio:**

- **Environment-level quotas:**
  - General messages: 8,000 requests per minute (RPM) per Dataverse environment
  - Generative AI: 50-100+ RPM / 1,000-2,000+ requests per hour (RPH) (scales with capacity packs: 50 RPM/1K RPH for 1-10 packs, up to 100 RPM/2K RPH for 51+ packs or PAYG)
- **Shared across agents:** All agents in environment share quota pool
- **Channel limits:** Channels include Teams, Web (Direct Line), Mobile, WhatsApp, Facebook, Azure Bot Service channels
- **Power Platform requests:** 250K/24h for standard subscription (flows triggered by agents)
- **Cost predictability:** Prepaid packs or PAYG ($0.01/Copilot Credit)
- **Increase limits:** Contact Support for rate limit increases (PAYG environments only)
- **Best for:** Predictable workloads, call centers, internal use cases with capacity planning

**Azure AI Foundry / Agent Service:**

- **Tokens per minute (TPM) quotas:** Per region/model (request increases available)
- **Variable cost:** Per-token billing scales with traffic
- **Cost optimization:** Model routing, provisioned throughput units (PTU) reservations, caching strategies
- **Best for:** Variable traffic patterns, public-facing channels with guardrails

**M365 Agents SDK:**

- **Custom auto-scaling:** Developer controls rate limiting and scaling logic
- **Flexible cost:** Hosting + token-based (if using Azure OpenAI)
- **Full control:** Custom traffic management and optimization
- **Best for:** Complex custom requirements, existing Azure infrastructure

**Sources:**

- [Copilot Studio Quotas and Limits](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-quotas) (Updated: 2024-11-01)
- [Resolve Throttling Errors](https://learn.microsoft.com/en-us/troubleshoot/power-platform/copilot-studio/licensing/throttling-errors-agents) (Updated: 2024-10-15)
- [Optimize Latency in CPS](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/optimize-minimize-latency) (Updated: 2024-09-20)
- [Performance and Latency - Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/how-to/latency) (Updated: 2024-10-22)
- [Power Platform Request Limits](https://learn.microsoft.com/en-us/power-platform/admin/api-request-limits-allocations) (Updated: 2024-10-18)

**Last Updated:** 2025-11-05

---

💡 **Cross-reference:** See [Decision Framework Q6](decision-framework.md#question-6-what-are-your-scale-and-cost-requirements)

---

## Decision Matrix

| Situation | Start | Path |
|-----------|-------|------|
| Makers, low budget, M365 data | M365 + Graph Connectors | → Studio |
| Makers, workflows | Studio + AI Builder | → Add BYOK |
| Devs, multi-channel | M365 SDK + Studio | → Azure AI Foundry |
| Devs, custom models | Azure AI Foundry | → Add Agent Framework |
| Data scientists | Foundry + Agent Framework | → BYOM |

---

## Evaluation Checklist

**Technical:**
- [ ] Identified data sources
- [ ] Assessed data quality
- [ ] Determined integrations
- [ ] Evaluated constraints

**Skills:**
- [ ] Confirmed skill levels
- [ ] Identified team size
- [ ] Assessed learning curve
- [ ] Planned knowledge transfer

**Budget:**
- [ ] Estimated setup costs
- [ ] Projected ongoing costs
- [ ] Set realistic timeline
- [ ] Planned contingency

**Governance:**
- [ ] Reviewed data sovereignty
- [ ] Confirmed compliance needs
- [ ] Assessed audit requirements
- [ ] Planned DLP policies

**Scale:**
- [ ] Estimated users
- [ ] Projected volume
- [ ] Assessed performance needs
- [ ] Planned monitoring

---

## Next Steps

**Feature comparison:**  
→ [Feature Comparison](feature-comparison.md)

**Visual guidance:**  
→ [Visual Framework](visual-framework.md)

**Real examples:**  
→ [Scenarios](scenarios.md)

**Architecture patterns:**  
→ [Implementation Patterns](implementation-patterns.md)

---

**Last Updated:** November 2025  
**Next:** [Implementation Patterns](implementation-patterns.md) - Learn common patterns and best practices
