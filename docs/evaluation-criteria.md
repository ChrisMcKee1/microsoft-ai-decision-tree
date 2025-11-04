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
- **Copilot Studio:** ⚠️ External connectors (custom APIs, non-Microsoft systems) **inherit external system's compliance posture**. Web search leaves enterprise boundary (NOT covered by DPA).
- **Azure AI Foundry/Agent Service:** Full Azure controls (VNet, private endpoints, CMK, Azure Policy). Governed by YOUR Azure landing zone.

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

| Scale | Users | Requests/Day | Approach |
|-------|-------|--------------|----------|
| **Small** | <100 | <1K | M365 Copilot, Studio |
| **Medium** | 100-1K | 1K-50K | Studio, AI Search Basic |
| **Large** | 1K-10K | 50K-500K | Azure AI Foundry, Standard |
| **Enterprise** | 10K+ | 500K+ | Foundry, Premium, CDN |

#### Critical Considerations - Rate Limits & Cost Models

**Microsoft 365 Copilot:**
- ✅ **No throttling** (Microsoft-managed scaling)
- ✅ **Predictable spend** ($30/user/month)
- ❌ **Not suitable** for external customer scenarios (licensing model)

**Copilot Studio:**
- ⚠️ **Environment-level quotas** (8,000 RPM general, 50-100 RPM gen AI based on capacity packs)
- ⚠️ **Shared across all agents** in environment (can hit throttling errors at scale)
- ✅ **Suitable for call centers/web** with adequate capacity planning
- **Cost:** Prepaid ($200/mo 25K credits) or PAYG ($0.01/credit)

**Azure AI Foundry / Agent Service:**
- ⚠️ **TPM quotas** per region/model (can request increases)
- ⚠️ **Cost scales linearly with traffic** (per-token billing, no hard limits)
- ✅ **Best for public-facing channels** with guardrails (intent classification, model routing, budget alerts)
- **Cost:** Variable per-token, requires cost optimization strategies

**M365 Agents SDK:**
- ⚠️ **Customer controls auto-scaling** (requires custom rate limiting middleware)
- ⚠️ **Cost:** Hosting + token-based (if using Azure OpenAI)
- ✅ **Full control over scaling** and cost optimization
- **Best for:** Custom traffic management requirements

💡 **Cross-reference:** See [Decision Framework Q6](decision-framework.md#question-6-what-are-your-scale-and-cost-requirements)

---

## Decision Matrix

| Situation | Start | Upgrade Path |
|-----------|-------|--------------|
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
