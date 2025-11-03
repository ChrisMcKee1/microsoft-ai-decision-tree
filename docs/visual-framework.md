---
layout: default
title: Visual Framework
nav_order: 10
description: "Decision tree diagrams with Mermaid visualizations"
---

# Visual Framework
{: .no_toc }

Interactive decision trees to guide Microsoft AI technology selection.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Complete Decision Flow

```mermaid
flowchart TD
    Start([Start: Need AI Solution]) --> Q1{Where should users<br/>experience the AI?}
    
    Q1 -->|M365 apps| M365[M365 Copilot]
    Q1 -->|Teams, custom apps| Q2{Build style &<br/>control level?}
    Q1 -->|Multi-channel| Q2
    
    Q2 -->|Low-code, makers| Studio[Copilot Studio]
    Q2 -->|Pro-code, full control| Q3{Primary<br/>platform?}
    
    Q3 -->|M365-centric| SDK[M365 Agents SDK]
    Q3 -->|Azure-centric| Foundry[Azure AI Foundry]
    
    M365 --> Data1{Need custom<br/>data sources?}
    Data1 -->|Yes| Graph[Add Graph Connectors]
    Data1 -->|No| End1([Deploy])
    Graph --> End1
    
    Studio --> Data2{Data location?}
    Data2 -->|M365 only| Studio_M365[Use Graph Connectors]
    Data2 -->|Azure + M365| Studio_BYOK[Use BYOK Preview]
    Data2 -->|Complex| Studio_Actions[Custom Actions]
    Studio_M365 --> End2([Deploy])
    Studio_BYOK --> End2
    Studio_Actions --> End2
    
    SDK --> Data3{Data strategy?}
    Data3 -->|M365 Graph| SDK_Graph[Graph API]
    Data3 -->|Azure Search| SDK_Search[Integrate Azure AI Search]
    Data3 -->|Custom DB| SDK_DB[Connect Cosmos/PostgreSQL]
    SDK_Graph --> End3([Deploy])
    SDK_Search --> End3
    SDK_DB --> End3
    
    Foundry --> Data4{Grounding pattern?}
    Data4 -->|Document search| Foundry_Search[Azure AI Search]
    Data4 -->|Database vectors| Foundry_DB[Cosmos/PostgreSQL/SQL]
    Data4 -->|Custom| Foundry_Custom[Custom embeddings]
    Foundry_Search --> End4([Deploy])
    Foundry_DB --> End4
    Foundry_Custom --> End4
    
    style M365 fill:#0078D4,color:#fff
    style Studio fill:#0078D4,color:#fff
    style SDK fill:#0078D4,color:#fff
    style Foundry fill:#0078D4,color:#fff
```

---

## Persona-Based Flow

```mermaid
flowchart TD
    Start([Who are you?]) --> P1{Your role?}
    
    P1 -->|End user| User[Use M365 Copilot]
    P1 -->|Business maker| Maker{Dev support?}
    P1 -->|Developer| Dev{Focus area?}
    P1 -->|Data scientist| DS[Azure AI Foundry]
    
    Maker -->|No devs| MakerStudio[Copilot Studio]
    Maker -->|Occasional help| MakerPlus[Studio + Custom Actions]
    
    Dev -->|M365 integration| DevM365[M365 Agents SDK]
    Dev -->|Azure services| DevAzure[Azure AI Foundry]
    Dev -->|Multi-platform| DevChoice{Skill level?}
    
    DevChoice -->|Mid-level| DevStudio[Copilot Studio Pro]
    DevChoice -->|Senior| DevSDK[M365 SDK or Foundry]
    
    User --> UserEnd([Start using Copilot])
    MakerStudio --> MakerEnd([Build in Studio])
    MakerPlus --> MakerPlusEnd([Studio + code])
    DevM365 --> DevM365End([Build with SDK])
    DevAzure --> DevAzureEnd([Build in Foundry])
    DS --> DSEnd([Build ML pipeline])
    DevStudio --> DevStudioEnd([Studio with code])
    DevSDK --> DevSDKEnd([Full code solution])
    
    style User fill:#107C10,color:#fff
    style MakerStudio fill:#0078D4,color:#fff
    style MakerPlus fill:#0078D4,color:#fff
    style DevM365 fill:#5C2D91,color:#fff
    style DevAzure fill:#5C2D91,color:#fff
    style DS fill:#D83B01,color:#fff
```

---

## Data Grounding Decision

```mermaid
flowchart TD
    Start([Need to ground AI]) --> Q1{Where is<br/>your data?}
    
    Q1 -->|M365 only| M365Data{Data type?}
    Q1 -->|Azure only| AzureData{Data type?}
    Q1 -->|Both| Hybrid{Primary<br/>location?}
    
    M365Data -->|SharePoint, OneDrive| Graph[Microsoft Graph Connectors]
    M365Data -->|Teams messages| GraphTeams[Graph Connectors]
    M365Data -->|Custom M365 app| GraphCustom[Custom Graph Connector]
    
    AzureData -->|Documents, PDFs| Search[Azure AI Search]
    AzureData -->|Structured DB| DB{Database?}
    AzureData -->|Unstructured| Blob[Blob Storage + AI Search]
    
    DB -->|Global scale| Cosmos[Cosmos DB + Vectors]
    DB -->|Relational| Postgres[PostgreSQL + pgvector]
    DB -->|On-prem/SQL| SQL[SQL Server 2025 VECTOR]
    
    Hybrid -->|M365 primary| HybridM365[Graph + BYOK]
    Hybrid -->|Azure primary| HybridAzure[AI Search + Graph API]
    
    Graph --> Layer{Which<br/>platform?}
    GraphTeams --> Layer
    GraphCustom --> Layer
    Search --> Layer
    Cosmos --> Layer
    Postgres --> Layer
    SQL --> Layer
    Blob --> Layer
    HybridM365 --> Layer
    HybridAzure --> Layer
    
    Layer -->|M365 Copilot| LayerM365([Use built-in])
    Layer -->|Copilot Studio| LayerStudio([Configure Studio])
    Layer -->|M365 SDK| LayerSDK([Code integration])
    Layer -->|Azure Foundry| LayerFoundry([Configure Foundry])
    
    style Graph fill:#0078D4,color:#fff
    style Search fill:#0078D4,color:#fff
    style Cosmos fill:#0078D4,color:#fff
    style Postgres fill:#0078D4,color:#fff
    style SQL fill:#0078D4,color:#fff
```

---

## Complexity Assessment Flow

```mermaid
flowchart TD
    Start([Assess Use Case]) --> Q1{How many<br/>data sources?}
    
    Q1 -->|1| Simple
    Q1 -->|2-3| Q2{Workflow<br/>complexity?}
    Q1 -->|4+| Complex
    
    Q2 -->|Linear| Medium
    Q2 -->|Branching| Complex
    
    Simple[Low Complexity] --> S_Tech{Skills?}
    S_Tech -->|Makers| S_M365[M365 Copilot + Graph]
    S_Tech -->|Devs| S_Studio[Copilot Studio]
    
    Medium[Medium Complexity] --> M_Tech{Skills?}
    M_Tech -->|Makers| M_Studio[Copilot Studio]
    M_Tech -->|Devs| M_SDK[Studio + Custom Actions]
    
    Complex[High Complexity] --> C_Tech{Need custom<br/>models?}
    C_Tech -->|No| C_SDK[M365 Agents SDK]
    C_Tech -->|Yes| C_Foundry[Azure AI Foundry]
    
    S_M365 --> Timeline1[Days to deploy]
    S_Studio --> Timeline2[1-2 weeks]
    M_Studio --> Timeline3[2-4 weeks]
    M_SDK --> Timeline4[1-2 months]
    C_SDK --> Timeline5[2-3 months]
    C_Foundry --> Timeline6[3-6 months]
    
    style Simple fill:#107C10,color:#fff
    style Medium fill:#FFB900,color:#000
    style Complex fill:#D83B01,color:#fff
```

---

## Budget & Timeline Tradeoffs

```mermaid
flowchart TD
    Start([Project Constraints]) --> Q1{Budget<br/>per month?}
    
    Q1 -->|< $500| Low[Low Budget]
    Q1 -->|$500-$2K| Mid[Medium Budget]
    Q1 -->|$2K-$10K| High[High Budget]
    Q1 -->|$10K+| VeryHigh[Enterprise Budget]
    
    Low --> LT{Timeline?}
    LT -->|Days| L_Fast[M365 Copilot<br/>Limited customization]
    LT -->|Weeks| L_Med[Copilot Studio Starter<br/>Low-code only]
    LT -->|Months| L_Slow[Not feasible]
    
    Mid --> MT{Timeline?}
    MT -->|Days| M_Fast[M365 + Graph<br/>Basic grounding]
    MT -->|Weeks| M_Med[Copilot Studio Pro<br/>Good balance]
    MT -->|Months| M_Slow[Studio + Actions<br/>High customization]
    
    High --> HT{Timeline?}
    HT -->|Days| H_Fast[Not realistic]
    HT -->|Weeks| H_Med[M365 SDK Basic<br/>Limited scope]
    HT -->|Months| H_Slow[M365 SDK or Foundry<br/>Full custom]
    
    VeryHigh --> VT{Timeline?}
    VT -->|Days| V_Fast[Not realistic]
    VT -->|Weeks| V_Med[Foundry MVP<br/>Focused scope]
    VT -->|Months| V_Slow[Full Foundry Stack<br/>Complete solution]
    
    style L_Fast fill:#107C10,color:#fff
    style M_Med fill:#107C10,color:#fff
    style M_Slow fill:#107C10,color:#fff
    style H_Slow fill:#107C10,color:#fff
    style V_Slow fill:#107C10,color:#fff
    
    style L_Slow fill:#D83B01,color:#fff
    style H_Fast fill:#D83B01,color:#fff
    style V_Fast fill:#D83B01,color:#fff
```

---

## Governance & Compliance Path

```mermaid
flowchart TD
    Start([Compliance Requirements]) --> Q1{Data<br/>residency<br/>critical?}
    
    Q1 -->|Yes, M365 only| Strict[Strict Governance]
    Q1 -->|Configurable| Medium[Medium Governance]
    Q1 -->|Flexible| Low[Low Governance]
    
    Strict --> S_DLP{Need<br/>DLP?}
    S_DLP -->|Yes| S_M365[M365 Copilot<br/>Built-in DLP]
    S_DLP -->|Custom| S_Studio[Copilot Studio<br/>M365 trust boundary]
    
    Medium --> M_RBAC{RBAC<br/>model?}
    M_RBAC -->|M365 groups| M_Studio[Copilot Studio<br/>M365 + custom RBAC]
    M_RBAC -->|Custom| M_SDK[M365 SDK<br/>Full control]
    
    Low --> L_Scale{Scale<br/>needs?}
    L_Scale -->|< 1K users| L_Studio[Copilot Studio<br/>Fast deployment]
    L_Scale -->|1K-10K users| L_SDK[M365 SDK<br/>Scalable]
    L_Scale -->|10K+ users| L_Foundry[Azure AI Foundry<br/>Enterprise scale]
    
    S_M365 --> Audit1[M365 audit logs]
    S_Studio --> Audit2[Studio analytics]
    M_Studio --> Audit3[Studio + custom]
    M_SDK --> Audit4[Custom telemetry]
    L_Studio --> Audit5[Studio analytics]
    L_SDK --> Audit6[Custom telemetry]
    L_Foundry --> Audit7[Azure Monitor]
    
    style S_M365 fill:#0078D4,color:#fff
    style S_Studio fill:#0078D4,color:#fff
    style M_Studio fill:#0078D4,color:#fff
```

---

## Multi-Agent Orchestration

```mermaid
flowchart TD
    Start([Need Multi-Agent?]) --> Q1{Complexity?}
    
    Q1 -->|Simple handoffs| Simple[Agent Handoffs]
    Q1 -->|Parallel execution| Medium[Multi-Agent Orchestration]
    Q1 -->|Complex workflows| Complex[Advanced Orchestration]
    
    Simple --> S_Platform{Platform?}
    S_Platform -->|Low-code| S_Studio[Copilot Studio<br/>Topics + handoffs]
    S_Platform -->|Code| S_SDK[M365 SDK<br/>Custom routing]
    
    Medium --> M_Framework{Framework?}
    M_Framework -->|Microsoft| M_SDK[M365 SDK<br/>Agent Framework]
    M_Framework -->|Azure| M_Foundry[Azure AI Foundry<br/>Multi-agent]
    M_Framework -->|Open source| M_Lang[LangGraph<br/>Agent graphs]
    
    Complex --> C_Need{Requirements?}
    C_Need -->|State management| C_LangGraph[LangGraph<br/>State graphs]
    C_Need -->|Azure services| C_Agent[Azure AI Agent Service<br/>Preview]
    C_Need -->|Custom| C_Custom[Custom orchestration<br/>Azure AI Foundry]
    
    S_Studio --> Deploy1([Deploy])
    S_SDK --> Deploy2([Deploy])
    M_SDK --> Deploy3([Deploy])
    M_Foundry --> Deploy4([Deploy])
    M_Lang --> Deploy5([Deploy])
    C_LangGraph --> Deploy6([Deploy])
    C_Agent --> Deploy7([Deploy])
    C_Custom --> Deploy8([Deploy])
    
    style Simple fill:#107C10,color:#fff
    style Medium fill:#FFB900,color:#000
    style Complex fill:#D83B01,color:#fff
```

---

## Upgrade Paths

```mermaid
flowchart LR
    M365[M365 Copilot<br/>Built-in AI] -->|Add custom data| Graph[+ Graph Connectors]
    Graph -->|Need workflows| Studio[Migrate to<br/>Copilot Studio]
    
    Studio[Copilot Studio<br/>Low-code] -->|Add Azure data| BYOK[+ BYOK Preview]
    Studio -->|Need code| Actions[+ Custom Actions]
    Actions -->|Complex logic| SDK[Migrate to<br/>M365 SDK]
    
    SDK[M365 Agents SDK<br/>Pro-code M365] -->|Need custom models| Foundry[Add Azure AI<br/>Foundry]
    SDK -->|Multi-agent| LangGraph[+ LangGraph]
    
    Foundry[Azure AI Foundry<br/>Full Azure] -->|Advanced orchestration| Agent[+ Agent Framework]
    Foundry -->|Custom models| BYOM[+ BYOM]
    
    style M365 fill:#0078D4,color:#fff
    style Studio fill:#0078D4,color:#fff
    style SDK fill:#5C2D91,color:#fff
    style Foundry fill:#D83B01,color:#fff
```

---

## Legend

### Decision Nodes

- 🔷 **Diamond:** Decision point requiring evaluation
- 🟦 **Rectangle:** Technology recommendation
- 🔵 **Circle:** Start/End point

### Colors

- **Blue (#0078D4):** Microsoft primary technologies
- **Purple (#5C2D91):** Developer-focused solutions
- **Green (#107C10):** Low complexity / fast path
- **Orange (#FFB900):** Medium complexity
- **Red (#D83B01):** High complexity / enterprise

---

## How to Use These Diagrams

1. **Start with Complete Decision Flow** for full end-to-end guidance
2. **Use Persona-Based Flow** if you know your role
3. **Jump to Data Grounding** if data architecture is your concern
4. **Check Complexity Assessment** to estimate effort
5. **Review Budget & Timeline** to set realistic expectations
6. **Verify Governance Path** for compliance requirements
7. **Explore Multi-Agent** if orchestration is needed
8. **Plan Upgrade Paths** for evolution strategy

---

## Next Steps

**Detailed comparisons:**  
→ [Feature Comparison](feature-comparison.md)

**Real-world examples:**  
→ [Scenarios](scenarios.md)

**Evaluate readiness:**  
→ [Evaluation Criteria](evaluation-criteria.md)

---

**Last Updated:** November 2025  
**Next:** [Resources](resources.md)
