---------

layout: default

title: Visual Frameworklayout: defaultlayout: default

nav_order: 10

description: "Decision tree diagrams with Mermaid visualizations"title: Visual Frameworktitle: Visual Framework

---

nav_order: 10nav_order: 10

# Visual Framework

{: .no_toc }description: "Decision tree diagrams with Mermaid visualizations"description: "Decision tree diagrams with Mermaid visualizations"



Interactive decision trees to guide Microsoft AI technology selection.------

{: .fs-6 .fw-300 }



## Table of contents

{: .no_toc .text-delta }# Visual Framework# Visual Framework



1. TOC{: .no_toc }

{:toc}

> **TODO:** Extract content from README.md Section 12 (lines ~1350-1450)

---

Interactive decision trees to guide Microsoft AI technology selection.

## Complete Decision Flow

{: .fs-6 .fw-300 }**Status:** Stub file created - content needs to be migrated

```mermaid

flowchart TD

    Start([Start: Need AI Solution]) --> Q1{Where should users<br/>experience the AI?}

    ## Table of contents---

    Q1 -->|M365 apps| M365[M365 Copilot]

    Q1 -->|Teams, custom apps| Q2{Build style &<br/>control level?}{: .no_toc .text-delta }

    Q1 -->|Multi-channel| Q2

    ## Migration Instructions

    Q2 -->|Low-code, makers| Studio[Copilot Studio]

    Q2 -->|Pro-code, full control| Q3{Primary<br/>platform?}1. TOC

    

    Q3 -->|M365-centric| SDK[M365 Agents SDK]{:toc}1. Open the original README.md

    Q3 -->|Azure-centric| Foundry[Azure AI Foundry]

    2. Locate the content mentioned above

    M365 --> Data1{Need custom<br/>data sources?}

    Data1 -->|Yes| Graph[Add Graph Connectors]---3. Copy and paste into this file (replace this stub content)

    Data1 -->|No| End1([Deploy])

    Graph --> End14. Verify all cross-references are updated to link to new file structure

    

    Studio --> Data2{Data location?}## Complete Decision Flow5. Test locally with undle exec jekyll serve

    Data2 -->|M365 only| Studio_M365[Use Graph Connectors]

    Data2 -->|Azure + M365| Studio_BYOK[Use BYOK Preview]

    Data2 -->|Complex| Studio_Actions[Custom Actions]

    Studio_M365 --> End2([Deploy])```mermaid---

    Studio_BYOK --> End2

    Studio_Actions --> End2flowchart TD

    

    SDK --> Data3{Data strategy?}    Start([Start: Need AI Solution]) --> Q1{Where should users<br/>experience the AI?}**Navigation:**

    Data3 -->|M365 Graph| SDK_Graph[Graph API]

    Data3 -->|Azure Search| SDK_Search[Integrate Azure AI Search]    - [← Back to Home](../README.md)

    Data3 -->|Custom DB| SDK_DB[Connect Cosmos/PostgreSQL]

    SDK_Graph --> End3([Deploy])    Q1 -->|M365 apps| M365[M365 Copilot]- [View Technologies](technologies.md)

    SDK_Search --> End3

    SDK_DB --> End3    Q1 -->|Teams, custom apps| Q2{Build style &<br/>control level?}- [View Decision Framework](decision-framework.md)

    

    Foundry --> Data4{Grounding pattern?}    Q1 -->|Multi-channel| Q2

    Data4 -->|Document search| Foundry_Search[Azure AI Search]    

    Data4 -->|Database vectors| Foundry_DB[Cosmos/PostgreSQL/SQL]    Q2 -->|Low-code, makers| Studio[Copilot Studio]

    Data4 -->|Custom| Foundry_Custom[Custom embeddings]    Q2 -->|Pro-code, full control| Q3{Primary<br/>platform?}

    Foundry_Search --> End4([Deploy])    

    Foundry_DB --> End4    Q3 -->|M365-centric| SDK[M365 Agents SDK]

    Foundry_Custom --> End4    Q3 -->|Azure-centric| Foundry[Azure AI Foundry]

        

    style M365 fill:#0078D4,color:#fff    M365 --> Data1{Need custom<br/>data sources?}

    style Studio fill:#0078D4,color:#fff    Data1 -->|Yes| Graph[Add Graph Connectors]

    style SDK fill:#0078D4,color:#fff    Data1 -->|No| End1([Deploy])

    style Foundry fill:#0078D4,color:#fff    Graph --> End1

```    

    Studio --> Data2{Data location?}

---    Data2 -->|M365 only| Studio_M365[Use Graph Connectors]

    Data2 -->|Azure + M365| Studio_BYOK[Use BYOK Preview]

## Persona-Based Flow    Data2 -->|Complex| Studio_Actions[Custom Actions]

    Studio_M365 --> End2([Deploy])

```mermaid    Studio_BYOK --> End2

flowchart TD    Studio_Actions --> End2

    Start([Who are you?]) --> P1{Your role?}    

        SDK --> Data3{Data strategy?}

    P1 -->|End user| User[Use M365 Copilot]    Data3 -->|M365 Graph| SDK_Graph[Graph API]

    P1 -->|Business maker| Maker{Dev support?}    Data3 -->|Azure Search| SDK_Search[Integrate Azure AI Search]

    P1 -->|Developer| Dev{Focus area?}    Data3 -->|Custom DB| SDK_DB[Connect Cosmos/PostgreSQL]

    P1 -->|Data scientist| DS[Azure AI Foundry]    SDK_Graph --> End3([Deploy])

        SDK_Search --> End3

    Maker -->|No devs| MakerStudio[Copilot Studio]    SDK_DB --> End3

    Maker -->|Occasional help| MakerPlus[Studio + Custom Actions]    

        Foundry --> Data4{Grounding pattern?}

    Dev -->|M365 integration| DevM365[M365 Agents SDK]    Data4 -->|Document search| Foundry_Search[Azure AI Search]

    Dev -->|Azure services| DevAzure[Azure AI Foundry]    Data4 -->|Database vectors| Foundry_DB[Cosmos/PostgreSQL/SQL]

    Dev -->|Multi-platform| DevChoice{Skill level?}    Data4 -->|Custom| Foundry_Custom[Custom embeddings]

        Foundry_Search --> End4([Deploy])

    DevChoice -->|Mid-level| DevStudio[Copilot Studio Pro]    Foundry_DB --> End4

    DevChoice -->|Senior| DevSDK[M365 SDK or Foundry]    Foundry_Custom --> End4

        

    User --> UserEnd([Start using Copilot])    style M365 fill:#0078D4,color:#fff

    MakerStudio --> MakerEnd([Build in Studio])    style Studio fill:#0078D4,color:#fff

    MakerPlus --> MakerPlusEnd([Studio + code])    style SDK fill:#0078D4,color:#fff

    DevM365 --> DevM365End([Build with SDK])    style Foundry fill:#0078D4,color:#fff

    DevAzure --> DevAzureEnd([Build in Foundry])```

    DS --> DSEnd([Build ML pipeline])

    DevStudio --> DevStudioEnd([Studio with code])---

    DevSDK --> DevSDKEnd([Full code solution])

    ## Persona-Based Flow

    style User fill:#107C10,color:#fff

    style MakerStudio fill:#0078D4,color:#fff```mermaid

    style MakerPlus fill:#0078D4,color:#fffflowchart TD

    style DevM365 fill:#5C2D91,color:#fff    Start([Who are you?]) --> P1{Your role?}

    style DevAzure fill:#5C2D91,color:#fff    

    style DS fill:#D83B01,color:#fff    P1 -->|End user| User[Use M365 Copilot]

```    P1 -->|Business maker| Maker{Dev support?}

    P1 -->|Developer| Dev{Focus area?}

---    P1 -->|Data scientist| DS[Azure AI Foundry]

    

## Data Grounding Decision    Maker -->|No devs| MakerStudio[Copilot Studio]

    Maker -->|Occasional help| MakerPlus[Studio + Custom Actions]

```mermaid    

flowchart TD    Dev -->|M365 integration| DevM365[M365 Agents SDK]

    Start([Need to ground AI]) --> Q1{Where is<br/>your data?}    Dev -->|Azure services| DevAzure[Azure AI Foundry]

        Dev -->|Multi-platform| DevChoice{Skill level?}

    Q1 -->|M365 only| M365Data{Data type?}    

    Q1 -->|Azure only| AzureData{Data type?}    DevChoice -->|Mid-level| DevStudio[Copilot Studio Pro]

    Q1 -->|Both| Hybrid{Primary<br/>location?}    DevChoice -->|Senior| DevSDK[M365 SDK or Foundry]

        

    M365Data -->|SharePoint, OneDrive| Graph[Microsoft Graph Connectors]    User --> UserEnd([Start using Copilot])

    M365Data -->|Teams messages| GraphTeams[Graph Connectors]    MakerStudio --> MakerEnd([Build in Studio])

    M365Data -->|Custom M365 app| GraphCustom[Custom Graph Connector]    MakerPlus --> MakerPlusEnd([Studio + code])

        DevM365 --> DevM365End([Build with SDK])

    AzureData -->|Documents, PDFs| Search[Azure AI Search]    DevAzure --> DevAzureEnd([Build in Foundry])

    AzureData -->|Structured DB| DB{Database?}    DS --> DSEnd([Build ML pipeline])

    AzureData -->|Unstructured| Blob[Blob Storage + AI Search]    DevStudio --> DevStudioEnd([Studio with code])

        DevSDK --> DevSDKEnd([Full code solution])

    DB -->|Global scale| Cosmos[Cosmos DB + Vectors]    

    DB -->|Relational| Postgres[PostgreSQL + pgvector]    style User fill:#107C10,color:#fff

    DB -->|On-prem/SQL| SQL[SQL Server 2025 VECTOR]    style MakerStudio fill:#0078D4,color:#fff

        style MakerPlus fill:#0078D4,color:#fff

    Hybrid -->|M365 primary| HybridM365[Graph + BYOK]    style DevM365 fill:#5C2D91,color:#fff

    Hybrid -->|Azure primary| HybridAzure[AI Search + Graph API]    style DevAzure fill:#5C2D91,color:#fff

        style DS fill:#D83B01,color:#fff

    Graph --> Layer{Which<br/>platform?}```

    GraphTeams --> Layer

    GraphCustom --> Layer---

    Search --> Layer

    Cosmos --> Layer## Data Grounding Decision

    Postgres --> Layer

    SQL --> Layer```mermaid

    Blob --> Layerflowchart TD

    HybridM365 --> Layer    Start([Need to ground AI]) --> Q1{Where is<br/>your data?}

    HybridAzure --> Layer    

        Q1 -->|M365 only| M365Data{Data type?}

    Layer -->|M365 Copilot| LayerM365([Use built-in])    Q1 -->|Azure only| AzureData{Data type?}

    Layer -->|Copilot Studio| LayerStudio([Configure Studio])    Q1 -->|Both| Hybrid{Primary<br/>location?}

    Layer -->|M365 SDK| LayerSDK([Code integration])    

    Layer -->|Azure Foundry| LayerFoundry([Configure Foundry])    M365Data -->|SharePoint, OneDrive| Graph[Microsoft Graph Connectors]

        M365Data -->|Teams messages| GraphTeams[Graph Connectors]

    style Graph fill:#0078D4,color:#fff    M365Data -->|Custom M365 app| GraphCustom[Custom Graph Connector]

    style Search fill:#0078D4,color:#fff    

    style Cosmos fill:#0078D4,color:#fff    AzureData -->|Documents, PDFs| Search[Azure AI Search]

    style Postgres fill:#0078D4,color:#fff    AzureData -->|Structured DB| DB{Database?}

    style SQL fill:#0078D4,color:#fff    AzureData -->|Unstructured| Blob[Blob Storage + AI Search]

```    

    DB -->|Global scale| Cosmos[Cosmos DB + Vectors]

---    DB -->|Relational| Postgres[PostgreSQL + pgvector]

    DB -->|On-prem/SQL| SQL[SQL Server 2025 VECTOR]

## Complexity Assessment Flow    

    Hybrid -->|M365 primary| HybridM365[Graph + BYOK]

```mermaid    Hybrid -->|Azure primary| HybridAzure[AI Search + Graph API]

flowchart TD    

    Start([Assess Use Case]) --> Q1{How many<br/>data sources?}    Graph --> Layer{Which<br/>platform?}

        GraphTeams --> Layer

    Q1 -->|1| Simple    GraphCustom --> Layer

    Q1 -->|2-3| Q2{Workflow<br/>complexity?}    Search --> Layer

    Q1 -->|4+| Complex    Cosmos --> Layer

        Postgres --> Layer

    Q2 -->|Linear| Medium    SQL --> Layer

    Q2 -->|Branching| Complex    Blob --> Layer

        HybridM365 --> Layer

    Simple[Low Complexity] --> S_Tech{Skills?}    HybridAzure --> Layer

    S_Tech -->|Makers| S_M365[M365 Copilot + Graph]    

    S_Tech -->|Devs| S_Studio[Copilot Studio]    Layer -->|M365 Copilot| LayerM365([Use built-in])

        Layer -->|Copilot Studio| LayerStudio([Configure Studio])

    Medium[Medium Complexity] --> M_Tech{Skills?}    Layer -->|M365 SDK| LayerSDK([Code integration])

    M_Tech -->|Makers| M_Studio[Copilot Studio]    Layer -->|Azure Foundry| LayerFoundry([Configure Foundry])

    M_Tech -->|Devs| M_SDK[Studio + Custom Actions]    

        style Graph fill:#0078D4,color:#fff

    Complex[High Complexity] --> C_Tech{Need custom<br/>models?}    style Search fill:#0078D4,color:#fff

    C_Tech -->|No| C_SDK[M365 Agents SDK]    style Cosmos fill:#0078D4,color:#fff

    C_Tech -->|Yes| C_Foundry[Azure AI Foundry]    style Postgres fill:#0078D4,color:#fff

        style SQL fill:#0078D4,color:#fff

    S_M365 --> Timeline1[Days to deploy]```

    S_Studio --> Timeline2[1-2 weeks]

    M_Studio --> Timeline3[2-4 weeks]---

    M_SDK --> Timeline4[1-2 months]

    C_SDK --> Timeline5[2-3 months]## Complexity Assessment Flow

    C_Foundry --> Timeline6[3-6 months]

    ```mermaid

    style Simple fill:#107C10,color:#fffflowchart TD

    style Medium fill:#FFB900,color:#000    Start([Assess Use Case]) --> Q1{How many<br/>data sources?}

    style Complex fill:#D83B01,color:#fff    

```    Q1 -->|1| Simple

    Q1 -->|2-3| Q2{Workflow<br/>complexity?}

---    Q1 -->|4+| Complex

    

## Budget & Timeline Tradeoffs    Q2 -->|Linear| Medium

    Q2 -->|Branching| Complex

```mermaid    

flowchart TD    Simple[Low Complexity] --> S_Tech{Skills?}

    Start([Project Constraints]) --> Q1{Budget<br/>per month?}    S_Tech -->|Makers| S_M365[M365 Copilot + Graph]

        S_Tech -->|Devs| S_Studio[Copilot Studio]

    Q1 -->|< $500| Low[Low Budget]    

    Q1 -->|$500-$2K| Mid[Medium Budget]    Medium[Medium Complexity] --> M_Tech{Skills?}

    Q1 -->|$2K-$10K| High[High Budget]    M_Tech -->|Makers| M_Studio[Copilot Studio]

    Q1 -->|$10K+| VeryHigh[Enterprise Budget]    M_Tech -->|Devs| M_SDK[Studio + Custom Actions]

        

    Low --> LT{Timeline?}    Complex[High Complexity] --> C_Tech{Need custom<br/>models?}

    LT -->|Days| L_Fast[M365 Copilot<br/>Limited customization]    C_Tech -->|No| C_SDK[M365 Agents SDK]

    LT -->|Weeks| L_Med[Copilot Studio Starter<br/>Low-code only]    C_Tech -->|Yes| C_Foundry[Azure AI Foundry]

    LT -->|Months| L_Slow[Not feasible]    

        S_M365 --> Timeline1[Days to deploy]

    Mid --> MT{Timeline?}    S_Studio --> Timeline2[1-2 weeks]

    MT -->|Days| M_Fast[M365 + Graph<br/>Basic grounding]    M_Studio --> Timeline3[2-4 weeks]

    MT -->|Weeks| M_Med[Copilot Studio Pro<br/>Good balance]    M_SDK --> Timeline4[1-2 months]

    MT -->|Months| M_Slow[Studio + Actions<br/>High customization]    C_SDK --> Timeline5[2-3 months]

        C_Foundry --> Timeline6[3-6 months]

    High --> HT{Timeline?}    

    HT -->|Days| H_Fast[Not realistic]    style Simple fill:#107C10,color:#fff

    HT -->|Weeks| H_Med[M365 SDK Basic<br/>Limited scope]    style Medium fill:#FFB900,color:#000

    HT -->|Months| H_Slow[M365 SDK or Foundry<br/>Full custom]    style Complex fill:#D83B01,color:#fff

    ```

    VeryHigh --> VT{Timeline?}

    VT -->|Days| V_Fast[Not realistic]---

    VT -->|Weeks| V_Med[Foundry MVP<br/>Focused scope]

    VT -->|Months| V_Slow[Full Foundry Stack<br/>Complete solution]## Budget & Timeline Tradeoffs

    

    style L_Fast fill:#107C10,color:#fff```mermaid

    style M_Med fill:#107C10,color:#fffflowchart TD

    style M_Slow fill:#107C10,color:#fff    Start([Project Constraints]) --> Q1{Budget<br/>per month?}

    style H_Slow fill:#107C10,color:#fff    

    style V_Slow fill:#107C10,color:#fff    Q1 -->|< $500| Low[Low Budget]

        Q1 -->|$500-$2K| Mid[Medium Budget]

    style L_Slow fill:#D83B01,color:#fff    Q1 -->|$2K-$10K| High[High Budget]

    style H_Fast fill:#D83B01,color:#fff    Q1 -->|$10K+| VeryHigh[Enterprise Budget]

    style V_Fast fill:#D83B01,color:#fff    

```    Low --> LT{Timeline?}

    LT -->|Days| L_Fast[M365 Copilot<br/>Limited customization]

---    LT -->|Weeks| L_Med[Copilot Studio Starter<br/>Low-code only]

    LT -->|Months| L_Slow[Not feasible]

## Governance & Compliance Path    

    Mid --> MT{Timeline?}

```mermaid    MT -->|Days| M_Fast[M365 + Graph<br/>Basic grounding]

flowchart TD    MT -->|Weeks| M_Med[Copilot Studio Pro<br/>Good balance]

    Start([Compliance Requirements]) --> Q1{Data<br/>residency<br/>critical?}    MT -->|Months| M_Slow[Studio + Actions<br/>High customization]

        

    Q1 -->|Yes, M365 only| Strict[Strict Governance]    High --> HT{Timeline?}

    Q1 -->|Configurable| Medium[Medium Governance]    HT -->|Days| H_Fast[Not realistic]

    Q1 -->|Flexible| Low[Low Governance]    HT -->|Weeks| H_Med[M365 SDK Basic<br/>Limited scope]

        HT -->|Months| H_Slow[M365 SDK or Foundry<br/>Full custom]

    Strict --> S_DLP{Need<br/>DLP?}    

    S_DLP -->|Yes| S_M365[M365 Copilot<br/>Built-in DLP]    VeryHigh --> VT{Timeline?}

    S_DLP -->|Custom| S_Studio[Copilot Studio<br/>M365 trust boundary]    VT -->|Days| V_Fast[Not realistic]

        VT -->|Weeks| V_Med[Foundry MVP<br/>Focused scope]

    Medium --> M_RBAC{RBAC<br/>model?}    VT -->|Months| V_Slow[Full Foundry Stack<br/>Complete solution]

    M_RBAC -->|M365 groups| M_Studio[Copilot Studio<br/>M365 + custom RBAC]    

    M_RBAC -->|Custom| M_SDK[M365 SDK<br/>Full control]    style L_Fast fill:#107C10,color:#fff

        style M_Med fill:#107C10,color:#fff

    Low --> L_Scale{Scale<br/>needs?}    style M_Slow fill:#107C10,color:#fff

    L_Scale -->|< 1K users| L_Studio[Copilot Studio<br/>Fast deployment]    style H_Slow fill:#107C10,color:#fff

    L_Scale -->|1K-10K users| L_SDK[M365 SDK<br/>Scalable]    style V_Slow fill:#107C10,color:#fff

    L_Scale -->|10K+ users| L_Foundry[Azure AI Foundry<br/>Enterprise scale]    

        style L_Slow fill:#D83B01,color:#fff

    S_M365 --> Audit1[M365 audit logs]    style H_Fast fill:#D83B01,color:#fff

    S_Studio --> Audit2[Studio analytics]    style V_Fast fill:#D83B01,color:#fff

    M_Studio --> Audit3[Studio + custom]```

    M_SDK --> Audit4[Custom telemetry]

    L_Studio --> Audit5[Studio analytics]---

    L_SDK --> Audit6[Custom telemetry]

    L_Foundry --> Audit7[Azure Monitor]## Governance & Compliance Path

    

    style S_M365 fill:#0078D4,color:#fff```mermaid

    style S_Studio fill:#0078D4,color:#fffflowchart TD

    style M_Studio fill:#0078D4,color:#fff    Start([Compliance Requirements]) --> Q1{Data<br/>residency<br/>critical?}

```    

    Q1 -->|Yes, M365 only| Strict[Strict Governance]

---    Q1 -->|Configurable| Medium[Medium Governance]

    Q1 -->|Flexible| Low[Low Governance]

## Multi-Agent Orchestration    

    Strict --> S_DLP{Need<br/>DLP?}

```mermaid    S_DLP -->|Yes| S_M365[M365 Copilot<br/>Built-in DLP]

flowchart TD    S_DLP -->|Custom| S_Studio[Copilot Studio<br/>M365 trust boundary]

    Start([Need Multi-Agent?]) --> Q1{Complexity?}    

        Medium --> M_RBAC{RBAC<br/>model?}

    Q1 -->|Simple handoffs| Simple[Agent Handoffs]    M_RBAC -->|M365 groups| M_Studio[Copilot Studio<br/>M365 + custom RBAC]

    Q1 -->|Parallel execution| Medium[Multi-Agent Orchestration]    M_RBAC -->|Custom| M_SDK[M365 SDK<br/>Full control]

    Q1 -->|Complex workflows| Complex[Advanced Orchestration]    

        Low --> L_Scale{Scale<br/>needs?}

    Simple --> S_Platform{Platform?}    L_Scale -->|< 1K users| L_Studio[Copilot Studio<br/>Fast deployment]

    S_Platform -->|Low-code| S_Studio[Copilot Studio<br/>Topics + handoffs]    L_Scale -->|1K-10K users| L_SDK[M365 SDK<br/>Scalable]

    S_Platform -->|Code| S_SDK[M365 SDK<br/>Custom routing]    L_Scale -->|10K+ users| L_Foundry[Azure AI Foundry<br/>Enterprise scale]

        

    Medium --> M_Framework{Framework?}    S_M365 --> Audit1[M365 audit logs]

    M_Framework -->|Microsoft| M_SDK[M365 SDK<br/>Agent Framework]    S_Studio --> Audit2[Studio analytics]

    M_Framework -->|Azure| M_Foundry[Azure AI Foundry<br/>Multi-agent]    M_Studio --> Audit3[Studio + custom]

    M_Framework -->|Open source| M_Lang[LangGraph<br/>Agent graphs]    M_SDK --> Audit4[Custom telemetry]

        L_Studio --> Audit5[Studio analytics]

    Complex --> C_Need{Requirements?}    L_SDK --> Audit6[Custom telemetry]

    C_Need -->|State management| C_LangGraph[LangGraph<br/>State graphs]    L_Foundry --> Audit7[Azure Monitor]

    C_Need -->|Azure services| C_Agent[Azure AI Agent Service<br/>Preview]    

    C_Need -->|Custom| C_Custom[Custom orchestration<br/>Azure AI Foundry]    style S_M365 fill:#0078D4,color:#fff

        style S_Studio fill:#0078D4,color:#fff

    S_Studio --> Deploy1([Deploy])    style M_Studio fill:#0078D4,color:#fff

    S_SDK --> Deploy2([Deploy])```

    M_SDK --> Deploy3([Deploy])

    M_Foundry --> Deploy4([Deploy])---

    M_Lang --> Deploy5([Deploy])

    C_LangGraph --> Deploy6([Deploy])## Multi-Agent Orchestration

    C_Agent --> Deploy7([Deploy])

    C_Custom --> Deploy8([Deploy])```mermaid

    flowchart TD

    style Simple fill:#107C10,color:#fff    Start([Need Multi-Agent?]) --> Q1{Complexity?}

    style Medium fill:#FFB900,color:#000    

    style Complex fill:#D83B01,color:#fff    Q1 -->|Simple handoffs| Simple[Agent Handoffs]

```    Q1 -->|Parallel execution| Medium[Multi-Agent Orchestration]

    Q1 -->|Complex workflows| Complex[Advanced Orchestration]

---    

    Simple --> S_Platform{Platform?}

## Upgrade Paths    S_Platform -->|Low-code| S_Studio[Copilot Studio<br/>Topics + handoffs]

    S_Platform -->|Code| S_SDK[M365 SDK<br/>Custom routing]

```mermaid    

flowchart LR    Medium --> M_Framework{Framework?}

    M365[M365 Copilot<br/>Built-in AI] -->|Add custom data| Graph[+ Graph Connectors]    M_Framework -->|Microsoft| M_SDK[M365 SDK<br/>Agent Framework]

    Graph -->|Need workflows| Studio[Migrate to<br/>Copilot Studio]    M_Framework -->|Azure| M_Foundry[Azure AI Foundry<br/>Multi-agent]

        M_Framework -->|Open source| M_Lang[LangGraph<br/>Agent graphs]

    Studio[Copilot Studio<br/>Low-code] -->|Add Azure data| BYOK[+ BYOK Preview]    

    Studio -->|Need code| Actions[+ Custom Actions]    Complex --> C_Need{Requirements?}

    Actions -->|Complex logic| SDK[Migrate to<br/>M365 SDK]    C_Need -->|State management| C_LangGraph[LangGraph<br/>State graphs]

        C_Need -->|Azure services| C_Agent[Azure AI Agent Service<br/>Preview]

    SDK[M365 Agents SDK<br/>Pro-code M365] -->|Need custom models| Foundry[Add Azure AI<br/>Foundry]    C_Need -->|Custom| C_Custom[Custom orchestration<br/>Azure AI Foundry]

    SDK -->|Multi-agent| LangGraph[+ LangGraph]    

        S_Studio --> Deploy1([Deploy])

    Foundry[Azure AI Foundry<br/>Full Azure] -->|Advanced orchestration| Agent[+ Agent Framework]    S_SDK --> Deploy2([Deploy])

    Foundry -->|Custom models| BYOM[+ BYOM]    M_SDK --> Deploy3([Deploy])

        M_Foundry --> Deploy4([Deploy])

    style M365 fill:#0078D4,color:#fff    M_Lang --> Deploy5([Deploy])

    style Studio fill:#0078D4,color:#fff    C_LangGraph --> Deploy6([Deploy])

    style SDK fill:#5C2D91,color:#fff    C_Agent --> Deploy7([Deploy])

    style Foundry fill:#D83B01,color:#fff    C_Custom --> Deploy8([Deploy])

```    

    style Simple fill:#107C10,color:#fff

---    style Medium fill:#FFB900,color:#000

    style Complex fill:#D83B01,color:#fff

## Legend```



### Decision Nodes---



- 🔷 **Diamond:** Decision point requiring evaluation## Upgrade Paths

- 🟦 **Rectangle:** Technology recommendation

- 🔵 **Circle:** Start/End point```mermaid

flowchart LR

### Colors    M365[M365 Copilot<br/>Built-in AI] -->|Add custom data| Graph[+ Graph Connectors]

    Graph -->|Need workflows| Studio[Migrate to<br/>Copilot Studio]

- **Blue (#0078D4):** Microsoft primary technologies    

- **Purple (#5C2D91):** Developer-focused solutions    Studio[Copilot Studio<br/>Low-code] -->|Add Azure data| BYOK[+ BYOK Preview]

- **Green (#107C10):** Low complexity / fast path    Studio -->|Need code| Actions[+ Custom Actions]

- **Orange (#FFB900):** Medium complexity    Actions -->|Complex logic| SDK[Migrate to<br/>M365 SDK]

- **Red (#D83B01):** High complexity / enterprise    

    SDK[M365 Agents SDK<br/>Pro-code M365] -->|Need custom models| Foundry[Add Azure AI<br/>Foundry]

---    SDK -->|Multi-agent| LangGraph[+ LangGraph]

    

## How to Use These Diagrams    Foundry[Azure AI Foundry<br/>Full Azure] -->|Advanced orchestration| Agent[+ Agent Framework]

    Foundry -->|Custom models| BYOM[+ BYOM]

1. **Start with Complete Decision Flow** for full end-to-end guidance    

2. **Use Persona-Based Flow** if you know your role    style M365 fill:#0078D4,color:#fff

3. **Jump to Data Grounding** if data architecture is your concern    style Studio fill:#0078D4,color:#fff

4. **Check Complexity Assessment** to estimate effort    style SDK fill:#5C2D91,color:#fff

5. **Review Budget & Timeline** to set realistic expectations    style Foundry fill:#D83B01,color:#fff

6. **Verify Governance Path** for compliance requirements```

7. **Explore Multi-Agent** if orchestration is needed

8. **Plan Upgrade Paths** for evolution strategy---



---## Legend



## Next Steps### Decision Nodes

- 🔷 **Diamond:** Decision point requiring evaluation

**Detailed comparisons:**  - 🟦 **Rectangle:** Technology recommendation

→ [Feature Comparison](feature-comparison.md)- 🔵 **Circle:** Start/End point



**Real-world examples:**  ### Colors

→ [Scenarios](scenarios.md)- **Blue (#0078D4):** Microsoft primary technologies

- **Purple (#5C2D91):** Developer-focused solutions

**Evaluate readiness:**  - **Green (#107C10):** Low complexity / fast path

→ [Evaluation Criteria](evaluation-criteria.md)- **Orange (#FFB900):** Medium complexity

- **Red (#D83B01):** High complexity / enterprise

---

---

**Last Updated:** November 2025  

**Next:** [Resources](resources.md)## How to Use These Diagrams


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
