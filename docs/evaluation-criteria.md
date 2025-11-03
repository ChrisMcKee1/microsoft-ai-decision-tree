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
| **High** | M365 only, strict DLP | M365 Copilot, Studio | M365 trust boundary |
| **Medium** | Data sovereignty, RBAC | Studio + Azure BYOK | Configurable |
| **Low** | Minimal | Any, prioritize speed | Maximum flexibility |

---

### 6. Scale & Performance

| Scale | Users | Requests/Day | Approach |
|-------|-------|--------------|----------|
| **Small** | <100 | <1K | M365 Copilot, Studio |
| **Medium** | 100-1K | 1K-50K | Studio, AI Search Basic |
| **Large** | 1K-10K | 50K-500K | Azure AI Foundry, Standard |
| **Enterprise** | 10K+ | 500K+ | Foundry, Premium, CDN |

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
