# Module 2: The Tech Stack of 2026

**Duration:** 45 minutes  
**Agent ID:** `module-2`

---

## Learning Objectives

By the end of this module, you will:
1. Identify the core components of an AI orchestration system
2. Explain the evolution from basic chatbots to agentic AI systems
3. Differentiate between various AI API providers and their strengths
4. Build a basic understanding of how AI tools connect together

---

## 2.1 The AI Orchestration Stack

### What Is AI Orchestration?

AI orchestration is the **coordination layer** that connects AI models, tools, memory, and actions into a coherent system. Think of it as the conductor of an AI orchestra.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    AI ORCHESTRATION STACK                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                    ORCHESTRATION LAYER                          │   │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐           │   │
│  │  │   Memory     │  │  Agentic     │  │   Workflow   │           │   │
│  │  │   Manager    │  │  Reasoning   │  │   Engine     │           │   │
│  │  └──────────────┘  └──────────────┘  └──────────────┘           │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                              │                                          │
│                              ▼                                          │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                        TOOL LAYER                                 │   │
│  │  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐          │   │
│  │  │Browser │ │  API   │ │  File  │ │  DB   │ │Search  │          │   │
│  │  │        │ │        │ │  System│ │       │ │        │          │   │
│  │  └────────┘ └────────┘ └────────┘ └────────┘ └────────┘          │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                              │                                          │
│                              ▼                                          │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │                     MODEL LAYER                                  │   │
│  │  ┌──────────────────────────────────────────────────────────┐    │   │
│  │  │  Large Language Models (GPT-4, Claude, Gemini, Llama)   │    │   │
│  │  └──────────────────────────────────────────────────────────┘    │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

---

### The Four Layers Explained

**Layer 1: The Model (The Brain)**
- The LLM processes input, reasons, and generates output
- The orchestrator decides *what* to ask the model
- Examples: GPT-4o, Claude 3.5 Sonnet, Gemini 1.5, Llama 3

**Layer 2: The Tool Layer (The Hands)**
- Models alone can only output text
- Tools let models interact with the real world
- Web search, code execution, API calls, file manipulation

**Layer 3: The Memory Layer (The Knowledge)**
- Short-term: Current conversation context
- Long-term: What the agent has learned about you
- Semantic: General world knowledge

**Layer 4: The Orchestration Layer (The Conductor)**
- Decides what to do, in what order
- Manages the loop: Observe → Think → Act → Reflect
- Routes between tools and models

---

## 2.2 The Three Eras of AI

### Era 1: Rule-Based (Pre-2015)

```
┌─────────────────────────────────────────────────────────────────┐
│                    ERA 1: RULE-BASED                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   INPUT ──► RULES ENGINE ──► OUTPUT                             │
│                                                                 │
│   if (email contains "FREE") → mark_as_spam                     │
│                                                                 │
│   Characteristics:                                             │
│   ✅ Highly reliable for known scenarios                        │
│   ✅ Fast                                                     │
│   ❌ Brittle — breaks on novel inputs                           │
│   ❌ Requires manual rule-writing                               │
│   ❌ Cannot learn                                               │
│                                                                 │
│   Examples: Spam filters, thermostats, early chatbots           │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Era 2: ML / Supervised Learning (2015–2022)

```
┌─────────────────────────────────────────────────────────────────┐
│                    ERA 2: MACHINE LEARNING                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   TRAINING DATA ──► ML MODEL ──► PREDICTION                     │
│                                                                 │
│   10,000 emails ──► Trained Model ──► "This is spam"            │
│                                                                 │
│   Characteristics:                                             │
│   ✅ Learns patterns from data                                  │
│   ✅ Handles variation in input                                 │
│   ❌ Requires massive labelled training data                    │
│   ❌ Single task (one model, one purpose)                       │
│   ❌ No generalisation beyond training                          │
│                                                                 │
│   Examples: Siri, recommendation engines, ChatGPT (GPT-3.5)   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Era 3: Agentic AI (2023+)

```
┌─────────────────────────────────────────────────────────────────┐
│                    ERA 3: AGENTIC AI                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   GOAL ──► ORCHESTRATOR ──► MULTI-STEP EXECUTION                │
│                │                                                 │
│                ▼                                                 │
│         ┌─────────────────────────────────────────────┐         │
│         │  Observe → Plan → Act → Reflect → Repeat     │         │
│         └─────────────────────────────────────────────┘         │
│                │                                                 │
│                ▼                                                 │
│         ┌──────┴──────┬──────────┬──────────┐                    │
│         ▼             ▼          ▼          ▼                    │
│     Web Search    Code Run   API Call   Memory Update             │
│                                                                 │
│   Characteristics:                                             │
│   ✅ Autonomous multi-step task completion                      │
│   ✅ Tool use and external connectivity                          │
│   ✅ Persistent memory                                          │
│   ✅ Adapts to novel situations                                  │
│   ✅ Chains actions toward goals                                 │
│                                                                 │
│   Examples: Claude Agents, GPT-4o, AutoGPT, OpenClaw, CoPaw      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 2.2 LLM Providers Compared

| Provider | Strengths | Best For | Context Window | Cost |
|----------|----------|----------|---------------|------|
| **GPT-4o** | General excellence, function calling | Complex reasoning, production agents | 128K tokens | $$ |
| **Claude 3.5 Sonnet** | Long context, safety, writing quality | Documents, research, safety-critical apps | 200K tokens | $$ |
| **Gemini 1.5 Pro** | 1M token context, multimodal | Long document analysis | 1M tokens | $$ |
| **Llama 3** | Open-source, local deployment | Privacy-sensitive, custom fine-tuning | 128K tokens | Free |

---

## 2.3 The AI Tooling Ecosystem

### Key Tool Categories

```
┌─────────────────────────────────────────────────────────────────┐
│                    AI TOOLING LANDSCAPE                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  🏗️ ORCHESTRATION          🤖 AGENTS              💬 FRAMEWORKS   │
│  ├── OpenClaw               ├── AutoGPT            ├── LangChain  │
│  ├── CoPaw                  ├── CrewAI              ├── LlamaIndex │
│  ├── LangFlow               ├── Manus               ├── AutoGen   │
│  ├── n8n                    ├── Claude Agents       ├── Semantic  │
│  └── Make.com               └── GPT Teams           └──────────── │
│                                                                 │
│  🧠 MEMORY/KNOWLEDGE        🌐 BROWSING              🔧 CODE       │
│  ├── Pinecone                ├── Firecrawl           ├── Bash      │
│  ├── ChromaDB                ├── Jina Reader          ├── Python    │
│  ├── Weaviate                ├── Browserbase         ├── JavaScript│
│  └── Qdrant                  └── Playwright          └──────────── │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### The Key Protocols

**Function Calling / Tool Calling**
```json
// Example: OpenAI Function Call
{
  "name": "get_weather",
  "description": "Get current weather for a city",
  "parameters": {
    "type": "object",
    "properties": {
      "city": {"type": "string"},
      "unit": {"type": "string", "enum": ["celsius", "fahrenheit"]}
    }
  }
}
```

**API Authentication**
| Method | Use Case |
|--------|---------|
| API Key | Simple, direct authentication |
| OAuth 2.0 | User-authorised access (Google, GitHub login) |

---

## 2.3 LLM Providers Compared

| Provider | Strengths | Best For | Context Window | Cost |
|----------|----------|----------|---------------|------|
| **GPT-4o** | General excellence, function calling | Complex reasoning, production agents | 128K tokens | $$ |
| **Claude 3.5 Sonnet** | Long context, safety, writing quality | Documents, research, safety-critical apps | 200K tokens | $$ |
| **Gemini 1.5 Pro** | 1M token context, multimodal | Long document analysis | 1M tokens | $$ |
| **Llama 3** | Open-source, local deployment | Privacy-sensitive, custom fine-tuning | 128K tokens | Free |

---

## 2.4 Exercises & Assessment

### Exercise 1: Component Matching

**Scenario:** A retail company wants an AI agent that monitors competitor prices, alerts them to price changes, and automatically adjusts their prices.

| Component | What It Does | Which Layer? |
|-----------|------------|-------------|
| Connects to competitor websites | _______________ | _______________ |
| Decides when to change prices | _______________ | _______________ |
| Stores pricing history | _______________ | _______________ |
| Coordinates all other components | _______________ | _______________ |

**Answers:** Web scraping/Tool Layer | Decision Making/Orchestration Layer | Memory/Memory Layer | Orchestration/Orchestration Layer

---

### Exercise 2: Era Classification (5 minutes)

Classify each AI system by era:

| # | Description | Era |
|---|-------------|-----|
| 1 | A spam filter that learns from user reports | |
| 2 | ChatGPT that writes creative stories | |
| 3 | An agent that books flights and hotels automatically | |
| 4 | A calculator that follows BEDMAS rules | |

**Answers:** 1=ML Era | 2=Generative AI | 3=Agentic AI | 4=Rules-Based

---

## Discussion Questions

1. **Technical:** How does the orchestration layer differ from simply calling an LLM API directly?

2. **Strategic:** What are the trade-offs between using a general-purpose LLM vs. a fine-tuned, domain-specific model?

3. **Practical:** Which AI provider would you choose for your organisation and why?

---

## Module 2 Quiz

**1.** What is AI orchestration?
- A) Writing prompts for LLMs
- B) The coordination layer connecting AI models, tools, memory, and actions
- C) Training machine learning models
- D) Building chatbots

**2.** Which layer gives an AI agent "hands"?
- A) Model Layer
- B) Orchestration Layer
- C) Tool Layer
- D) Memory Layer

**3.** Which provider has a 1 million token context window?
- A) GPT-4o
- B) Claude 3.5
- C) Llama 3
- D) Gemini 1.5

**4.** What are the Three Eras of AI?
- A) Desktop → Internet → Cloud
- B) Rules-Based → ML/Supervised → Agentic AI
- C) Chatbots → Agents → Robots
- D) Training → Deployment → Monitoring

**5.** What does a webhook do?
- A) Schedules tasks for a specific time
- B) Triggers an action when an external event occurs
- C) Stores conversation history
- D) Authenticates API requests

---

### Quiz Answers

| Q | Answer |
|---|--------|
| 1 | B |
| 2 | C |
| 3 | D |
| 4 | B |
| 5 | B |

---

## Module 2 Summary

✅ **AI Orchestration** = Coordination layer connecting models, tools, and memory

✅ **Four Eras of AI:** Rules-Based → ML/Supervised → Generative AI → Agentic AI

✅ **Core Stack Components:** Orchestration Layer, LLM Provider, Vector Database, Tool Connectors, Memory System

✅ **Provider Selection** depends on: context needs, cost, safety, offline capability

✅ **Function Calling** enables LLMs to use external tools through structured schemas

---

*Module 2 complete. You're building the technical foundation!*