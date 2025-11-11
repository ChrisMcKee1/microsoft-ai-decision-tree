---
layout: default
title: Home
nav_order: 1
description: "Comprehensive guide to navigating Microsoft's AI technology portfolio and making informed technology decisions"
permalink: /
---

# Microsoft AI Decision Tree
{: .fs-9 }

Master the art of selecting the right Microsoft AI technology for your business needs.
{: .fs-6 .fw-300 }

[Start Learning](docs/capability-model.md){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[View Visual Framework](docs/visual-framework.md){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## The Challenge

Microsoft's AI portfolio includes **M365 Copilot, Copilot Studio, Azure AI Foundry, Agent Service, SDKs, and more**. Each technology serves different needs, and choosing the wrong one wastes time and money.

**This guide solves that problem** by teaching you a systematic framework for evaluating and selecting the right tool for your specific requirements.

---

## What You'll Learn

By following this framework, you'll gain:

✅ **Foundation** - Understanding of Microsoft's five-layer AI capability model  
✅ **Methodology** - The BXT decision framework for systematic technology selection  
✅ **Context** - Real-world scenarios showing how others solved similar problems  
✅ **Application** - Interactive decision trees for visual technology selection  
✅ **Assessment** - Evaluation criteria for complexity, skills, budget, and governance  
✅ **Execution** - Implementation patterns and architecture guidance  
✅ **Mastery** - Deep technical knowledge of each technology's capabilities  

---

## Your Learning Journey

Follow this progressive path for the best learning experience:

```mermaid
%%{init: {'theme':'dark', 'themeVariables': {'fontSize':'14px'}}}%%
flowchart LR
    Start([📖 Start]) --> CM[1️⃣ Capability Model<br/>Five Layers]
    CM --> DF[2️⃣ Decision Framework<br/>BXT Method]
    DF --> SC[3️⃣ Scenarios<br/>Examples]
    SC --> VF[4️⃣ Visual Framework<br/>Diagrams]
    VF --> EC[5️⃣ Evaluation<br/>Assessment]
    EC --> IP[6️⃣ Implementation<br/>Patterns]
    IP --> TECH[7️⃣ Technologies<br/>Deep Dive]
    TECH --> FC[8️⃣ Comparison<br/>Features]
    
    style Start fill:#4CAF50,stroke:#2E7D32,color:#fff
    style CM fill:#1976D2,stroke:#0D47A1,color:#fff
    style DF fill:#1976D2,stroke:#0D47A1,color:#fff
    style SC fill:#1976D2,stroke:#0D47A1,color:#fff
    style VF fill:#1976D2,stroke:#0D47A1,color:#fff
    style EC fill:#1976D2,stroke:#0D47A1,color:#fff
    style IP fill:#1976D2,stroke:#0D47A1,color:#fff
    style TECH fill:#1976D2,stroke:#0D47A1,color:#fff
    style FC fill:#1976D2,stroke:#0D47A1,color:#fff
```

### The Progressive Path

| Step | Module | What You'll Learn | Time Investment |
|------|--------|-------------------|-----------------|
| 1️⃣ | [Capability Model](docs/capability-model.md) | **Foundation** - Five layers from M365 Copilot to Infrastructure | 15 min |
| 2️⃣ | [Decision Framework](docs/decision-framework.md) | **Methodology** - BXT assessment + 6 critical questions | 20 min |
| 3️⃣ | [Scenarios](docs/scenarios.md) | **Context** - Real-world use cases with solutions | 15 min |
| 4️⃣ | [Visual Framework](docs/visual-framework.md) | **Application** - Interactive decision tree diagrams | 20 min |
| 5️⃣ | [Evaluation Criteria](docs/evaluation-criteria.md) | **Assessment** - Complexity, skills, budget, governance | 15 min |
| 6️⃣ | [Implementation Patterns](docs/implementation-patterns.md) | **Execution** - Proven architecture patterns | 15 min |
| 7️⃣ | [Technologies](docs/technologies.md) | **Deep Dive** - Technical specifications for each tool | 30 min |
| 8️⃣ | [Feature Comparison](docs/feature-comparison.md) | **Mastery** - Side-by-side feature matrices | 10 min |

**Total learning time:** ~2.5 hours for complete framework mastery

**Reference materials** (use as needed): [Quick Reference](docs/quick-reference.md) · [Resources](docs/resources.md) · [Glossary](docs/glossary.md)

---

## Choose Your Learning Path

### 🎓 First-Time Learner
**Recommended:** Follow the sequential path above for comprehensive understanding.

**Start here:** [Capability Model](docs/capability-model.md) - Understand the five-layer foundation

### 🎨 Visual Learner
**Prefer diagrams?** Jump to the interactive decision trees and explore visually.

**Start here:** [Visual Framework](docs/visual-framework.md) - See the decision trees first

### ⚡ Need Quick Answers
**Experienced user?** Use the fast-lookup tables and scenario shortcuts.

**Start here:** [Scenarios](docs/scenarios.md) - "I need X" → recommended path

---

---

## Common Paths (Quick Shortcuts)

For experienced users who need fast recommendations:

### "I need something in production next week"

→ **[M365 Copilot](docs/technologies.md#microsoft-365-copilot)** (fastest end-user experience once IT completes [tenant readiness and licensing](https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-setup)) or **[Copilot Studio](docs/technologies.md#copilot-studio)** (templates available)

### "I have makers but no developers"

→ **[Copilot Studio](docs/technologies.md#copilot-studio)** + **[AI Builder](docs/capability-model.md#layer-4-infrastructure--ai-services-building-blocks)**

### "I have a dev team and complex requirements"

→ **[Azure AI Foundry](docs/technologies.md#azure-ai-foundry)** or **[M365 Agents SDK](docs/technologies.md#microsoft-365-agents-sdk--toolkit)**

### "I need enterprise integration + AI"

→ **[Azure Logic Apps](docs/technologies.md#azure-logic-apps)** (1,400+ connectors, AI agent workflows)

### "I need to extend M365 Copilot"

→ **[Graph Connectors](docs/capability-model.md#layer-2-extensibility-enhance-existing-copilots)** (data) or **[Declarative Agents](docs/capability-model.md#layer-2-extensibility-enhance-existing-copilots)** (custom skills)

{: .note }
> **Note:** These shortcuts skip the learning framework. For comprehensive understanding, follow the [progressive learning path](#your-learning-journey) above.

---

## Framework Principles

This guide is built on evidence-based research and systematic decision-making:

1. **Source-First Research** - All content backed by official Microsoft documentation
2. **Framework-Driven** - BXT methodology + 6 critical questions + scenario criteria
3. **Pattern-Oriented** - Proven implementation approaches from real deployments
4. **Progressive Learning** - Foundation → Context → Application → Mastery
5. **Start Simple, Scale Smart** - Choose the simplest technology that meets requirements

---

## How to Use This Guide

**Sequential Learning (Recommended for first-time users)**  
Follow the numbered path from Capability Model → Feature Comparison to build comprehensive knowledge.

**Modular Learning (For specific questions)**  
Jump directly to relevant sections using the navigation sidebar or Quick Reference.

**Visual Learning (For diagram-oriented thinkers)**  
Start with the Visual Framework to see decision trees, then drill into details as needed.

**Scenario-Based Learning (For practical problem-solvers)**  
Begin with Scenarios to find use cases similar to yours, then explore referenced sections.

---

## About This Framework

**Purpose:** Systematic methodology for navigating Microsoft's AI portfolio and selecting the right technology for your business requirements.

**Approach:**

- Source-backed (official Microsoft Learn documentation)
- Framework-driven (BXT + Technology Groupings + Selection Criteria)
- Pattern-oriented (proven architecture approaches)
- Validation-focused (all diagrams validated against official capabilities)

**Maintenance:** This guide reflects the state as of **November 2025**. Microsoft's AI capabilities evolve rapidly—always verify with official sources for production decisions.

---

## Still Want the Simplified Version?

After understanding the comprehensive framework above, if you prefer Microsoft's official high-level decision tree:

![Microsoft AI Decision Tree](images/ai-decision-tree.svg)

**Source:** [Azure Cloud Adoption Framework - AI Strategy](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/ai/strategy)

{: .warning }
> **Why we recommend the full framework:** This simplified tree doesn't address critical enterprise considerations like governance requirements, data boundaries, network isolation, permissions models, action safety, scale/cost tradeoffs, and proactive capabilities. Real-world decisions require the systematic approach taught in this guide.

---

## Credits & Foundations

This framework integrates:

- Microsoft's [Business-Experience-Technology (BXT) Framework](https://learn.microsoft.com/en-us/microsoft-cloud/dev/copilot/isv/business-envisioning)
- [Cloud Adoption Framework AI Strategy](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/ai/strategy)
- [M365 Copilot Extensibility Guidance](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agents-overview)

---

**Ready to start your learning journey?** → [Begin with the Capability Model](docs/capability-model.md)
