------

layout: defaultlayout: default

title: Resources & Next Stepstitle: Resources & Next Steps

nav_order: 11nav_order: 11

description: "Key takeaways and resources by role"description: "Key takeaways and resources by role"

------



# Resources & Next Steps# Resources & Next Steps

{: .no_toc }

> **TODO:** Extract content from README.md Sections 10+11 (lines ~1450-1500)

Official Microsoft resources and role-based action plans.

{: .fs-6 .fw-300 }**Status:** Stub file created - content needs to be migrated



## Table of contents---

{: .no_toc .text-delta }

## Migration Instructions

1. TOC

{:toc}1. Open the original README.md

2. Locate the content mentioned above

---3. Copy and paste into this file (replace this stub content)

4. Verify all cross-references are updated to link to new file structure

## Key Takeaways5. Test locally with undle exec jekyll serve



### 5 Critical Questions---



Before choosing any Microsoft AI technology, answer these:**Navigation:**

- [← Back to Home](../README.md)

1. **Where should users experience the AI?**  - [View Technologies](technologies.md)

   M365 apps → M365 Copilot | Teams/custom → Copilot Studio or M365 SDK | Multi-channel → Azure AI Foundry- [View Decision Framework](decision-framework.md)


2. **What's your build style?**  
   No-code → M365 Copilot | Low-code → Copilot Studio | Pro-code → M365 SDK or Azure AI Foundry

3. **Where does your data live?**  
   M365 only → Graph Connectors | Azure only → Azure AI Search | Both → Hybrid (BYOK or Graph + Azure)

4. **How complex is your agent?**  
   Simple Q&A → M365 Copilot | Workflows → Studio | Multi-agent → M365 SDK + LangGraph or Azure AI Agent Service

5. **What are your compliance needs?**  
   M365 trust boundary only → M365 Copilot/Studio | Configurable → Studio with BYOK | Full control → Azure AI Foundry

---

### Decision Hierarchy

```
Layer 1: User Experience
   ↓
Layer 2: Build Approach (Low-code vs Pro-code)
   ↓
Layer 3: Platform (M365 Copilot, Studio, M365 SDK, Azure AI Foundry)
   ↓
Layer 4: Data & AI Services (Graph, Azure AI Search, Cosmos DB, etc.)
   ↓
Layer 5: Supporting Services (Azure OpenAI, AI Content Safety, etc.)
```

---

## Next Steps by Role

### For Business Decision Makers

**Your Goal:** Understand costs, timelines, and ROI

1. **Start Here:**
   - Review [Scenarios](scenarios.md) for real-world examples
   - Check [Feature Comparison](feature-comparison.md) cost tables
   - Use [Evaluation Criteria](evaluation-criteria.md) budget assessment

2. **Key Resources:**
   - [M365 Copilot Adoption](https://learn.microsoft.com/microsoft-365-copilot/adoption/) - Change management guidance
   - [Copilot Studio Pricing](https://www.microsoft.com/microsoft-copilot/copilot-studio-pricing) - Message-based pricing
   - [Azure AI Pricing Calculator](https://azure.microsoft.com/pricing/calculator/) - Estimate Azure costs

3. **Next Actions:**
   - Identify pilot use case from [Scenarios](scenarios.md)
   - Assess team skills with [Evaluation Criteria](evaluation-criteria.md)
   - Schedule architecture review with technical team

---

### For Architects & Tech Leads

**Your Goal:** Design the right architecture

1. **Start Here:**
   - Review [Technologies](technologies.md) for full tech stack
   - Study [Implementation Patterns](implementation-patterns.md) for proven designs
   - Use [Visual Framework](visual-framework.md) decision trees

2. **Key Resources:**
   - [Microsoft 365 Copilot Extensibility](https://learn.microsoft.com/microsoft-365-copilot/extensibility/) - Official architecture guidance
   - [Azure AI Foundry Documentation](https://learn.microsoft.com/azure/ai-studio/) - Azure AI architecture
   - [Microsoft Agents Reference](https://learn.microsoft.com/microsoft-365-copilot/extensibility/microsoft-365-agents-overview) - Agent patterns

3. **Next Actions:**
   - Map data sources to grounding patterns ([Visual Framework](visual-framework.md) - Data Grounding Decision)
   - Assess compliance constraints ([Evaluation Criteria](evaluation-criteria.md) - Governance)
   - Design pilot architecture using [Implementation Patterns](implementation-patterns.md)

---

### For Developers

**Your Goal:** Build and deploy AI solutions

1. **Start Here:**
   - Choose your platform: [Feature Comparison](feature-comparison.md)
   - Pick a use case: [Scenarios](scenarios.md)
   - Follow implementation steps: [Implementation Patterns](implementation-patterns.md)

2. **Key Resources by Platform:**

   **M365 Copilot:**
   - [Build Declarative Agents](https://learn.microsoft.com/microsoft-365-copilot/extensibility/declarative-agents) - No-code agents
   - [Graph Connectors](https://learn.microsoft.com/graph/connecting-external-content-connectors-overview) - Data grounding
   - [API Plugins](https://learn.microsoft.com/microsoft-365-copilot/extensibility/api-plugins-overview) - Extend Copilot

   **Copilot Studio:**
   - [Copilot Studio Documentation](https://learn.microsoft.com/microsoft-copilot-studio/) - Full docs
   - [Build Topics](https://learn.microsoft.com/microsoft-copilot-studio/authoring-create-edit-topics) - Conversational design
   - [Custom Actions](https://learn.microsoft.com/microsoft-copilot-studio/advanced-plugin-actions) - Code integration

   **M365 Agents SDK:**
   - [Teams AI Library](https://learn.microsoft.com/microsoftteams/platform/bots/how-to/teams-conversational-ai/teams-conversation-ai-overview) - TypeScript/C#/Python
   - [Build Multi-Agent Systems](https://learn.microsoft.com/microsoft-365-copilot/extensibility/build-declarative-agents) - Orchestration
   - [Microsoft Agents Framework](https://learn.microsoft.com/semantic-kernel/frameworks/agent/) - Agent patterns

   **Azure AI Foundry:**
   - [Azure AI Foundry Quickstart](https://learn.microsoft.com/azure/ai-studio/quickstarts/) - Get started
   - [Prompt Flow](https://learn.microsoft.com/azure/ai-studio/how-to/prompt-flow) - Build orchestrations
   - [Azure AI Agent Service](https://learn.microsoft.com/azure/ai-services/agents/) - Multi-agent (Preview)

3. **Data & AI Services:**
   - [Azure AI Search](https://learn.microsoft.com/azure/search/) - Document grounding
   - [Cosmos DB Vector Search](https://learn.microsoft.com/azure/cosmos-db/vector-search) - Database vectors
   - [PostgreSQL AI Extensions](https://learn.microsoft.com/azure/postgresql/flexible-server/generative-ai-azure-overview) - Relational + AI
   - [LangChain with Microsoft](https://python.langchain.com/docs/integrations/providers/microsoft/) - Open-source orchestration

4. **Next Actions:**
   - Clone sample from [Microsoft Copilot Studio Samples](https://github.com/microsoft/copilot-studio-samples)
   - Follow a [Scenario](scenarios.md) step-by-step
   - Join [Microsoft Copilot Community](https://techcommunity.microsoft.com/copilot)

---

### For Makers & Power Users

**Your Goal:** Build solutions without code

1. **Start Here:**
   - Explore [Copilot Studio](https://copilotstudio.microsoft.com) - Sign in and try templates
   - Review [Scenarios](scenarios.md) - Focus on Scenario 1 (HR Bot) and Scenario 2 (Invoice Processing)
   - Check [Quick Reference](quick-reference.md) for fast lookups

2. **Key Resources:**
   - [Copilot Studio Learning Path](https://learn.microsoft.com/training/paths/work-power-virtual-agents/) - Free training
   - [AI Builder Documentation](https://learn.microsoft.com/ai-builder/) - Pre-built AI models
   - [Power Automate AI](https://learn.microsoft.com/power-automate/use-ai-builder) - Workflow automation

3. **Next Actions:**
   - Create a test environment in [Copilot Studio](https://copilotstudio.microsoft.com)
   - Build "HR Knowledge Base" from [Scenarios](scenarios.md)
   - Explore Graph Connectors for SharePoint data

---

### For Data Scientists

**Your Goal:** Train and deploy custom models

1. **Start Here:**
   - [Azure AI Foundry](https://ai.azure.com) - ML workspace
   - [Capability Model](capability-model.md) - Understand full stack
   - [Feature Comparison](feature-comparison.md) - When to use Foundry vs SDK

2. **Key Resources:**
   - [Azure AI Foundry Documentation](https://learn.microsoft.com/azure/ai-studio/) - Full platform docs
   - [Prompt Flow](https://learn.microsoft.com/azure/ai-studio/how-to/prompt-flow) - Build flows
   - [Model Catalog](https://learn.microsoft.com/azure/ai-studio/how-to/model-catalog) - Pre-trained models
   - [Fine-Tuning](https://learn.microsoft.com/azure/ai-studio/how-to/fine-tune-models) - Custom training
   - [Evaluation](https://learn.microsoft.com/azure/ai-studio/how-to/evaluate-generative-ai-app) - Metrics and testing

3. **Data & Vector Stores:**
   - [Azure AI Search](https://learn.microsoft.com/azure/search/vector-search-overview) - Vector indexing
   - [Cosmos DB Vectors](https://learn.microsoft.com/azure/cosmos-db/vector-search) - Database vectors
   - [Azure AI Content Understanding](https://learn.microsoft.com/azure/ai-services/document-intelligence/concept-layout) - Document processing (Preview)

4. **Next Actions:**
   - Create Azure AI Foundry project
   - Follow [Azure OpenAI + RAG Tutorial](https://learn.microsoft.com/azure/ai-studio/tutorials/deploy-chat-web-app)
   - Experiment with Prompt Flow for orchestration

---

## Official Microsoft Communities

### Forums & Support
- [Microsoft Copilot Community](https://techcommunity.microsoft.com/copilot) - Official forums
- [Copilot Studio Community](https://powerusers.microsoft.com/t5/Microsoft-Copilot-Studio/bd-p/PVACommunity) - Maker community
- [Azure AI Community](https://techcommunity.microsoft.com/category/azure-ai/ct-p/azure-ai) - Azure AI discussions
- [Microsoft Q&A](https://learn.microsoft.com/answers/) - Technical Q&A

### GitHub Repositories
- [Copilot Studio Samples](https://github.com/microsoft/copilot-studio-samples) - Official samples
- [Teams AI Library Samples](https://github.com/microsoft/teams-ai/tree/main/js/samples) - M365 SDK examples
- [Azure AI Foundry Samples](https://github.com/Azure/azure-ai-studio-samples) - Foundry examples
- [Semantic Kernel](https://github.com/microsoft/semantic-kernel) - Agent framework
- [LangChain Azure](https://github.com/langchain-ai/langchain/tree/master/libs/partners/microsoft) - LangChain + Microsoft

### Learning Paths
- [M365 Copilot Training](https://learn.microsoft.com/training/paths/get-started-with-microsoft-365-copilot/) - For end users
- [Copilot Studio Learning](https://learn.microsoft.com/training/paths/work-power-virtual-agents/) - For makers
- [Teams AI Library Learning](https://learn.microsoft.com/training/modules/teams-toolkit-vsc-create-bot/) - For developers
- [Azure AI Fundamentals](https://learn.microsoft.com/training/paths/get-started-with-artificial-intelligence-on-azure/) - For AI/ML roles

---

## Documentation Hub

### By Technology Layer

**Layer 1-3: Platforms**
- [M365 Copilot](https://learn.microsoft.com/microsoft-365-copilot/) - Official docs
- [Copilot Studio](https://learn.microsoft.com/microsoft-copilot-studio/) - Studio docs
- [M365 Agents SDK](https://learn.microsoft.com/microsoft-365-copilot/extensibility/build-declarative-agents) - Agent development
- [Azure AI Foundry](https://learn.microsoft.com/azure/ai-studio/) - Azure AI platform

**Layer 4: Data & AI Services**
- [Graph Connectors](https://learn.microsoft.com/graph/connecting-external-content-connectors-overview) - M365 data
- [Azure AI Search](https://learn.microsoft.com/azure/search/) - Document search
- [Cosmos DB](https://learn.microsoft.com/azure/cosmos-db/) - NoSQL + vectors
- [PostgreSQL](https://learn.microsoft.com/azure/postgresql/flexible-server/generative-ai-azure-overview) - Relational + AI
- [SQL Server 2025](https://learn.microsoft.com/sql/relational-databases/vectors/vectors-sql-server) - On-prem/cloud vectors

**Layer 5: AI Services**
- [Azure OpenAI](https://learn.microsoft.com/azure/ai-services/openai/) - LLM APIs
- [AI Content Safety](https://learn.microsoft.com/azure/ai-services/content-safety/) - Safety filters
- [Document Intelligence](https://learn.microsoft.com/azure/ai-services/document-intelligence/) - OCR + extraction

---

## Staying Current

Microsoft's AI landscape evolves rapidly. Track updates:

### Official Blogs
- [Microsoft 365 Blog](https://www.microsoft.com/microsoft-365/blog/) - M365 Copilot updates
- [Azure AI Blog](https://techcommunity.microsoft.com/category/azure-ai/blog/azure-ai-blog/ba-p/Azure-AI-Blog) - Azure AI announcements
- [Copilot Studio Blog](https://powervirtualagents.microsoft.com/blog/) - Studio updates

### Release Notes
- [M365 Copilot Roadmap](https://www.microsoft.com/microsoft-365/roadmap?filters=Microsoft%20365%20Copilot) - Public roadmap
- [Copilot Studio Release Notes](https://learn.microsoft.com/power-platform-release-plan/2025wave1/copilot-studio/) - Quarterly releases
- [Azure AI Updates](https://azure.microsoft.com/updates/?category=ai-machine-learning) - Azure AI changes

### Events
- [Microsoft Build](https://build.microsoft.com/) - Annual developer conference (May)
- [Microsoft Ignite](https://ignite.microsoft.com/) - Annual IT conference (November)
- [AI Community Calls](https://learn.microsoft.com/shows/) - Monthly webcasts

---

## Quick Action Checklist

Use this to start your AI project:

**Phase 1: Assess (1-2 days)**
- [ ] Review [Scenarios](scenarios.md) for similar use cases
- [ ] Complete [Evaluation Criteria](evaluation-criteria.md) checklist
- [ ] Identify data sources and locations
- [ ] Confirm team skills and budget

**Phase 2: Design (3-5 days)**
- [ ] Use [Visual Framework](visual-framework.md) decision trees
- [ ] Compare platforms in [Feature Comparison](feature-comparison.md)
- [ ] Choose architecture from [Implementation Patterns](implementation-patterns.md)
- [ ] Document requirements and constraints

**Phase 3: Prototype (1-2 weeks)**
- [ ] Set up development environment
- [ ] Build MVP following [Scenarios](scenarios.md) steps
- [ ] Test with 5-10 users
- [ ] Measure key metrics

**Phase 4: Production (2-4 weeks)**
- [ ] Implement governance policies
- [ ] Set up monitoring and analytics
- [ ] Train end users
- [ ] Deploy and iterate

---

## Get Help

**Stuck on technology choice?**  
→ Start with [Visual Framework](visual-framework.md) - Complete Decision Flow

**Need cost estimates?**  
→ See [Feature Comparison](feature-comparison.md) - Cost Comparison table

**Looking for examples?**  
→ Review [Scenarios](scenarios.md) - 3 real-world use cases

**Want to dive deeper?**  
→ Explore [Technologies](technologies.md) - Full tech stack reference

---

**Framework Version:** 1.0  
**Last Updated:** November 2025  
**Contributors:** Microsoft AI Decision Tree Project

**Found this helpful? [⭐ Star this repo](https://github.com/ChrisMcKee1/microsoft-ai-decision-tree)**
