---
layout: default
title: Microsoft AI Technologies
nav_order: 8
description: "Complete reference for Microsoft's AI technology portfolio"
---

# Microsoft AI Technologies Reference

This section provides a comprehensive overview of Microsoft's AI technology stack, from end-user productivity tools to infrastructure services.

---

## Core AI Platforms

### Microsoft 365 Copilot
**Description:** Integrated AI assistant across M365 apps (Word, Excel, Teams, Outlook, PowerPoint, OneNote) with tenant context and Graph security. Supports extensibility via declarative agents (low-code) and custom engine agents (pro-code) for tailored productivity experiences.  
**Official Docs:** [Microsoft 365 Copilot Overview](https://learn.microsoft.com/en-us/microsoft-365-copilot/)  
**Status:** GA

**Key Features:**
- **Tenant-aware AI:** Works across M365 apps with Graph security and compliance
- **Extensibility:** Declarative agents (instructions + knowledge + actions), custom engine agents (full orchestration control)
- **Agent Discovery:** Unified in-app store for Word/PowerPoint/Excel, agent pinning for tenant-wide visibility
- **Admin Controls:** Pre-approval for trusted agents, agent sharing governance, extensibility management in M365 admin center
- **Knowledge Sources:** Teams meetings, SharePoint (up to 100 files), embedded file content (up to 100MB), email, Dataverse, Copilot connectors with scoping
- **APIs (Preview):** M365 Copilot Chat API (multi-turn conversations), Search API (semantic search across OneDrive)
- **Advanced Capabilities:** Fine-tune models with tenant data, multi-step workflows (declarative instructions), asynchronous/proactive messaging in custom engine agents

**Recent Updates (2025):**
- **Model fine-tuning:** Use tenant data to fine-tune M365 Copilot models (August 2025)
- **Agent Center:** Centralized agent management, prompt fine-tuning, in-context action registration (June 2025)
- **Enhanced SharePoint Q&A:** Improved accuracy on files with tables, comments, formatting (August 2025)
- **Custom engine agents in Copilot Studio:** One-click deployment to M365 Copilot channel (June 2025)
- **Admin pre-approval:** Pre-approve trusted agents to reduce confirmation prompts (August 2025)

**Network Isolation:**
- **VNet Support:** ❌ No custom VNet support
- Fully managed SaaS (no VNet integration available)
- Requires gateway architecture for private on-premises data access
- Inherits M365 tenant network security
- **Ideal for:** Organizations accepting Microsoft-managed SaaS networking model

**When to use:** Broad productivity gains, existing M365 licenses, tenant-aware context, no deep AI expertise required, extend via low-code (Copilot Studio) or pro-code (M365 Agents SDK)

**Sources:**
- [M365 Copilot Release Notes](https://learn.microsoft.com/en-us/copilot/microsoft-365/release-notes) (Updated: 2025-08-05)
- [What's New in M365 Copilot Extensibility](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/whats-new) (Updated: 2025-10-01)
- [M365 Copilot Extensibility Overview](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent)
- [M365 Copilot Security](https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-ai-security)

---

### Copilot Studio
**Description:** Graphical, low-code platform for building agents and agent flows with managed governance, ALM, and multi-channel deployment. Supports declarative agents (extend M365 Copilot) and custom engine agents (bring your own orchestration). Available as both standalone web app and Teams app.  
**Official Docs:** [Copilot Studio Documentation](https://learn.microsoft.com/en-us/microsoft-copilot-studio/)  
**Implementation Guide:** [aka.ms/CopilotStudioImplementationGuide](https://aka.ms/CopilotStudioImplementationGuide)

**Key Features:**
- **Low-code to pro-code agent development:** No-code (Copilot Studio Lite), low-code (full experience), or pro-code integration
- **1,400+ Power Platform connectors:** Seamless Microsoft and third-party service integration
- **Event Triggers (GA):** Autonomous agents responding to SharePoint, OneDrive, Planner, Recurrence events
- **Declarative agents:** Extend M365 Copilot with instructions, knowledge, actions (individual/departmental use)
- **Custom engine agents (GA):** Full control over orchestration, models, and workflows (complex scenarios, group collaboration, multi-channel)
- **Multi-channel deployment:** M365 Copilot, Teams, Web, Mobile, Facebook, WhatsApp (via Azure Bot Service)
- **BYOK (GA):** Azure AI Search integration, SharePoint/OneDrive (security-trimmed), Graph Connectors
- **BYOM (Preview):** Azure AI Foundry model integration
- Managed ALM via Power Platform solutions (in-product pipelines, Azure DevOps, GitHub Actions)

**NLU (Natural Language Understanding) Options:**
- **Generative AI Orchestration (Default):** LLM-driven multi-intent recognition, automatic topic/action selection, slot-filling, unified responses combining topics + actions + knowledge (up to ~128 triggerable items, ~5 chained messages per item)
- **Classic Orchestration (NLU):** Original NLU for simpler needs; 5-20 trigger phrases per topic, RegEx/List entities, no entity annotations required (⚠️ latency increases with excess training data)
- **Classic Orchestration (NLU+):** High-precision enterprise option; large-scale topics/entities, extensive training samples, entity annotations, precompiled model for consistent performance (⚠️ requires Dynamics 365 Contact Center license for voice/chat channels)
- **Azure CLU Integration:** Link existing Azure Conversational Language Understanding models for advanced entity extraction, more languages (requires Azure subscription + manual model synchronization)

**Topic & Orchestration Architecture:**
- **Topics:** Conversational thread portions authored on visual canvas with nodes (send message, ask question, conditional logic)
- **Generative Orchestration:** Agent selects best combination of topics/actions/knowledge at runtime based on descriptions and user queries
- **Classic Orchestration:** Trigger phrases drive topic selection via NLU, deterministic conversation flows
- **Multi-Agent Systems (Preview):** Child agents (lightweight, embedded) and connected agents (independent, reusable across solutions, Fabric data agents supported)
- **Autonomous Agents:** Event-driven triggers (SharePoint file changes, Planner task updates, recurrence schedules) with proactive actions

**Performance Characteristics:**
- **Optimized for:** Speed to market, managed operations, built-in governance, connector ecosystem integration
- **Managed orchestration layer:** Provides convenience (ALM, multi-channel, governance) with managed SaaS infrastructure
- **Power Automate integration:** 120-second flow execution limit, 100-second return requirement to Copilot Studio; HTTP Request node offers lower latency for simple calls
- **Latency profile:** Suitable for <1s response scenarios; for <100ms requirements, consider Azure AI Foundry

**Context Window (GPT-5 Preview):**
- **GPT-5 chat/reasoning:** Up to 400k tokens (model capacity)
- **Effective context:** Varies based on agent configuration, orchestration features, and system variables
- **Trade-off:** Managed platform convenience vs full model context (Foundry provides full context but requires infrastructure management)

**Knowledge Sources (BYOK):**
- **Internal:** SharePoint/OneDrive (security-trimmed), Dataverse tables, Documents (uploaded to Dataverse), Graph Connectors, Azure AI Search
- **External:** Public websites (Bing-indexed), Web Search (Grounding with Bing Search), Bing Custom Search
- **Generative Answers:** Combines knowledge sources with LLM responses, citations, moderation

**Multi-Channel Deployment:**
- **M365:** Teams, M365 Copilot, SharePoint
- **Web/Mobile:** Custom website, demo website, mobile apps
- **Social/Messaging:** Facebook, WhatsApp, SMS
- **Contact Center:** Dynamics 365 Omnichannel (live chat hand-off to agents), voice IVR integration
- **Other:** Azure Bot Service channels (Slack, Telegram, etc.)

**Licensing:**
- **Prepaid capacity:** Copilot Credit packs (predictable high-volume, pooled tenant-wide)
- **Pay-as-you-go:** $0.01/Copilot Credit (Azure subscription, consumption-based)
- **Quotas:** 8,000 RPM (general messages), 50-100+ RPM (gen AI, scales with message packs)

**Network Isolation:**
- **VNet Support:** ⚠️ Gateway-based (does NOT execute in customer VNet)
- On-premises data gateway (for on-premises systems)
- VNet data gateway (GA, for Azure resources) — Microsoft-managed, supports private endpoints to Azure resources
- Requires Managed Environment in Power Platform + VNet support enabled
- External connectors inherit external system's network security posture
- **Limitations:** Power Platform is a managed service (agent runtime NOT in customer VNet), not suitable for fully air-gapped environments without gateway setup
- **Ideal for:** Managed PaaS scenarios with Azure resource access via VNet gateway

**When Copilot Studio is the Right Tool:**
- **Declarative agents:** Individual/team productivity in M365 context, faster implementation (days), user workflows within M365 apps (SharePoint, OneDrive, Teams via @mentions)
- **Custom engine agents:** Complex workflows with custom orchestration, specific business logic, group collaboration in Teams channels, multi-system integrations, proactive messaging/event-driven workflows, multi-channel deployment (beyond M365), migrating existing conversational bots
- Leveraging Power Platform's 1,400+ connectors and event triggers
- Prefer Microsoft-managed infrastructure and built-in governance
- Team includes makers and developers; no deep AI/ML expertise required

**Sources:**
- [Copilot Studio Fundamentals](https://learn.microsoft.com/en-us/microsoft-copilot-studio/fundamentals-what-is-copilot-studio) (Updated: 2024-10-15)
- [Agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agents-overview) (Updated: 2024-11-05)
- [Implementation Guide](https://aka.ms/CopilotStudioImplementationGuide) (PDF Version 2.0)
- [Event Triggers Overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-triggers-about) (Updated: 2024-09-20)
- [VNet Data Gateway](https://learn.microsoft.com/en-us/power-platform/admin/vnet-support-overview)
- [Managed Environments](https://learn.microsoft.com/en-us/power-platform/admin/managed-environment-overview)

---

### Azure AI Foundry
**Description:** Code-first platform for AI models, prompt flow, evaluations, RAG, and safety features. Comprehensive model catalog including Azure OpenAI (GPT-5, o3/o4, Sora video, audio models), open-source models, and custom deployments. Works with or without Azure AI Agent Service.  
**Official Docs:** [Azure AI Foundry Portal](https://learn.microsoft.com/en-us/azure/ai-studio/)  
**Status:** GA

**Key Features:**
- **Code-first AI development:** Full programmatic control over AI workflows
- **Model catalog:** Azure OpenAI (GPT-5, o3/o4-mini, GPT-4.1, Sora, Realtime API), open-source models (Meta, Hugging Face), custom models
- **Latest Models (2025):**
  - GPT-5 series (gpt-5, gpt-5-mini, gpt-5-nano) for reasoning (August 2025)
  - o3/o4-mini reasoning models for enhanced quality (April 2025)
  - Sora video generation with image-to-video support (May 2025, GA August 2025)
  - GPT-image-1 (limited access, improved text rendering, image editing/inpainting)
  - Realtime API with WebRTC for low-latency audio (April 2025, GA August 2025)
  - GPT-4.1 with 1M token context (April 2025)
- **Prompt flow:** Visual orchestration for AI workflows
- **Evaluation and safety:** Model router (auto-selects best model per prompt), prompt shields with spotlighting, stored completions for fine-tuning
- **RAG patterns:** Grounding with Bing Search, Azure AI Search, file search
- **Provisioned throughput:** PTU deployments, spillover traffic management (GA August 2025)
- **Azure consumption pricing:** Pay-as-you-go, PTU reservations

**Performance Characteristics:**
- **Optimized for:** Latency-sensitive applications, full architectural control, custom implementations
- **Direct model API access:** Minimal orchestration overhead for sub-100ms response scenarios
- **Custom optimization:** Full control over caching, batching, PTU provisioning, infrastructure
- **Latency profile:** Suitable for real-time, high-throughput scenarios; requires performance tuning expertise

**Context Window:**
- **GPT-5-codex/pro:** 400k tokens (272k input, 128k output)
- **GPT-5-chat:** 128k tokens
- **GPT-4.1:** 1M tokens
- **Full model context:** No SaaS orchestration layer consumption
- **Trade-off:** Full context available but requires self-managed infrastructure and deployment

**Network Isolation:**
- **VNet Support:** ✅ Full private networking support
- VNet integration with container injection (platform APIs communicate within customer VNet)
- Private endpoints for all resources (Storage, AI Search, Cosmos DB, Foundry resource)
- Network Security Groups (NSGs) for traffic isolation
- Standard Setup with Private Networking: No public egress by default
- Customer-managed keys (CMK) optional
- Azure landing zone controls (Azure Policy, RBAC)
- **Ideal for:** Zero-trust environments, air-gapped deployments, sovereign data strategies

**When Azure AI Foundry is the Right Tool:**
- Latency-sensitive applications (<100ms response requirements)
- Need full control over architecture and optimization
- Custom AI patterns beyond platform capabilities
- Custom integrations outside standard connector ecosystem
- Team has Azure infrastructure and AI engineering expertise
- High-throughput scenarios requiring PTU provisioning
- Video generation, advanced audio (transcription, TTS, real-time), image generation scenarios

**Sources:**
- [Azure AI Foundry Documentation](https://learn.microsoft.com/en-us/azure/ai-studio/)
- [What's New in Azure OpenAI](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/whats-new) (Updated: 2025-08-01)
- [Performance and Latency Guide](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/how-to/latency)
- [GPT-5 Quotas and Limits](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/quotas-limits#gpt-5-series)
- [Model Choice Guide](https://learn.microsoft.com/en-us/azure/ai-foundry/foundry-models/how-to/model-choice-guide)
- [Configure Private Link](https://learn.microsoft.com/en-us/azure/ai-foundry/how-to/configure-private-link)
- [Virtual Networks for Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/agents/how-to/virtual-networks)

---

### Azure AI Agent Service
**Description:** Managed PaaS for agent orchestration, skills management, and runtime infrastructure within Azure AI Foundry. Supports connected agents (multi-agent systems), 15+ built-in tools, full RBAC + VNet + BYO storage. GA with continuous feature additions.  
**Official Docs:** [Azure AI Agent Service](https://learn.microsoft.com/en-us/azure/ai-services/agents/)  
**Status:** GA (May 2025)

**Key Features:**
- **Managed agent runtime infrastructure:** Fully managed compute, memory, and state management
- **Connected agents (GA):** Multi-agent systems with task-specific agents coordinated by primary agent, supports Fabric data agents
- **Memory and state management:** Conversation context, checkpointing, thread storage
- **Full enterprise security:** RBAC, VNet integration, private endpoints, BYO Cosmos DB for thread storage (April 2025)
- **Tracing and monitoring:** Azure Monitor integration (metrics for file indexing, run counts), trace agents SDK for debugging
- **Event-driven triggers:** Integrate with Azure Logic Apps for automatic agent invocation

**Built-in Tools (Knowledge):**
- **Azure AI Search:** Ground agents with indexed data, chat with your data
- **File Search:** RAG with proprietary documents (Azure Blob Storage, local files). Uses vector stores (up to 10,000 files), automatic chunking/embedding (text-embedding-3-large), hybrid search (keyword + semantic), reranking
- **Grounding with Bing Search:** Access real-time web information
- **Grounding with Bing Custom Search (GA June 2025):** Enhanced responses with selected web domains
- **Microsoft Fabric (GA March 2025):** Integrate with Fabric Data Agents for data analysis capabilities
- **SharePoint (Preview):** Chat with private SharePoint documents, OBO authentication for security-trimmed access, leverages M365 Copilot API built-in indexing
- **Licensed Data:** Proprietary data via licensed API keys (TripAdvisor, Morningstar, LexisNexis, LEGALFLY, etc.)

**Built-in Tools (Action):**
- **Function Calling:** Custom stateless functions
- **Azure Functions:** Intelligent, event-driven serverless code execution
- **Azure Logic Apps:** 1,400+ connector-based workflows
- **Code Interpreter:** Write and run Python code in sandboxed environment (data handling, visuals)
- **OpenAPI 3.0 Specified Tool:** Connect to external APIs via OpenAPI spec
- **Model Context Protocol (GA June 2025):** Access tools hosted on existing MCP endpoints
- **Deep Research (GA June 2025):** Multi-step web-based research with o3-deep-research model + Bing Search
- **Browser Automation (Preview):** Real-world browser tasks via natural language with Playwright Workspaces
- **Computer Use (Preview):** UI interaction via specialized computer-use-preview model, interprets raw pixel screenshots, virtual keyboard/mouse control
- **Image Generation (Preview):** Generate and edit images as part of conversations and multi-step workflows

**Agent Setup Options:**
- **Basic Setup:** Microsoft-managed search and storage (files stored in MS-managed storage, vector stores in MS-managed search)
- **Standard Setup:** BYO Azure AI Search + Blob Storage + Cosmos DB (files in your Blob, vector stores in your AI Search, thread storage in your Cosmos DB), private networking, no public egress by default

**Recent Updates (2025):**
- **General Availability:** Service went GA in May 2025
- **Connected agents:** Multi-agent orchestration without external orchestrators (May 2025)
- **MCP tool:** Connect to remote Model Context Protocol servers (June 2025)
- **Deep Research:** o3-deep-research + Bing Search for multi-step analysis (June 2025)
- **Bing Custom Search:** Specify websites for grounding (June 2025)
- **Azure Monitor integration:** Metrics for file indexing, run tracking (April 2025)
- **BYO Cosmos DB:** Thread storage in customer-managed Cosmos DB for NoSQL (April 2025)

**Network Isolation:**
- **VNet Support:** ✅ Full private networking support (same as Azure AI Foundry)
- VNet integration with container injection
- Private endpoints for all resources
- Network Security Groups (NSGs) for traffic isolation
- Standard Setup: No public egress by default
- **Ideal for:** Managed PaaS with private networking requirements

**When to use:** Managed agent orchestration at PaaS layer, scalable agent infrastructure, multi-agent systems, comprehensive built-in tool ecosystem, prefer Azure-managed RAG infrastructure, need enterprise security + observability

**Sources:**
- [What's New in Azure AI Agent Service](https://learn.microsoft.com/en-us/azure/ai-foundry/agents/whats-new) (Updated: 2025-06-01)
- [Azure AI Agent Service Overview](https://learn.microsoft.com/en-us/azure/ai-services/agents/overview)
- [Agent Tools Overview](https://learn.microsoft.com/en-us/azure/ai-foundry/agents/how-to/tools/overview)
- [Transparency Note for Azure Agent Service](https://learn.microsoft.com/en-us/azure/ai-foundry/responsible-ai/agents/transparency-note)
- [Virtual Networks for Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/agents/how-to/virtual-networks)

---

### AI Builder
**Description:** Power Platform AI services for document processing, vision, text analysis, and predictions. Backed by Azure AI Document Intelligence and GPT models. Callable from Copilot Studio agents, Power Automate, and Power Apps.  
**Official Docs:** [AI Builder Documentation](https://learn.microsoft.com/en-us/ai-builder/)  
**Status:** GA

**Key Features:**
- **Prebuilt AI models:** No training required for common scenarios (document processing, vision, text analysis)
- **Custom AI model training:** Train models on organization-specific data
- **Power Platform integration:** Seamless use in Power Apps, Power Automate, Copilot Studio
- **GPT integration:** Extract information from documents, text classification, content generation (GA March 2025)
- **Azure Document Intelligence:** Advanced document processing with latest models

**Capabilities:**
- **Document processing:** Invoices, receipts, contracts, business cards, tax forms, identity documents (passports, driver's licenses)
- **Text generation and analysis:** GPT-powered extraction, sentiment analysis, entity extraction, language detection, key phrase extraction, text translation
- **Vision:** Object detection, OCR (text recognition), image classification
- **Predictions:** Classification, regression models
- **Prebuilt model customization:** Add organization-specific fields to prebuilt models (GA January 2024)

**Recent Updates (2025):**
- **GPT document extraction:** Use GPT to extract information from any document type without model training (GA March 2025, Preview November 2024)
- **Azure Document Intelligence integration:** Leverage advanced features from Azure's latest document models (GA April 2025, Preview December 2024)
- **Model versioning:** Iteratively improve model performance across environments
- **Environment portability:** Move trainable models across Power Platform environments

**When to use:** Document understanding in Power Platform solutions, prebuilt AI capabilities for common scenarios, no-code/low-code AI, Power Automate workflow integration, no deep AI/ML expertise required

**Sources:**
- [AI Builder Documentation](https://learn.microsoft.com/en-us/ai-builder/)
- [What's New and Planned for AI Builder](https://learn.microsoft.com/en-us/power-platform/release-plan/2024wave2/ai-builder/planned-features) (2024 Wave 2)
- [Intelligent Document Processing](https://learn.microsoft.com/en-us/power-platform/release-plan/2025wave1/ai-builder/intelligent-document-email-processing) (2025 Wave 1)

---

## Pro-Code Development Frameworks

### Azure Logic Apps
**Description:** Pro-developer workflow automation platform for enterprise integration and AI agent orchestration. Supports autonomous and conversational AI agent workflows (Preview) with Azure OpenAI and Azure AI Foundry integration. Can be configured as remote MCP servers to expose workflows as tools for LLMs and AI agents. 1,400+ connectors for building agent tools across cloud and on-premises systems.  
**Status:** Agent Workflows (Preview), MCP Server (Preview), Core Platform (GA)  
**Official Docs:** [Azure Logic Apps Documentation](https://learn.microsoft.com/en-us/azure/logic-apps/) | [Agent Workflows](https://learn.microsoft.com/en-us/azure/logic-apps/agent-workflows-concepts) | [MCP Server](https://learn.microsoft.com/en-us/azure/logic-apps/set-up-model-context-protocol-server-standard)

**Key Features:**
- 1,400+ connectors (cloud + on-premises)
- Visual workflow designer + code
- AI agent workflows (autonomous & conversational)
- MCP server capabilities (expose workflows as AI tools)
- State management and checkpointing
- DevOps integration (GitHub Actions, Azure DevOps)

**When to use:** Enterprise integration + AI agents, workflow automation with LLM integration, exposing enterprise systems as AI tools

---

### Microsoft 365 Agents SDK & Toolkit
**Description:** Pro-code framework for building multi-channel custom engine agents. Model-agnostic and orchestrator-agnostic (bring your own: Agent Framework recommended, LangChain third-party alternative, Semantic Kernel in maintenance mode). Deploys to M365 Copilot, Teams, Web, Mobile, SMS, Email, and 10+ external channels. Bot Framework successor (BF support ends Dec 31, 2025). Includes CLI, VS Code extension, and Visual Studio extension.  
**Status:** GA (C#, JavaScript/TypeScript, Python)  
**Official Docs:** [M365 Agents SDK](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/) | [M365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/developer/overview-m365-agents-toolkit) | [Bot Framework Migration](https://aka.ms/bfmigrationguidance)

**Key Features:**
- **Multi-channel deployment:** M365 Copilot, Teams, Web, Mobile, SMS, Email, WhatsApp, Slack, and 10+ other platforms
- **Model-agnostic:** Azure OpenAI, OpenAI, Anthropic, custom models via bring-your-own
- **Orchestrator-agnostic:** Agent Framework (recommended), LangChain (third-party), Semantic Kernel (maintenance mode), custom orchestrators
- **Bot Framework successor:** Migration path from Bot Framework SDK (deprecated Dec 31, 2025)
- **Group productivity scenarios:** Teams channels, meetings, collaborative workspaces
- **Proactive messaging:** Send messages outside of user-initiated conversations
- **M365 Agents Playground:** Local testing sandbox, no M365 tenant required, simulates Teams environment
- **Multi-language support:** C#, JavaScript, TypeScript, Python

**Development Tools:**
- **M365 Agents Toolkit (VS Code):** Templates, scaffolding, deployment automation, API plugin generation via Kiota (May 2025)
- **M365 Agents Toolkit (Visual Studio):** C# + .NET development, Blazor support
- **CLI:** Command-line interface for CI/CD, automation, collaboration workflows

**Recent Updates (2025):**
- **Kiota API plugin generation:** Search public APIs, visually select endpoints, improved plugin maintainability (May 2025)
- **Agent Framework integration:** Official recommendation for multi-agent orchestration (replaces Semantic Kernel for new projects)
- **Simplified deployment:** One-click publishing to M365 Copilot, Teams, organizational catalog

**Supported Channels:**
- M365 Copilot
- Microsoft Teams (chat, channels, meetings)
- Web, Mobile
- SMS, Email
- WhatsApp, Slack, Telegram, and more

**Network Isolation:**
- **VNet Support:** ✅ Full control (depends on hosting platform)
- M365 Agents SDK is a development framework - network isolation is determined by where you deploy it
- **Azure App Service hosting:** Full VNet integration, private endpoints, NSG controls, managed certificates
- **Azure Container Apps hosting:** VNet integration, private endpoints, workload profiles for isolation
- **Azure Kubernetes Service (AKS):** Complete network control, custom CNI, network policies
- **On-premises hosting:** Full control over network infrastructure and security policies
- Customer controls all networking decisions based on chosen hosting platform
- **Ideal for:** Organizations requiring custom network control, air-gapped support, or hybrid on-premises/cloud deployments

**When to use:** Multi-channel agents, full control over AI models and orchestration, Bot Framework migration, group productivity in Teams, require specific programming language (C#/.NET), complex authentication scenarios, self-hosted deployment requirements

**Sources:**
- [M365 Agents SDK Overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agents-sdk-overview)
- [M365 Agents Toolkit Overview](https://learn.microsoft.com/en-us/microsoft-365/developer/overview-m365-agents-toolkit)
- [M365 Copilot Release Notes - Extensibility](https://learn.microsoft.com/en-us/copilot/microsoft-365/release-notes) (Updated: 2025-08-19)
- [Bot Framework Migration Guide](https://aka.ms/bfmigrationguidance)

---

### Microsoft Agent Framework
**Description:** Microsoft's next-generation orchestration framework for building multi-agent workflows with type-safe, declarative patterns. Combines best capabilities of Semantic Kernel and Microsoft Research's AutoGen. Features: 5 orchestration patterns (Sequential, Concurrent, Handoff, Group Chat, Magentic), workflow-based architecture with executors and edges, checkpointing for long-running processes, human-in-the-loop support. Works with M365 Agents SDK (BYO orchestrator model) or standalone. **Microsoft's strategic investment direction for multi-agent orchestration.**  
**Status:** Preview/Experimental (C#, Python, Java) - **Active development, will GA soon**  
**Official Docs:** [Microsoft Agent Framework](https://learn.microsoft.com/en-us/agent-framework/) | [Workflows Overview](https://learn.microsoft.com/en-us/agent-framework/user-guide/workflows/overview)

**Key Features:**
- **5 Orchestration Patterns:** Sequential (pipelines, step-by-step processing), Concurrent (parallel analysis, independent subtasks), Handoff (dynamic routing, escalation scenarios), Group Chat (collaborative problem solving, multi-agent debates), Magentic (complex generalist multi-agent tasks inspired by MagenticOne research)
- **Workflow-based architecture:** Graph-based control flow with executors and edges, conditional routing, parallel processing
- **Type safety:** Strong typing ensures messages flow correctly between components with comprehensive validation
- **Checkpointing:** Save workflow states for recovery and resumption of long-running processes on server sides
- **External integration:** Built-in request/response patterns for API integration and human-in-the-loop scenarios
- **M365 Agents SDK Integration:** Recommended orchestrator for M365 SDK (BYO model), replaces Semantic Kernel as primary recommendation
- **Replaces Semantic Kernel Agents:** Semantic Kernel agents in maintenance mode (security patches only, no new features), Agent Framework is the future
- **Enterprise-grade:** Built-in observability (OpenTelemetry), Microsoft Entra security, responsible AI features (prompt injection protection, task adherence)
- **Standards-based:** Integration with Agent-to-Agent (A2A) protocol and Model Context Protocol (MCP)

**Workflow vs Agent Distinction:**
- **AI Agent:** LLM-driven with dynamic, context-dependent steps chosen by the model
- **Workflow:** Predefined sequence of operations that can include AI agents as components for controlled execution paths

**When to use:** Multi-agent workflows requiring coordination, specialized task delegation, complex collaborative problem-solving, human-agent collaboration, long-running processes with checkpointing needs, enterprise security + observability requirements. **Use this instead of Semantic Kernel agents for new projects.**

**Sources:**
- [Microsoft Agent Framework Overview](https://learn.microsoft.com/en-us/agent-framework/overview/agent-framework-overview)
- [Agent Orchestration Patterns](https://learn.microsoft.com/en-us/semantic-kernel/frameworks/agent/agent-orchestration/)
- [Agent Framework Workflows](https://learn.microsoft.com/en-us/agent-framework/user-guide/workflows/overview)
- [Using with M365 Agents SDK](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/using-semantic-kernel-agent-framework)

---

## "Agent Framework" Terminology Clarification

The term "agent framework" refers to two distinct technologies:

**1. Microsoft Agent Framework (Orchestration SDK)**  
Open-source library for workflow-based orchestration. Public Preview. Use for: Executor/Edge workflows, checkpointing, M365 Agents SDK integration.

**2. Azure AI Agent Service (Managed PaaS)**  
Managed service for agent orchestration within Azure AI Foundry. GA. Use for: Managed infrastructure, Azure-hosted agents, scalable runtime.

**Quick Decision:**
- M365 productivity agents → M365 Agents SDK + Agent Framework
- Azure-hosted agents → Azure AI Foundry + AI Agent Service  
- Bot Framework migration → M365 Agents SDK
- Workflow orchestration + checkpointing → Agent Framework

---

## Technology Selection Quick Guide

| Your Need | Recommended Technology | Why? |
|-----------|------------------------|------|
| End-user productivity (no dev) | Microsoft 365 Copilot | Built-in, tenant-aware, immediate value |
| Custom agents (low-code) | Copilot Studio | Managed platform, fast deployment, governance |
| Custom agents (pro-code) | M365 Agents SDK or Azure AI Foundry | Full control, any model, any orchestrator |
| Managed agent runtime | Azure AI Agent Service | PaaS for agent infrastructure, multi-agent support |
| Enterprise workflow + AI | Azure Logic Apps | 1,400+ connectors, MCP server, AI agent workflows |
| Document processing | AI Builder | Prebuilt models, Power Platform integration |
| Workflow orchestration | Microsoft Agent Framework | Checkpointing, type-safe workflows, multi-agent patterns |

---

## Network Isolation Decision Matrix

| Technology | VNet Support | Private Endpoints | Air-Gapped | Gateway Required | Best For |
|------------|-------------|-------------------|------------|------------------|----------|
| **Azure AI Foundry** | ✅ Full | ✅ Yes | ✅ Yes | ❌ No | Zero-trust, air-gapped, sovereign data |
| **Azure AI Agent Service** | ✅ Full | ✅ Yes | ✅ Yes | ❌ No | Managed PaaS with private networking |
| **Copilot Studio** | ⚠️ Gateway-based | ⚠️ Via gateway | ❌ No | ✅ Yes | Managed PaaS with Azure resource access |
| **M365 Agents SDK** | ✅ Self-hosted | ✅ Yes | ✅ Yes | ❌ No | Custom network control |
| **M365 Copilot** | ❌ No | ❌ No | ❌ No | ✅ For on-prem | Managed SaaS only |

---

**Next:** [Feature Comparison](feature-comparison.md) - Side-by-side capability matrices
