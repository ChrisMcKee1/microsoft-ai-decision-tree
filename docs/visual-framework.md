---
layout: default
title: Visual Framework
nav_order: 5
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

## About This Visual Framework

These diagrams provide **visual representations** of the [Decision Framework](decision-framework.md) methodology, helping you navigate Microsoft's AI portfolio through interactive flowcharts.

### Optimal Learning Path

Follow this sequence through the documentation for the best learning experience:

```mermaid
%%{init: {'theme':'dark', 'themeVariables': {'fontSize':'16px'}}}%%
flowchart LR
    Start([Start Here]) --> CM[📚 Capability Model<br/>Five-Layer Architecture]
    CM --> DF[🎯 Decision Framework<br/>BXT Methodology]
    DF --> SC[💼 Scenarios<br/>Real-World Examples]
    SC --> VF[📊 Visual Framework<br/>Interactive Diagrams]
    VF --> EC[✅ Evaluation Criteria<br/>Assess Requirements]
    EC --> IP[🏗️ Implementation Patterns<br/>Build Guidance]
    IP --> TECH[🔧 Technologies<br/>Technical Deep Dive]
    TECH --> FC[📋 Feature Comparison<br/>Side-by-Side Matrices]
    
    %% Reference materials (not in main flow)
    FC -.-> QR[⚡ Quick Reference]
    FC -.-> RES[🔗 Resources]
    FC -.-> GLOSS[📖 Glossary]
    
    style Start fill:#4CAF50,stroke:#2E7D32,color:#fff
    style VF fill:#2196F3,stroke:#1565C0,color:#fff
    style QR fill:#9E9E9E,stroke:#616161,color:#fff
    style RES fill:#9E9E9E,stroke:#616161,color:#fff
    style GLOSS fill:#9E9E9E,stroke:#616161,color:#fff
    
    classDef mainPath fill:#1976D2,stroke:#0D47A1,color:#fff
    class CM,DF,SC,EC,IP,TECH,FC mainPath
```

**📌 Main Learning Path** (blue): Foundation → Context → Application → Assessment → Execution → Reference  
**📎 Reference Materials** (gray, dotted): Quick Reference, Resources, Glossary - use as needed, not part of sequential flow

### How This Connects to the Complete Framework

| **You Are Here** | **This Provides** | **Complements** |
|------------------|-------------------|-----------------|
| **Visual Framework** | Decision tree diagrams | [Decision Framework](decision-framework.md) - Written methodology (BXT + 6 Questions) |
| | Technology selection paths | [Scenarios](scenarios.md) - Real-world examples with step-by-step guidance |
| | Complexity/budget/governance views | [Evaluation Criteria](evaluation-criteria.md) - Assessment frameworks and checklists |
| | Multi-agent orchestration patterns | [Quick Reference](quick-reference.md) - Fast-lookup tables for common needs |
| | Upgrade path visualization | [Capability Model](capability-model.md) - Five architectural layers |

### Navigation Guide

**🎯 If you're a visual learner:** Start here with the diagrams  
**📖 If you prefer written guidance:** Start with [Decision Framework](decision-framework.md)  
**🔍 If you need fast answers:** Jump to [Quick Reference](quick-reference.md)  
**💼 If you have a specific use case:** See [Scenarios](scenarios.md)  
**🏗️ If you need architecture context:** Review [Capability Model](capability-model.md)

---

## Diagram Index

| Diagram | Purpose | Maps To Framework |
|---------|---------|-------------------|
| **1. Complete Decision Flow** | End-to-end technology selection | [Phase 2: Q1-Q6](decision-framework.md#phase-2-technology-groupings-six-critical-questions) - All six critical questions |
| **2. Data Grounding Decision** | Data strategy and knowledge sources | [Phase 2: Q4](decision-framework.md#question-4-data-strategy--knowledge) - Data grounding patterns |
| **3. Persona-Based Flow** | Selection by role and skill level | [Phase 2: Q2](decision-framework.md#question-2-build-style--control-level) - Build approach + [Scenarios](scenarios.md) |
| **4. Complexity Assessment** | Technical complexity evaluation | [Evaluation Criteria: Complexity](evaluation-criteria.md#1-technical-complexity-assessment) |
| **5. Budget & Timeline** | Cost and time-to-production paths | [Evaluation Criteria: Budget & Time](evaluation-criteria.md#3-budget-assessment) |
| **6. Governance & Compliance** | Security and compliance requirements | [Evaluation Criteria: Governance](evaluation-criteria.md#5-governance--compliance) |
| **7. Multi-Agent Orchestration** | Multi-agent patterns and frameworks | [Quick Reference: Orchestration Complexity](quick-reference.md#orchestration-complexity-decision-matrix) |
| **8. Upgrade Paths** | Migration and enhancement options | [Capability Model: Layers 1-3](capability-model.md) - Technology progression |

---

## Complete Decision Flow

```mermaid
flowchart TD
    Start([Start: Need AI Solution]) --> Q1{User interaction<br/>pattern?}
    
    Q1 -->|Conversational/Chat UI| UI_Path[UI-Based Agent]
    Q1 -->|Autonomous/Event-driven| Auto_Path[Autonomous Agent]
    Q1 -->|API/Headless Service| API_Path[Headless Service]
    
    UI_Path --> Q2{Where will users<br/>interact?}
    Q2 -->|M365 apps only| M365[M365 Copilot]
    Q2 -->|Teams + custom| Q3{Build approach?}
    Q2 -->|Multi-channel| Q3
    
    Q3 -->|Low-code| Studio[Copilot Studio]
    Q3 -->|Pro-code| Q4{Primary platform?}
    
    Q4 -->|M365-centric| SDK[M365 Agents SDK]
    Q4 -->|Azure-centric| Foundry[Azure AI Foundry]
    
    Auto_Path --> Q5{Primary workflow type?}
    Q5 -->|Enterprise integration| LogicApps[Azure Logic Apps<br/>AI Agent Workflows<br/><i>Preview</i>]
    Q5 -->|Custom orchestration| Foundry
    
    API_Path --> Q6{Hosting preference?}
    Q6 -->|Managed PaaS| AgentService[Azure AI Agent Service]
    Q6 -->|Self-hosted| Foundry
    
    M365 --> DataQ{Need custom data?}
    Studio --> DataQ
    SDK --> DataQ
    Foundry --> DataQ
    LogicApps --> DataQ
    AgentService --> DataQ
    
    DataQ -->|M365 data| GraphConn[Graph Connectors]
    DataQ -->|Documents| AISearch[Azure AI Search]
    DataQ -->|Structured data| VectorDB{Vector DB choice?}
    DataQ -->|Analytics data| Fabric[Microsoft Fabric]
    DataQ -->|No grounding| DirectDeploy
    
    VectorDB -->|Global scale NoSQL| CosmosDB[Cosmos DB<br/>IVF/HNSW/DiskANN]
    VectorDB -->|Relational| PostgreSQL[PostgreSQL<br/>pgvector]
    VectorDB -->|Enterprise SQL| SQLServer[SQL Server 2025<br/>VECTOR <i>Preview</i>]
    
    GraphConn --> DeployConfig
    AISearch --> DeployConfig
    CosmosDB --> DeployConfig
    PostgreSQL --> DeployConfig
    SQLServer --> DeployConfig
    Fabric --> DeployConfig
    DirectDeploy --> DeployConfig
    
    DeployConfig[Configure Deployment] --> Q7{Deployment needs?}
    Q7 -->|M365 Copilot| Deploy_M365[Publish to M365 Copilot]
    Q7 -->|Teams| Deploy_Teams[Publish to Teams]
    Q7 -->|Web/Mobile| Deploy_Web[Web/Mobile Channels]
    Q7 -->|Multiple channels| Deploy_Multi[Multi-channel:<br/>10+ channels via SDK]
    Q7 -->|Azure service| Deploy_Azure[Azure Container Apps/<br/>App Service/AKS]
    
    Deploy_M365 --> Monitor[Monitor & Govern]
    Deploy_Teams --> Monitor
    Deploy_Web --> Monitor
    Deploy_Multi --> Monitor
    Deploy_Azure --> Monitor
    
    Monitor --> End([Production])
    
    style M365 fill:#0078D4,color:#fff
    style Studio fill:#0078D4,color:#fff
    style SDK fill:#5C2D91,color:#fff
    style Foundry fill:#D83B01,color:#fff
    style LogicApps fill:#0078D4,color:#fff
    style AgentService fill:#D83B01,color:#fff
```

### Validation Summary

**Last Validated:** November 2025

**Key Changes from Validation:**
- **Removed:** Fabric Data Agents from Autonomous path (validated as conversational Q&A tool, not autonomous agent)
- **Added Preview Status:** Logic Apps AI Agent Workflows, SQL Server 2025 VECTOR

**Validated Technologies:**

*UI-Based Agents (GA unless noted):*
- **M365 Copilot:** Conversational chat in M365 apps [(docs)](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/)
- **Copilot Studio:** Low-code, 13+ channels [(docs)](https://learn.microsoft.com/en-us/microsoft-copilot-studio/fundamentals-what-is-copilot-studio)
- **M365 Agents SDK:** Pro-code, 10+ channels, C#/JS/Python [(docs)](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agents-sdk-overview)
- **Azure AI Foundry:** Custom UI deployment [(docs)](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/how-to/use-web-app)

*Autonomous Agents:*
- **Logic Apps AI Agent Workflows (Preview):** Event-driven, 1,400+ connectors [(docs)](https://learn.microsoft.com/en-us/azure/logic-apps/agent-workflows-concepts)
- **Azure AI Foundry Agent Service:** Custom orchestration [(docs)](https://learn.microsoft.com/en-us/azure/ai-foundry/agents/overview)

*API/Headless Services (GA):*
- **Azure AI Agent Service:** REST API, managed PaaS [(docs)](https://learn.microsoft.com/en-us/azure/ai-foundry/agents/quickstart)
- **Azure AI Foundry:** REST API deployment [(docs)](https://learn.microsoft.com/en-us/rest/api/aifoundry/)

*Vector Databases:*
- **Cosmos DB (GA):** IVF, HNSW, DiskANN algorithms [(docs)](https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/vector-search)
- **PostgreSQL pgvector (GA):** Extension 0.7.0 [(docs)](https://learn.microsoft.com/en-us/azure/postgresql/flexible-server/how-to-use-pgvector)
- **SQL Server 2025 VECTOR (Preview):** Native type, float32/float16 [(docs)](https://learn.microsoft.com/en-us/sql/t-sql/data-types/vector-data-type)

---

## Persona-Based Flow

```mermaid
flowchart TD
    Start([Who are you?]) --> P1{Your role?}
    
    P1 -->|End user| User[Use M365 Copilot]
    P1 -->|Business maker| Maker{Dev support?}
    P1 -->|Developer| Dev{Focus area?}
    P1 -->|Data scientist/analyst| DS{Primary workload?}
    P1 -->|Integration specialist| IntSpec[Azure Logic Apps<br/>AI Agent Workflows<br/><i>Preview</i>]
    
    Maker -->|No devs| MakerStudio[Copilot Studio]
    Maker -->|Occasional help| MakerPlus[Studio + Custom Actions]
    
    Dev -->|M365 integration| DevM365[M365 Agents SDK]
    Dev -->|Azure services| DevAzure[Azure AI Foundry]
    Dev -->|Multi-platform| DevChoice{Skill level?}
    Dev -->|Autonomous agents| DevAuto{Event-driven?}
    
    DevChoice -->|Mid-level| DevStudio[Copilot Studio<br/>+ Custom Actions]
    DevChoice -->|Senior| DevSDK[M365 SDK or Foundry]
    
    DevAuto -->|Yes| DevLogic[Logic Apps<br/>AI Agent Workflows<br/><i>Preview</i>]
    DevAuto -->|Custom orchestration| DevFoundry[Azure AI Foundry<br/>+ Agent Service]
    
    DS -->|Analytics/BI| DSFabric[Fabric Data Agents<br/><i>Preview</i>]
    DS -->|ML/Custom models| DSFoundry[Azure AI Foundry]
    
    User --> UserEnd([Start using Copilot])
    MakerStudio --> MakerEnd([Build in Studio])
    MakerPlus --> MakerPlusEnd([Studio + code])
    DevM365 --> DevM365End([Build with SDK])
    DevAzure --> DevAzureEnd([Build in Foundry])
    DevStudio --> DevStudioEnd([Studio with code])
    DevSDK --> DevSDKEnd([Full code solution])
    DevLogic --> DevLogicEnd([Event-driven agent])
    DevFoundry --> DevFoundryEnd([Custom agent])
    DSFabric --> DSFabricEnd([Data agent])
    DSFoundry --> DSFoundryEnd([ML pipeline])
    IntSpec --> IntSpecEnd([Enterprise workflows])
    
    style User fill:#107C10,color:#fff
    style MakerStudio fill:#0078D4,color:#fff
    style MakerPlus fill:#0078D4,color:#fff
    style DevM365 fill:#5C2D91,color:#fff
    style DevAzure fill:#5C2D91,color:#fff
    style DevLogic fill:#0078D4,color:#fff
    style DevFoundry fill:#D83B01,color:#fff
    style DSFabric fill:#FFB900,color:#000
    style DSFoundry fill:#D83B01,color:#fff
    style IntSpec fill:#0078D4,color:#fff
```

### Validation Summary - Persona-Based Flow
**Last Validated:** November 3, 2025

**Key Changes:**
- Added Preview annotations to Logic Apps AI Agent Workflows and Fabric Data Agents
- Corrected "Copilot Studio Pro" to "Copilot Studio + Custom Actions" (no official "Pro" tier)
- Validated persona assignments against official Microsoft documentation

**Persona-to-Technology Mappings:**

*End User (GA):*
- **M365 Copilot:** Built-in AI in M365 apps, no setup required - [M365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/)

*Business Maker (GA):*
- **Copilot Studio:** Low-code platform, no dev support needed - [Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/fundamentals-what-is-copilot-studio)
- **Copilot Studio + Custom Actions:** Low-code with occasional developer support for custom connectors/flows - [Custom Actions](https://learn.microsoft.com/en-us/microsoft-copilot-studio/copilot-plugins-overview)

*Developer (GA unless noted):*
- **M365 Agents SDK:** Pro-code for M365-centric solutions, C#/JavaScript/Python, 10+ channels - [M365 Agents SDK](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-custom-engine-agent)
- **Azure AI Foundry:** Pro-code for Azure-centric solutions, custom models, full control - [Azure AI Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry)
- **Copilot Studio + Custom Actions:** Mid-level developers, low-code with custom code extensibility - [Copilot Studio Extensibility](https://learn.microsoft.com/en-us/microsoft-copilot-studio/copilot-plugins-overview)
- **Logic Apps AI Agent Workflows (Preview):** Event-driven autonomous agents, 1,400+ connectors - [Logic Apps Agent Workflows](https://learn.microsoft.com/en-us/azure/logic-apps/agent-workflows-concepts)

*Data Scientist/Analyst:*
- **Fabric Data Agents (Preview):** Analytics/BI focus, Python SDK, evaluation capabilities, Power BI/semantic models - [Fabric Data Agents](https://learn.microsoft.com/en-us/fabric/data-science/concept-data-agent) | [Python SDK](https://learn.microsoft.com/en-us/fabric/data-science/evaluate-data-agent)
- **Azure AI Foundry (GA):** ML/custom models, full AI/ML pipeline control - [Azure AI Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry)

*Integration Specialist:*
- **Logic Apps AI Agent Workflows (Preview):** Enterprise integration focus, 1,400+ connectors, workflow automation - [Logic Apps Overview](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-overview) | [AI Agent Workflows](https://learn.microsoft.com/en-us/azure/logic-apps/agent-workflows-concepts)

---

## Data Grounding Decision

```mermaid
flowchart TD
    Start([Need to ground AI]) --> Q1{Where is<br/>your data?}
    
    Q1 -->|M365 only| M365Data{Data type?}
    Q1 -->|Azure only| AzureData{Data type?}
    Q1 -->|Both| Hybrid{Primary<br/>location?}
    Q1 -->|Analytics platform| FabricData[Microsoft Fabric]
    
    M365Data -->|SharePoint, OneDrive| Graph[Microsoft Graph Connectors]
    M365Data -->|Teams messages| GraphTeams[Graph Connectors]
    M365Data -->|Custom M365 app| GraphCustom[Custom Graph Connector]
    
    AzureData -->|Documents, PDFs| Q2{Processing needs?}
    AzureData -->|Structured DB| DB{Database?}
    AzureData -->|Unstructured| Blob[Blob Storage + AI Search]
    
    Q2 -->|Standard indexing| Search[Azure AI Search]
    Q2 -->|Multimodal content| ContentUnderstanding[Azure AI Content Understanding<br/>+ AI Search<br/><i>Preview</i>]
    
    DB -->|Global scale, NoSQL| Cosmos{Vector algorithm?}
    DB -->|Relational| Postgres[PostgreSQL + pgvector]
    DB -->|Enterprise SQL| SQL[SQL Server 2025<br/>VECTOR <i>Preview</i>]
    
    Cosmos -->|Flat index| CosmosIVF[Cosmos DB + IVF]
    Cosmos -->|Graph-based| CosmosHNSW[Cosmos DB + HNSW]
    Cosmos -->|Disk-optimized| CosmosDiskANN[Cosmos DB + DiskANN]
    
    Hybrid -->|M365 primary| HybridM365[Graph + BYOK]
    Hybrid -->|Azure primary| HybridAzure[AI Search + Graph API]
    
    FabricData --> Q3{Access method?}
    Q3 -->|Direct platform access| FabricPlatform[Fabric Lakehouse/Warehouse<br/>OneLake + SQL endpoint]
    Q3 -->|Conversational agent| FabricAgent[Fabric Data Agents<br/><i>Preview</i>]
    
    Graph --> Layer{Which<br/>platform?}
    GraphTeams --> Layer
    GraphCustom --> Layer
    Search --> Layer
    ContentUnderstanding --> Layer
    CosmosIVF --> Layer
    CosmosHNSW --> Layer
    CosmosDiskANN --> Layer
    Postgres --> Layer
    SQL --> Layer
    Blob --> Layer
    HybridM365 --> Layer
    HybridAzure --> Layer
    FabricPlatform --> Layer
    FabricAgent --> Layer
    
    Layer -->|M365 Copilot| LayerM365([Use built-in])
    Layer -->|Copilot Studio| LayerStudio([Configure Studio])
    Layer -->|M365 SDK| LayerSDK([Code integration])
    Layer -->|Azure Foundry| LayerFoundry([Configure Foundry])
    Layer -->|Logic Apps| LayerLogicApps([MCP Server/<br/>Connector])
    
    style Graph fill:#0078D4,color:#fff
    style Search fill:#0078D4,color:#fff
    style ContentUnderstanding fill:#50E6FF,color:#000
    style CosmosIVF fill:#0078D4,color:#fff
    style CosmosHNSW fill:#0078D4,color:#fff
    style CosmosDiskANN fill:#0078D4,color:#fff
    style Postgres fill:#0078D4,color:#fff
    style SQL fill:#0078D4,color:#fff
    style FabricPlatform fill:#FFB900,color:#000
    style FabricAgent fill:#FFB900,color:#000
```### Validation Summary - Data Grounding Decision
**Last Validated:** November 3, 2025

**Key Changes:**
- Added Preview annotation to Azure AI Content Understanding (2025-05-01-preview API)
- Added Preview annotation to Fabric Data Agents (Copilot Studio integration)
- **Distinguished Microsoft Fabric platform vs Fabric Data Agents** - added decision node for direct platform access (Lakehouse/Warehouse/OneLake) vs conversational agent layer
- Confirmed SQL Server 2025 VECTOR Preview status (RC1)

**Validated Technologies:**
- **Microsoft Graph Connectors** (GA): M365 data sources (SharePoint, OneDrive, Teams) - [Graph Connectors Overview](https://learn.microsoft.com/en-us/microsoftsearch/connectors-overview)
- **Azure AI Search** (GA): Document indexing, full-text search, vector search, hybrid queries - [AI Search Overview](https://learn.microsoft.com/en-us/azure/search/search-what-is-azure-search)
- **Azure AI Content Understanding** (Preview): Multimodal processing (documents/images/audio/video), RAG-ready Markdown output, AI Search custom skill integration, built-in chunking, standard/pro modes - [Content Understanding Overview](https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/overview) | [Multimodal Search](https://learn.microsoft.com/en-us/azure/search/multimodal-search-overview)
- **Cosmos DB Vector Search** (GA): IVF/HNSW/DiskANN algorithms, NoSQL & MongoDB vCore APIs - [Cosmos DB Vector Search](https://learn.microsoft.com/en-us/azure/cosmos-db/vector-database)
- **PostgreSQL pgvector** (GA): Extension version 0.7.0, HNSW/IVF indexes - [PostgreSQL Vector Search](https://learn.microsoft.com/en-us/azure/postgresql/flexible-server/how-to-use-pgvector)
- **SQL Server 2025 VECTOR** (Preview RC1): Native VECTOR data type, float32 (1,998 dims)/float16 (3,996 dims) - [SQL Server Vector](https://learn.microsoft.com/en-us/sql/t-sql/data-types/vector-data-type)
- **Microsoft Fabric Platform** (GA): Direct knowledge source access via Lakehouse (Delta tables, Spark), Warehouse (T-SQL), OneLake (ADLS Gen2 APIs), KQL databases. Azure AI Foundry integration for RAG - [Fabric Overview](https://learn.microsoft.com/en-us/fabric/fundamentals/microsoft-fabric-overview) | [AI Foundry Fabric Integration](https://learn.microsoft.com/en-us/azure/ai-foundry/faq)
- **Fabric Data Agents** (Preview): Analytics data grounding (warehouses, lakehouses, Power BI semantic models, KQL databases), Copilot Studio connected agents, Azure AI Agent Service integration - [Fabric Data Agents](https://learn.microsoft.com/en-us/fabric/data-science/concept-data-agent) | [Copilot Studio Integration](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-microsoft-copilot-studio)
- **Logic Apps MCP Server** (Preview): Standard logic apps as remote MCP servers, 1,400+ connectors, OAuth 2.0 auth, Streamable HTTP/SSE transports - [Logic Apps MCP Server](https://learn.microsoft.com/en-us/azure/logic-apps/set-up-model-context-protocol-server-standard) | [API Center Integration](https://learn.microsoft.com/en-us/azure/logic-apps/create-mcp-server-api-center)

---

## Complexity Assessment Flow

```mermaid
flowchart TD
    Start([Assess Use Case]) --> Q1{How many<br/>data sources?}
    
````
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
    Start([Need Multi-Agent?]) --> Q1{Pattern Type?}
    
    Q1 -->|Connected agents<br/>sub-agents| Connected[Connected/Sub-Agent Pattern]
    Q1 -->|Sequential/Parallel<br/>workflows| Workflows[Agent Workflow Orchestration]
    Q1 -->|Event triggers| EventDriven[Event-Driven Agents]
    
    Connected --> C_Platform{Platform?}
    C_Platform -->|Low-code| C_Studio[Copilot Studio Preview<br/>Connected agents<br/>Child agents<br/>Handoffs]
    C_Platform -->|Azure| C_Foundry[Azure AI Foundry GA<br/>Connected agents<br/>Sub-agent delegation]
    
    Workflows --> W_Framework{Framework?}
    W_Framework -->|Microsoft| W_AgentFW[Microsoft Agent Framework Preview<br/>Sequential/Concurrent/Handoff/Magentic]
    W_Framework -->|Open source| W_SK[Semantic Kernel<br/>Sequential/Concurrent/Group Chat<br/>Handoff/Magentic]
    W_Framework -->|Bring your own| W_SDK[M365 Agents SDK<br/>Integrate Agent Framework or SK]
    W_Framework -->|Third-party state| W_LangGraph[LangGraph Third-Party<br/>State graphs]
    
    EventDriven --> E_Type{Event source?}
    E_Type -->|Enterprise systems| E_Logic[Logic Apps Preview<br/>AI Agent Workflows<br/>+ MCP Server<br/>Single agent event-triggered]
    E_Type -->|Azure events| E_Functions[Azure Functions<br/>+ Agent Service<br/>Single agent event-triggered]
    E_Type -->|Custom events| E_Custom[Event Grid + Foundry<br/>Event routing to agents]
    
    C_Studio --> Note1[Can connect Fabric Data Agents<br/>as data grounding participants]
    C_Foundry --> Note2[Fabric Data Agents can integrate<br/>as connected agents]
    
    C_Studio --> Deploy1([Deploy])
    C_Foundry --> Deploy2([Deploy])
    W_AgentFW --> Deploy3([Deploy])
    W_SK --> Deploy4([Deploy])
    W_SDK --> Deploy5([Deploy])
    W_LangGraph --> Deploy6([Deploy])
    E_Logic --> Deploy7([Deploy])
    E_Functions --> Deploy8([Deploy])
    E_Custom --> Deploy9([Deploy])
    
    style Connected fill:#107C10,color:#fff
    style Workflows fill:#FFB900,color:#000
    style EventDriven fill:#5C2D91,color:#fff
```

### Validation Summary: Multi-Agent Orchestration

**Connected Agents / Sub-Agent Pattern:**

- **Copilot Studio (Preview):** Connected agents feature supports other Copilot Studio agents + Fabric Data Agents in same environment. Child agents are lightweight sub-agents within main agent. Handoffs enable agent-to-agent transfer.
- **Azure AI Foundry Agent Service (GA May 2025):** Connected agents feature allows main agent to delegate to purpose-built sub-agents using natural language routing. No custom orchestrator required.
- **Fabric Data Agents (Preview):** Can participate as connected agent in Copilot Studio or integrate with Azure AI Agent Service. Consumed BY other agents for data grounding—NOT itself an orchestrator.

**Agent Workflow Orchestration:**

- **Microsoft Agent Framework (Preview/Experimental):** Provides Sequential, Concurrent, Handoff, and Magentic orchestration patterns. Available in C#, Python via Semantic Kernel. Under active development.
- **Semantic Kernel:** Supports Sequential, Concurrent, Group Chat, Handoff, and Magentic orchestration patterns.
- **M365 Agents SDK:** Integrates with Microsoft Agent Framework or Semantic Kernel for orchestration. "Bring your own orchestrator" model—does NOT have built-in Agent Framework.
- **LangGraph:** Third-party framework (not Microsoft) providing state graph management for complex workflows.

**Event-Driven Agents:**

- **Logic Apps AI Agent Workflows (Preview):** Event triggers + MCP Server for enterprise system integration. Triggers SINGLE agent via events—NOT multi-agent orchestration.
- **Azure Functions + Agent Service:** Event-driven invocation of single agents. Event routing, not multi-agent coordination.
- **Event Grid + Foundry:** Event routing to agents. Routes events to trigger agents independently—NOT multi-agent orchestration.

**Sources:**

- [Build AI agents with Copilot Studio](https://learn.microsoft.com/microsoft-copilot-studio/copilot-ai-plugins) — Updated 2025-01-29
- [Connect agents in Copilot Studio (Preview)](https://learn.microsoft.com/microsoft-copilot-studio/advanced-connected-agents) — Updated 2025-01-20
- [Microsoft Agent Framework overview](https://learn.microsoft.com/semantic-kernel/frameworks/agent/agent-framework) — Updated 2024-12-18
- [Connected agents in Azure AI Foundry](https://learn.microsoft.com/azure/ai-services/agents/concepts/connected-agents) — Updated 2025-04-30
- [Add Fabric Data agent as connected agent (Preview)](https://learn.microsoft.com/fabric/data-activator/data-agent-copilot-studio-integration) — Updated 2025-01-30
- [Semantic Kernel agents](https://learn.microsoft.com/semantic-kernel/frameworks/agent/) — Updated 2024-12-18
- [Logic Apps AI Agent Workflows (Preview)](https://learn.microsoft.com/azure/logic-apps/create-run-ai-agent-workflow) — Updated 2025-01-15

---

## Upgrade Paths

```mermaid
flowchart LR
    M365[M365 Copilot<br/>Built-in AI] -->|Add custom data| Graph[+ Graph Connectors GA]
    Graph -->|Need workflows| Studio[Migrate to<br/>Copilot Studio]
    
    Studio[Copilot Studio<br/>Low-code] -->|Connect Azure models| AzureModels[+ Azure AI Foundry models<br/>via connector]
    Studio -->|Need code| Actions[+ Custom Actions]
    Actions -->|Complex orchestration| SDK[Migrate to<br/>M365 SDK]
    
    SDK[M365 Agents SDK<br/>Pro-code M365] -->|Add Azure AI| Foundry[+ Azure AI<br/>Foundry]
    SDK -->|Custom orchestration| Orchestrator[+ Orchestration framework<br/>Agent Framework Preview recommended,<br/>LangChain third-party alternative]
    
    Foundry[Azure AI Foundry<br/>Full Azure] -->|Fine-tune models| FineTune[+ Fine-tuned models]
    Foundry -->|Custom models| CustomModels[+ Custom model deployments]
    
    style M365 fill:#0078D4,color:#fff
    style Studio fill:#0078D4,color:#fff
    style SDK fill:#5C2D91,color:#fff
    style Foundry fill:#D83B01,color:#fff
```

### Validation Summary: Upgrade Paths

**M365 Copilot Extensions:**

- **Graph Connectors (GA Mar 2025):** Add enterprise data from external sources (Stack Overflow, Salesforce, GitHub, custom APIs). Works across M365 Copilot, Copilot Studio, and Microsoft Search. Can use without migrating to Copilot Studio.

**Copilot Studio Enhancements:**

- **Azure AI Foundry Model Connector:** Connect Azure AI Foundry deployed models (GPT-4o, Phi-3.5-vision, fine-tuned models) to Copilot Studio prompts via connector. Enables using custom or fine-tuned models without full migration.
- **Custom Actions:** Extend agents with custom APIs and workflows. Bridge between low-code and pro-code development.

**M365 Agents SDK Integration:**

- **Azure AI Foundry:** Add Azure AI models, custom model deployments, and advanced AI services to M365 SDK agents. Provides AI infrastructure beyond M365 boundaries.
- **Orchestration Frameworks:** M365 SDK supports bring-your-own-orchestrator model. Options include:
  - **Semantic Kernel:** Microsoft framework with Agent Framework patterns (Preview/Experimental - Sequential, Concurrent, Handoff, Magentic)
  - **LangChain:** Third-party orchestration framework
  - **LangGraph:** Third-party state graph management (not Microsoft product)
  - **Custom orchestration:** Build your own orchestrator

**Azure AI Foundry Advanced Features:**

- **Fine-Tuned Models:** Deploy and use fine-tuned custom models via serverless API deployments.
- **Custom Model Deployments:** Deploy models from catalog (1900+ models from Microsoft, OpenAI, Meta, Hugging Face, partners).

**Key Migration Insights:**

- Graph Connectors can be added to M365 Copilot WITHOUT migrating to Copilot Studio (enhancement, not migration requirement)
- M365 SDK is model- and orchestrator-agnostic - supports ANY AI stack via bring-your-own approach
- Microsoft Agent Framework is orchestration pattern IN Semantic Kernel, not standalone Azure AI Foundry feature
- LangGraph and LangChain are third-party frameworks (not Microsoft products) - supported via M365 SDK's flexible architecture

**Sources:**

- [Graph connectors for M365 Copilot](https://learn.microsoft.com/en-us/power-platform/release-plan/2024wave2/microsoft-copilot-studio/add-enterprise-data-new-graph-connections) — Updated 2024-11-06
- [Bring your own model for prompts](https://learn.microsoft.com/en-us/ai-builder/byom-for-your-prompts) — Updated 2025-01-31
- [M365 Agents SDK overview](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/create-deploy-agents-sdk) — Updated 2025-01-27
- [Semantic Kernel and Agent Framework in Agents SDK](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/using-semantic-kernel-agent-framework) — Updated 2025-01-15
- [Azure AI Foundry Models overview](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/foundry-models-overview) — Updated 2025-04-23

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
**Next:** [Evaluation Criteria](evaluation-criteria.md) - Assess complexity, skills, budget, and governance requirements

