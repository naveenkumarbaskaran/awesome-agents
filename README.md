<div align="center">

# 🤖 Awesome Agents

[![Awesome](https://awesome.re/badge-flat2.svg)](https://awesome.re)
[![GitHub Stars](https://img.shields.io/github/stars/naveenkumarbaskaran/awesome-agents?style=flat-square&logo=github&color=yellow)](https://github.com/naveenkumarbaskaran/awesome-agents/stargazers)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](https://github.com/naveenkumarbaskaran/awesome-agents/blob/main/CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](https://opensource.org/licenses/MIT)
[![Agents](https://img.shields.io/badge/agents-65%2B-brightgreen?style=flat-square)](https://github.com/naveenkumarbaskaran/awesome-agents)
[![Made with Python](https://img.shields.io/badge/Made%20with-Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)

**A curated collection of 65+ production-ready AI agent implementations.**
From one-shot utilities to multi-agent enterprise systems — runnable on day one.

[Coding](#-coding-agents) •
[DevOps](#-devops-agents) •
[SAP + Enterprise](#-sap--enterprise-agents) •
[Data](#-data-agents) •
[Research](#-research-agents) •
[Communication](#-communication-agents) •
[Finance](#-finance-agents) •
[Multi-Agent](#-multi-agent--protocol) •
[LLM Infra](#-llm-infrastructure) •
[Productivity](#-productivity-agents) •
[PEOS Architecture](#the-peos-architecture) •
[Quickstart](#quickstart) •
[Contributing](#contributing)

</div>

---

## Why This List?

Most "awesome AI" lists are link dumps. This one is different:

- Every repo ships **runnable code**, not pseudocode
- Every entry shows the **stack** so you can evaluate fit in five seconds
- Sections map to **real engineering problems** — pick a category, find a solution
- The flagship repos implement the [PEOS Architecture](#the-peos-architecture) — a production pattern that achieves 77% token reduction over naive agent loops

---

## The PEOS Architecture

The best agents in this collection are built on **PEOS** — a four-phase pattern that separates planning from execution and prevents error cascades.

```
┌──────────────────────────────────────────────────────────────┐
│                        PLANNER                               │
│  • Classifies intent from user query                         │
│  • Selects ONLY relevant tools (dynamic binding)             │
│  • Outputs JSON execution plan                               │
│  • Uses 3-turn sliding window (not full history)             │
└────────────────────────────┬─────────────────────────────────┘
                             │
                             ▼
┌──────────────────────────────────────────────────────────────┐
│                        EXECUTOR                              │
│  • Receives ONLY the tools specified in plan                 │
│  • Loops up to N iterations (configurable)                   │
│  • Results capped at 50 KB per tool call                     │
│  • Automatic retry with exponential backoff                  │
└────────────────────────────┬─────────────────────────────────┘
                             │
                             ▼
┌──────────────────────────────────────────────────────────────┐
│                        OBSERVER                              │
│  • Validates execution completeness                          │
│  • Checks business rules (write safety, data quality)        │
│  • Routes to HITL gate if write operation detected           │
│  • Can request re-execution with modified params             │
└────────────────────────────┬─────────────────────────────────┘
                             │
                             ▼
┌──────────────────────────────────────────────────────────────┐
│                        SYNTHESISER                           │
│  • Applies response templates (cards, tables, markdown)      │
│  • Generates contextual quick replies                        │
│  • Enforces UI constraints (char limits, schema validation)  │
│  • Zero hallucination — data-driven rendering only           │
└──────────────────────────────────────────────────────────────┘
```

**Benchmark vs naive ReAct loop (AgentForge, 1k requests):**

| Metric | Naive Agent | PEOS Agent | Delta |
|--------|-------------|------------|-------|
| Tokens / request | 18,400 | 4,200 | **-77%** |
| Latency (avg) | 12.3 s | 3.8 s | **-69%** |
| Cost / 1k requests | $14.70 | $3.36 | **-77%** |
| Error leaks | Uncontrolled | 0 | **100% eliminated** |

---

## Quickstart

Five copy-paste examples to get an agent running in under two minutes.

**1. Natural language to SQL**
```bash
pip install sql-agent-ai
sql-agent --db postgresql://user:pass@localhost/mydb
# > "show me all orders over $500 from last week"
```

**2. Debug any stack trace**
```bash
pip install debug-agent-ai
debug-agent --trace error.log
# Outputs: root cause, affected line, patch suggestion
```

**3. SAP OData natural language query**
```bash
pip install odataagent
odataagent --service https://my-s4.example.com/odata/v4/Orders
# > "list all open purchase orders for vendor 1000042"
```

**4. Token cost monitoring (drop-in decorator)**
```python
from tokmon import watch

@watch(budget_usd=0.50)
def my_agent_call(prompt):
    # your LLM call here — tokmon will alert if budget is hit
    ...
```

**5. Multi-agent orchestration with NeuralHive**
```bash
pip install neuralhive
neuralhive init --mode supervisor
# Spawns planner + executor + reviewer crew automatically
```

---

## 🔧 Coding Agents

Agents that read, write, test, and transform code.

| Agent | What it does | Stack | Quickstart |
|-------|-------------|-------|------------|
| [sql-agent](https://github.com/naveenkumarbaskaran/sql-agent) | Natural language to SQL for any database | Python, LangChain, SQLAlchemy | `pip install sql-agent-ai` |
| [debug-agent](https://github.com/naveenkumarbaskaran/debug-agent) | Paste stack trace, get root cause + fix | Python, Claude/GPT-4o | `pip install debug-agent-ai` |
| [test-gen-agent](https://github.com/naveenkumarbaskaran/test-gen-agent) | Reads your code, writes pytest tests | Python, AST, pytest | `pip install test-gen-agent` |
| [doc-agent](https://github.com/naveenkumarbaskaran/doc-agent) | Auto-generates and syncs API documentation | Python, OpenAI, Markdown | `pip install doc-agent-ai` |
| [refactor-agent](https://github.com/naveenkumarbaskaran/refactor-agent) | Detects code smells, applies fixes with diffs | Python, tree-sitter, Claude | `pip install refactor-agent` |
| [security-agent](https://github.com/naveenkumarbaskaran/security-agent) | OWASP Top 10, secrets, CVE scanning | Python, Semgrep, NVD API | `pip install security-agent-ai` |
| [api-gen-agent](https://github.com/naveenkumarbaskaran/api-gen-agent) | English description → FastAPI + OpenAPI spec | Python, FastAPI, Pydantic | `pip install api-gen-agent` |
| [lint-agent](https://github.com/naveenkumarbaskaran/lint-agent) | AI linting that learns your codebase style | Python, AST, LLM | `pip install lint-agent-ai` |
| [dep-agent](https://github.com/naveenkumarbaskaran/dep-agent) | Reads changelogs, assesses risk, opens update PRs | Python, GitHub API, LLM | `pip install dep-agent-ai` |
| [migrate-agent](https://github.com/naveenkumarbaskaran/migrate-agent) | Safe database migration script generation | Python, Alembic, LLM | `pip install migrate-agent` |

---

## 🚀 DevOps Agents

Agents that automate infrastructure, deployments, and incident response.

| Agent | What it does | Stack | Quickstart |
|-------|-------------|-------|------------|
| [deploy-agent](https://github.com/naveenkumarbaskaran/deploy-agent) | Reads project, generates Dockerfile + k8s manifests | Python, Docker, Kubernetes, LLM | `pip install deploy-agent-ai` |
| [incident-agent](https://github.com/naveenkumarbaskaran/incident-agent) | Log analysis, alert correlation, RCA | Python, OpenTelemetry, LLM | `pip install incident-agent` |
| [ci-agent](https://github.com/naveenkumarbaskaran/ci-agent) | Reads project, writes GitHub Actions workflows | Python, GitHub API, LLM | `pip install ci-agent-ai` |
| [monitor-agent](https://github.com/naveenkumarbaskaran/monitor-agent) | Generates Prometheus alerts, Grafana dashboards, runbooks | Python, Prometheus, Grafana API | `pip install monitor-agent` |
| [cost-agent](https://github.com/naveenkumarbaskaran/cost-agent) | Cloud cost analysis, waste detection, savings report | Python, AWS/GCP/Azure SDK, LLM | `pip install cost-agent-ai` |

---

## 🏭 SAP + Enterprise Agents

Production-grade agents for SAP and enterprise ecosystems — built by an engineer from SAP Labs.

| Agent | What it does | Stack | Quickstart |
|-------|-------------|-------|------------|
| [OData-MCP-Server](https://github.com/naveenkumarbaskaran/OData-MCP-Server) | SAP OData V2/V4 as AI tools via MCP | Python, MCP, SAP OData | `pip install odata-mcp-server` |
| [ODataAgent](https://github.com/naveenkumarbaskaran/ODataAgent) | Natural language querying of OData services | Python, LangChain, OData | `pip install odataagent` |
| [a2a-sap-agent](https://github.com/naveenkumarbaskaran/a2a-sap-agent) | S/4HANA maintenance agent on A2A protocol | Python, A2A, SAP APIs | `pip install a2a-sap-agent` |
| [AgentForge](https://github.com/naveenkumarbaskaran/AgentForge) | Production enterprise agent framework (PEOS, 77% token savings) | Python, LangGraph, PEOS | `pip install agentforge-ai` |
| [PEOSGraph](https://github.com/naveenkumarbaskaran/PEOSGraph) | LangGraph PEOS implementation | Python, LangGraph, PEOS | `pip install peosgraph` |
| [AgentGuard](https://github.com/naveenkumarbaskaran/AgentGuard) | Security guardrails for enterprise agents | Python, HITL, Policy Engine | `pip install agentguard-ai` |
| [K8s-Copilot-MCP](https://github.com/naveenkumarbaskaran/K8s-Copilot-MCP) | Kubernetes management via AI and MCP | Python, MCP, kubectl, k8s API | `pip install k8s-copilot-mcp` |
| [Grafana-Insights-MCP](https://github.com/naveenkumarbaskaran/Grafana-Insights-MCP) | Grafana dashboards + alerts via MCP | Python, MCP, Grafana API | `pip install grafana-insights-mcp` |
| [Confluence-MCP](https://github.com/naveenkumarbaskaran/Confluence-MCP) | Confluence wiki search via MCP | Python, MCP, Confluence REST | `pip install confluence-mcp` |
| [abap-ai-workspace](https://github.com/naveenkumarbaskaran/abap-ai-workspace) | AI-assisted ABAP development | Python, ABAP, LLM, SAP APIs | `pip install abap-ai-workspace` |

---

## 📊 Data Agents

Agents that build pipelines, profile datasets, and generate visualizations.

| Agent | What it does | Stack | Quickstart |
|-------|-------------|-------|------------|
| [data-pipeline-agent](https://github.com/naveenkumarbaskaran/data-pipeline-agent) | English description → ETL pipeline code | Python, Pandas, SQLAlchemy, LLM | `pip install data-pipeline-agent` |
| [data-quality-agent](https://github.com/naveenkumarbaskaran/data-quality-agent) | Data profiling, anomaly detection, lineage | Python, Great Expectations, LLM | `pip install data-quality-agent` |
| [viz-agent](https://github.com/naveenkumarbaskaran/viz-agent) | Natural language → Plotly chart | Python, Plotly, LLM | `pip install viz-agent-ai` |
| [schema-agent](https://github.com/naveenkumarbaskaran/schema-agent) | DB schema documentation + Mermaid ER diagrams | Python, SQLAlchemy, Mermaid, LLM | `pip install schema-agent-ai` |
| [notebook-agent](https://github.com/naveenkumarbaskaran/notebook-agent) | Task description → Jupyter notebook | Python, nbformat, LLM | `pip install notebook-agent` |

---

## 🔬 Research Agents

Agents that search the web, analyze papers, and surface intelligence.

| Agent | What it does | Stack | Quickstart |
|-------|-------------|-------|------------|
| [research-agent](https://github.com/naveenkumarbaskaran/research-agent) | Web search, source verification, cited reports | Python, Tavily, LLM | `pip install research-agent-ai` |
| [paper-agent](https://github.com/naveenkumarbaskaran/paper-agent) | Academic paper analysis and summarization | Python, arXiv API, LLM | `pip install paper-agent-ai` |
| [news-agent](https://github.com/naveenkumarbaskaran/news-agent) | Topic monitoring, signal detection, daily briefings | Python, NewsAPI, LLM | `pip install news-agent-ai` |
| [competitive-agent](https://github.com/naveenkumarbaskaran/competitive-agent) | Track competitor moves, pricing, job postings | Python, SerpAPI, LLM | `pip install competitive-agent` |
| [patent-agent](https://github.com/naveenkumarbaskaran/patent-agent) | Patent search, prior art, claim analysis | Python, USPTO API, LLM | `pip install patent-agent-ai` |

---

## 💬 Communication Agents

Agents that handle email, meetings, Slack, Jira, and LinkedIn.

| Agent | What it does | Stack | Quickstart |
|-------|-------------|-------|------------|
| [email-agent](https://github.com/naveenkumarbaskaran/email-agent) | Email triage, classification, reply drafting | Python, Gmail/IMAP, LLM | `pip install email-agent-ai` |
| [meeting-agent](https://github.com/naveenkumarbaskaran/meeting-agent) | Transcript → action items + follow-up email | Python, Whisper, LLM | `pip install meeting-agent-ai` |
| [slack-agent](https://github.com/naveenkumarbaskaran/slack-agent) | Slack bot answering from docs, thread summaries | Python, Slack Bolt, RAG, LLM | `pip install slack-agent-ai` |
| [jira-agent](https://github.com/naveenkumarbaskaran/jira-agent) | Natural language → Jira issues, triage, linking | Python, Jira REST API, LLM | `pip install jira-agent-ai` |
| [linkedin-agent](https://github.com/naveenkumarbaskaran/linkedin-agent) | LinkedIn post drafting and engagement analysis | Python, LinkedIn API, LLM | `pip install linkedin-agent-ai` |

---

## 💰 Finance Agents

Agents that process invoices, contracts, forecasts, and expense reports.

| Agent | What it does | Stack | Quickstart |
|-------|-------------|-------|------------|
| [invoice-agent](https://github.com/naveenkumarbaskaran/invoice-agent) | Extract fields, validate, match POs, flag anomalies | Python, OCR, LLM | `pip install invoice-agent-ai` |
| [contract-agent](https://github.com/naveenkumarbaskaran/contract-agent) | Clause extraction, risk flagging, template comparison | Python, pdfplumber, LLM | `pip install contract-agent-ai` |
| [forecast-agent](https://github.com/naveenkumarbaskaran/forecast-agent) | Time series forecasting with scenario narratives | Python, Prophet, LLM | `pip install forecast-agent-ai` |
| [expense-agent](https://github.com/naveenkumarbaskaran/expense-agent) | Categorize, detect policy violations, audit report | Python, OCR, LLM | `pip install expense-agent-ai` |
| [report-agent](https://github.com/naveenkumarbaskaran/report-agent) | Pull data, analyze trends, write business narrative | Python, Pandas, LLM | `pip install report-agent-ai` |

---

## 🤝 Multi-Agent + Protocol

Orchestration frameworks, protocol bridges, and swarm systems.

| Agent | What it does | Stack | Quickstart |
|-------|-------------|-------|------------|
| [mcp-a2a-bridge](https://github.com/naveenkumarbaskaran/mcp-a2a-bridge) | Bidirectional MCP ↔ A2A bridge | Python, MCP, A2A | `pip install mcp-a2a-bridge` |
| [A2A-Kit](https://github.com/naveenkumarbaskaran/A2A-Kit) | A2A protocol toolkit | Python, A2A protocol | `pip install a2a-kit` |
| [agent-gateway](https://github.com/naveenkumarbaskaran/agent-gateway) | Universal protocol gateway (A2A, MCP, OpenAI, REST) | Python, FastAPI, multi-protocol | `pip install agent-gateway-ai` |
| [NeuralHive](https://github.com/naveenkumarbaskaran/NeuralHive) | Multi-agent orchestration (supervisor, swarm, router) | Python, LangGraph, LLM | `pip install neuralhive` |
| [SwarmLab](https://github.com/naveenkumarbaskaran/SwarmLab) | Swarm intelligence simulation framework | Python, asyncio, LLM | `pip install swarmlab-ai` |
| [hive](https://github.com/naveenkumarbaskaran/hive) | 13-phase AI development lifecycle agent crew | Python, CrewAI, LangGraph | `pip install hive-agents` |
| [agent-flow](https://github.com/Rajeshdevandla/agent-flow) | 6-agent Constitutional AI orchestration system with safety layer, eval framework, and full decision audit trail | Python, Anthropic Claude SDK, FastAPI | Clone + run |

---

## 🛠️ LLM Infrastructure

Observability, prompt management, testing, and cost control for LLM systems.

| Tool | What it does | Stack | Quickstart |
|------|-------------|-------|------------|
| [TokenShield](https://github.com/naveenkumarbaskaran/TokenShield) | Real-time token cost monitoring + budget gates | Python, OpenAI/Anthropic SDK | `pip install tokenshield` |
| [context-budget](https://github.com/naveenkumarbaskaran/context-budget) | Drop-in context window manager | Python, LangChain compatible | `pip install context-budget` |
| [tokmon](https://github.com/naveenkumarbaskaran/tokmon) | Lightweight token/cost tracker with decorators | Python, decorator pattern | `pip install tokmon` |
| [promptlab](https://github.com/naveenkumarbaskaran/promptlab) | Git for prompts — version, diff, A/B test | Python, CLI, YAML | `pip install promptlab-ai` |
| [consync](https://github.com/naveenkumarbaskaran/consync) | Sync constants between spreadsheets and code | Python, Google Sheets API | `pip install consync` |
| [agent-diff](https://github.com/naveenkumarbaskaran/agent-diff) | PR reviewer for AI-generated code | Python, GitHub API, LLM | `pip install agent-diff` |
| [pytest-agents](https://github.com/naveenkumarbaskaran/pytest-agents) | Pytest plugin for testing AI agents | Python, pytest, LLM eval | `pip install pytest-agents` |
| [PromptForge](https://github.com/naveenkumarbaskaran/PromptForge) | Enterprise prompt engineering toolkit | Python, LLM, versioning | `pip install promptforge-ai` |
| [claude-hooks-hub](https://github.com/naveenkumarbaskaran/claude-hooks-hub) | Installable Claude Code hooks | Shell, Python, Claude Code | see repo |
| [codewise](https://github.com/naveenkumarbaskaran/codewise) | LLM-agnostic code review + security scanning | Python, CLI, multi-provider | `pip install codewise` |

---

## 🌱 Productivity Agents

Agents for learning, goal tracking, journaling, and daily life.

| Agent | What it does | Stack | Quickstart |
|-------|-------------|-------|------------|
| [learn-agent](https://github.com/naveenkumarbaskaran/learn-agent) | Adaptive quizzes, spaced repetition, concept maps | Python, LLM, Anki-compatible | `pip install learn-agent-ai` |
| [goal-agent](https://github.com/naveenkumarbaskaran/goal-agent) | Break goals into tasks, track progress, daily nudges | Python, LLM, scheduler | `pip install goal-agent-ai` |
| [journal-agent](https://github.com/naveenkumarbaskaran/journal-agent) | Daily prompts, mood tracking, weekly reflections | Python, LLM, local storage | `pip install journal-agent-ai` |
| [recipe-agent](https://github.com/naveenkumarbaskaran/recipe-agent) | Suggest meals, scale servings, shopping list | Python, LLM, nutrition APIs | `pip install recipe-agent-ai` |
| [travel-agent-ai](https://github.com/naveenkumarbaskaran/travel-agent-ai) | Full trip planning — itinerary, budget, packing list | Python, Maps API, LLM | `pip install travel-agent-ai` |

---

## Contributing

All contributions are welcome. To add an agent:

1. Fork the repo
2. Add a row to the relevant section in `README.md`
3. Make sure the repo you're linking to has a working `README.md` and install instructions
4. Open a PR with title: `Add [repo-name] to [Section]`

See [CONTRIBUTING.md](https://github.com/naveenkumarbaskaran/awesome-agents/blob/main/CONTRIBUTING.md) for full guidelines.

---

## About

Curated by [Naveen Kumar Baskaran](https://github.com/naveenkumarbaskaran), AI agent engineer at SAP Labs India.

Focus areas: enterprise multi-agent systems, the A2A and MCP protocols, production LLM patterns, and SAP AI integration.

If this list saved you time, consider starring the repo — it helps others find it.

[![GitHub Stars](https://img.shields.io/github/stars/naveenkumarbaskaran/awesome-agents?style=social)](https://github.com/naveenkumarbaskaran/awesome-agents/stargazers)

---

<div align="center">
<sub>Made with care. Licensed MIT. PRs welcome.</sub>
</div>
