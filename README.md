<div align="center">

<br/>

```
░█████╗░██████╗░██╗░█████╗░
██╔══██╗██╔══██╗██║██╔══██╗
███████║██████╔╝██║███████║
██╔══██║██╔══██╗██║██╔══██║
██║░░██║██║░░██║██║██║░░██║
╚═╝░░╚═╝╚═╝░░╚═╝╚═╝╚═╝░░╚═╝
```

### Autonomous Research Intelligence Agent

**An AI-powered research automation system built entirely inside Claude.ai —**
**no backend, no IDE, no deployment. Just prompts.**

<br/>

[![Built with Claude](https://img.shields.io/badge/Built%20with-Claude%20AI-00d4ff?style=flat-square&logo=anthropic&logoColor=white)](https://claude.ai)
[![Notion MCP](https://img.shields.io/badge/Notion-MCP%20Connector-7c3aed?style=flat-square&logo=notion&logoColor=white)](https://notion.so)
[![Web Search](https://img.shields.io/badge/Tool-Web%20Search-10b981?style=flat-square)](https://docs.anthropic.com)
[![ReAct Framework](https://img.shields.io/badge/Framework-ReAct%20Loop-f59e0b?style=flat-square)](https://arxiv.org/abs/2210.03629)
[![License: MIT](https://img.shields.io/badge/License-MIT-94a3b8?style=flat-square)](LICENSE)

<br/>

![ARIA Demo](https://placehold.co/860x440/07090f/00d4ff?text=ARIA+·+AI+Research+Papers+Database&font=monospace)

<br/>

</div>

---

## What is ARIA?

**ARIA** (Autonomous Research Intelligence Agent) is a fully autonomous AI research assistant that discovers, analyzes, and stores academic AI research papers — automatically, every day.

It was built entirely through a **single Claude.ai conversation** using structured prompt engineering, the Notion MCP connector, and Claude's built-in web search tool. No separate backend. No API integrations. No deployment pipeline.

Every day at **10:00 AM IST**, ARIA:

1. Searches **arXiv, Semantic Scholar, and Google Scholar** for high-impact AI papers
2. Analyzes each paper using the **ReAct reasoning framework**
3. Checks for **duplicates** before storing
4. Creates a **Notion database entry** with 14 structured properties
5. Writes a **full analysis page** inside each entry — Summary, Key Findings, Technical Contribution, Future Vision, and more
6. Rates each paper on an **Importance Score (1–10)**

---

## Features

| Feature | Description |
|---|---|
| 🔬 **Daily Research Cycle** | Discovers 3 high-impact AI papers every day across arXiv, Semantic Scholar, Google Scholar |
| 🗄 **Notion Knowledge Base** | Creates and populates the *AI Research Papers* database with 14 properties and 5 smart views |
| 📄 **Rich Analysis Pages** | Each paper gets a full structured page — Summary, Key Findings, Technical Contribution, Future Vision, Related Papers, Personal Notes |
| 🔍 **Deduplication** | Checks if a paper already exists before creating an entry — no duplicate rows |
| ⏰ **IST Scheduler** | Auto-runs at 10:00 AM IST daily with a live countdown timer and run history |
| ⚙️ **Agent Execution Trace** | Live step-by-step log of ARIA's reasoning — Plan → Search → Analyze → Store |
| 🛡️ **Self-Critique Mode** | ARIA verifies its own outputs before finalizing — papers real? citations accurate? |
| 🔖 **5 Smart Notion Views** | Latest Research · Most Influential · AI Agents · Deep Dive Queue · High Impact Papers |

---

## Tech Stack

```
┌─────────────────────────────────────────────────────────┐
│                        ARIA Stack                       │
├──────────────────┬──────────────────────────────────────┤
│  Frontend        │  React (JSX Artifact in Claude.ai)   │
│  Agent Brain     │  Claude claude-sonnet-4-20250514     │
│  Web Research    │  web_search_20250305 tool            │
│  Knowledge Base  │  Notion MCP Connector                │
│  Scheduler       │  JavaScript setInterval (IST)        │
│  Memory          │  Conversation history array          │
│  Deduplication   │  Title-match in storage prompt       │
└──────────────────┴──────────────────────────────────────┘
```

---

## How It Was Built

> **This entire system was built through conversation — no code editor, no terminal, no deployment.**

### The Build Process

```
01  PROMPT ENGINEERING
    Designed ARIA's system prompt using ReAct framework,
    AutoGPT-style 8-step loop, and strict output format templates.

02  WEB SEARCH TOOL
    Connected Claude's built-in web_search_20250305 tool for
    real-time discovery from academic databases.

03  NOTION MCP CONNECTOR
    Enabled the Notion MCP connector in Claude settings.
    ARIA can create databases, write pages, and manage entries.

04  DATABASE ARCHITECTURE
    Designed a 14-property Notion schema. Each paper = one row
    + a rich analysis page inside that row.

05  AGENT LOOP
    Implemented AutoGPT-style 8-step loop with deduplication
    built into the storage step.

06  SCHEDULER
    Built a browser-based IST scheduler. At 10:00 AM IST,
    ARIA auto-triggers and populates the Notion database.
```

### The Prompt Architecture

ARIA's behavior is entirely defined by its system prompt — structured like a program:

```
┌─────────────────────────────────────────────┐
│              ARIA System Prompt             │
├─────────────────────────────────────────────┤
│  Identity Layer      →  Name, role, persona │
│  ReAct Framework     →  Reason→Act→Observe  │
│  AutoGPT Loop        →  8-step task cycle   │
│  Output Template     →  Exact report format │
│  Notion Rules        →  DB + page structure │
│  Page Template       →  8-section analysis  │
│  Constraints         →  No hallucinations   │
│  Self-Critique       →  Verify own outputs  │
└─────────────────────────────────────────────┘
```

> **Key insight:** Treating the prompt like a program — with specific rules, templates, and constraints — produces reliable, autonomous behavior.

---

## Notion Database Schema

The *AI Research Papers* database has **14 properties**:

| Property | Type | Purpose |
|---|---|---|
| Title | `title` | Primary key — paper name |
| Authors | `rich_text` | Author names |
| Year | `number` | Publication year |
| Publication | `select` | arXiv / NeurIPS / ICML / ACL / ICLR / CVPR |
| Paper Link | `url` | Direct link to paper |
| Citation Count | `number` | Influence metric |
| Research Category | `multi_select` | LLM Architecture, AI Agents, RAG, Safety… |
| Key Idea | `rich_text` | One-sentence core insight |
| Significance | `rich_text` | Why it matters now |
| Future Impact | `rich_text` | Long-term implications |
| Date Added | `date` | Auto-set by ARIA |
| Status | `select` | New / Reviewed / Deep Dive |
| Importance Score | `number` | ARIA's rating 1–10 |

### 5 Smart Views

| View | Logic |
|---|---|
| 📊 Latest Research | Sort by Date Added ↓ |
| 🔥 Most Influential | Sort by Citation Count ↓ |
| 🤖 AI Agents Research | Filter: Category contains "AI Agents" |
| 📚 Deep Dive Queue | Filter: Status = "New" |
| 🚀 High Impact Papers | Filter: Importance Score ≥ 8 |

---

## Page Content Template

Every database row opens as a full Notion page with this structure:

```markdown
# Research Paper Analysis

## 📄 Paper Summary
High-level explanation of the research.

## 🔍 Key Findings
• Finding 1
• Finding 2
• Finding 3

## 🔬 Technical Contribution
What new method or innovation this paper introduces.

## ⚡ Why This Research Matters
Importance in the current AI ecosystem.

## 🔭 Future Vision
Possible long-term impact on AI development.

## 💡 Key Takeaways
• Takeaway 1
• Takeaway 2

## 📚 Related Papers
Papers worth exploring next.

## ✏️ Personal Research Notes
← Your own thoughts go here
```

---

## Research Categories

ARIA tags every paper with one or more of these multi-select categories:

```
LLM Architecture          AI Agents
Retrieval Augmented Generation    AI Infrastructure
Model Optimization        Alignment & Safety
Multimodal AI             Robotics AI
Training Methods          Evaluation Methods
```

---

## ReAct Reasoning Framework

ARIA uses the **ReAct** (Reasoning + Acting) framework for every research task:

```
┌─────────┐     ┌─────────┐     ┌─────────┐     ┌─────────┐
│  REASON │ ──► │   ACT   │ ──► │ OBSERVE │ ──► │ REFLECT │
│         │     │         │     │         │     │         │
│ Think   │     │ Search  │     │ Review  │     │ Refine  │
│ about   │     │ analyze │     │ results │     │ & store │
│ task    │     │ retrieve│     │         │     │         │
└─────────┘     └─────────┘     └─────────┘     └─────────┘
```

Combined with the **AutoGPT-style task loop**:

```
Plan → Discover → Filter → Analyze → Synthesize → Reflect → Store → Learn
```

---

## Self-Critique Mode

Before finalizing any report, ARIA verifies its own outputs:

```
SELF-CRITIQUE CHECK
├── Are all papers real?          [YES / UNCERTAIN]
├── Are citations accurate?       [YES / UNCERTAIN]
├── Are summaries faithful?       [YES / UNCERTAIN]
└── Are insights logically derived? [YES / UNCERTAIN]
```

If uncertainty exists, ARIA explicitly flags it in the output rather than presenting guesses as facts.

---

## Try It Free

ARIA is available as a **free prototype** inside Claude.ai — no API key needed. The artifact calls the Anthropic API through Claude's built-in access.

**To use it:**

1. Open [claude.ai](https://claude.ai)
2. Load the ARIA artifact from this repository
3. *(Optional)* Enable the **Notion MCP connector** in Claude settings for database storage
4. Click **"🔬 Run Daily Research Cycle"** and watch ARIA work

---

## Project Structure

```
ARIA/
├── ARIA.jsx                      # Main React artifact (free prototype)
├── ARIA_Standalone.html          # Standalone HTML version (requires API key)
├── ARIA_Portfolio_Case_Study.docx  # Full build documentation
├── ARIA.mp4                        # Prototype video
└── README.md                     # This file
```

---

## Key Learnings

Building ARIA taught me that **prompt engineering is software engineering** — when done with the same rigor:

- **Specificity beats vagueness** — every rule in ARIA's prompt is unambiguous
- **Structured output templates** make responses machine-parseable, not just human-readable
- **MCP connectors are superpowers** — they turn a chatbot into a real automation system
- **Iterative refinement works** — the final system emerged through 6+ rounds of conversation
- **The database-as-knowledge-base pattern** — each row opening as a full analysis page is far more valuable than a flat log

---

## What This Demonstrates

> A system that would normally require a backend server, a database, multiple API integrations, and weeks of engineering — built entirely in conversation.

```
Structured Prompts  +  MCP Connectors  +  Built-in Tools  +  Iterative Refinement
        =
A deployable autonomous research agent
```

---

## Built With

- [Claude AI](https://anthropic.com) — Anthropic's AI assistant
- [Notion](https://notion.so) — Knowledge base and database
- [Notion MCP](https://mcp.notion.com) — Model Context Protocol connector
- [ReAct Paper](https://arxiv.org/abs/2210.03629) — Reasoning + Acting framework
- [arXiv](https://arxiv.org) — Open-access research repository

---

<div align="center">

Built with [Claude AI](https://claude.ai) · No backend · No IDE · Just prompts

<br/>

*"The best architecture is the one you can explain to a language model."*

</div>
