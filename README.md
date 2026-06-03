<div align="center">

# 🤖 Awesome Agents

**50+ AI agent apps you can actually run.**

Clone. Customize. Ship.

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![Stars](https://img.shields.io/github/stars/naveenkumarbaskaran/awesome-agents?style=flat-square&color=yellow)](https://github.com/naveenkumarbaskaran/awesome-agents/stargazers)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](LICENSE)

[MCP Agents](#-mcp-agents) • [A2A Agents](#-a2a-agents) • [SAP Agents](#-sap--enterprise-agents) • [RAG Agents](#-rag--knowledge-agents) • [Multi-Agent](#-multi-agent-systems) • [LLM Tools](#-llm-tools--infrastructure) • [Contribute](#contributing)

</div>

---

> A curated collection of production-ready AI agent patterns — not toy demos.
> Each entry links to a working implementation with a quickstart.
> Built by an AI engineer at SAP Labs who ships agents to production daily.

---

## 🔌 MCP Agents

Model Context Protocol servers that turn any tool into an AI-callable interface.

| Repo | What it does | Stack | Run |
|------|-------------|-------|-----|
| [OData-MCP-Server](https://github.com/naveenkumarbaskaran/OData-MCP-Server) | Expose any SAP OData V2/V4 service as AI tools — zero boilerplate | Python | `pip install odata-mcp` |
| [K8s-Copilot-MCP](https://github.com/naveenkumarbaskaran/K8s-Copilot-MCP) | Kubernetes cluster management via AI — list pods, scale deployments, read logs | Python | `pip install k8s-copilot-mcp` |
| [Grafana-Insights-MCP](https://github.com/naveenkumarbaskaran/Grafana-Insights-MCP) | Query Grafana dashboards and alerting data through AI | Python | `pip install grafana-insights-mcp` |
| [Confluence-MCP](https://github.com/naveenkumarbaskaran/Confluence-MCP) | Search and retrieve Confluence wiki pages via MCP | Python | `pip install confluence-mcp` |
| [abap-ai-workspace](https://github.com/naveenkumarbaskaran/abap-ai-workspace) | AI-assisted ABAP development — 15 Claude Code skills, VS Code integration | JS | `npm i -g abap-ai-workspace` |

---

## 🤝 A2A Agents

Agent-to-Agent protocol — agents that talk to other agents.

| Repo | What it does | Stack | Run |
|------|-------------|-------|-----|
| [mcp-a2a-bridge](https://github.com/naveenkumarbaskaran/mcp-a2a-bridge) | Bidirectional MCP ↔ A2A bridge — the answer to "MCP vs A2A?" is *both* | Python | `pip install mcp-a2a-bridge` |
| [a2a-sap-agent](https://github.com/naveenkumarbaskaran/a2a-sap-agent) | SAP S/4HANA maintenance agent on A2A protocol — PEOS + LangGraph | Python | See README |
| [A2A-Kit](https://github.com/naveenkumarbaskaran/A2A-Kit) | Toolkit for A2A agent communication and discovery | Python | `pip install a2a-kit` |
| [agent-gateway](https://github.com/naveenkumarbaskaran/agent-gateway) | Universal gateway — route between A2A, MCP, OpenAI Assistants, REST | Python | `pip install agentic-gateway` |

---

## 🏭 SAP + Enterprise Agents

AI agents that integrate with real enterprise systems.

| Repo | What it does | Stack | Run |
|------|-------------|-------|-----|
| [ODataAgent](https://github.com/naveenkumarbaskaran/ODataAgent) | Turn any OData service into an AI-queryable tool — zero boilerplate | Python | See README |
| [PEOSGraph](https://github.com/naveenkumarbaskaran/PEOSGraph) | LangGraph implementation of PEOS architecture for enterprise automation | Python | See README |
| [AgentForge](https://github.com/naveenkumarbaskaran/AgentForge) | Production-grade enterprise agent framework — 77% token savings, zero error leaks | Python | `pip install agentforge-core` |
| [AgentGuard](https://github.com/naveenkumarbaskaran/AgentGuard) | Security guardrails — HITL write gates, error sanitization, business rules | Python | See README |
| [ABAP-MASTER](https://github.com/naveenkumarbaskaran/ABAP-MASTER) | ABAP development patterns and reusable components for SAP systems | ABAP | See README |

---

## 📚 RAG + Knowledge Agents

Agents that retrieve, reason over, and synthesize knowledge.

| Repo | What it does | Stack | Run |
|------|-------------|-------|-----|
| [NeuralHive](https://github.com/naveenkumarbaskaran/NeuralHive) | Multi-agent orchestration — supervisor, router, swarm topologies | Python | `pip install neuralhive` |
| [hive](https://github.com/naveenkumarbaskaran/hive) | 13-phase AI dev lifecycle — Scout → PRD → Architect → Code → Test → Ship | Python | `pip install hive-agents` |
| [codewise](https://github.com/naveenkumarbaskaran/codewise) | LLM-agnostic code review, security scanning, test generation | Python | `pip install codewise-ai` |
| [pr-review-ai](https://github.com/naveenkumarbaskaran/pr-review-ai) | Multi-pass LLM PR review with inline comments and architecture analysis | Python | See README |
| [conflict-resolver-ai](https://github.com/naveenkumarbaskaran/conflict-resolver-ai) | LLM-powered merge conflict resolution with confidence scoring | Python | See README |

---

## 🕸️ Multi-Agent Systems

Frameworks for coordinating fleets of agents.

| Repo | What it does | Stack | Run |
|------|-------------|-------|-----|
| [SwarmLab](https://github.com/naveenkumarbaskaran/SwarmLab) | Swarm intelligence simulation — PSO, ACO, Firefly, hybrid algorithms | Python | See README |
| [agent-diff](https://github.com/naveenkumarbaskaran/agent-diff) | PR reviewer built for AI-generated code — catches over-building, traces, drift | Python | `pip install agent-diff` |
| [pytest-agents](https://github.com/naveenkumarbaskaran/pytest-agents) | Pytest plugin for testing AI agents — mock LLMs, assert tool calls | Python | `pip install pytest-agents` |
| [PromptForge](https://github.com/naveenkumarbaskaran/PromptForge) | Enterprise prompt engineering — version control, A/B testing, analytics | Python | See README |

---

## 🛠️ LLM Tools + Infrastructure

The plumbing that makes agents production-ready.

| Repo | What it does | Stack | Run |
|------|-------------|-------|-----|
| [TokenShield](https://github.com/naveenkumarbaskaran/TokenShield) | Real-time token cost monitoring, budget enforcement, optimization | Python | `pip install tokenshield` |
| [context-budget](https://github.com/naveenkumarbaskaran/context-budget) | Drop-in context window manager — summarize, prune, archive automatically | Python | `pip install context-budget` |
| [tokmon](https://github.com/naveenkumarbaskaran/tokmon) | Lightweight LLM token and cost tracker — decorators, budgets, session tracking | Python | `pip install tokmon-ai` |
| [promptlab](https://github.com/naveenkumarbaskaran/promptlab) | Git for prompts — version, diff, A/B test your LLM prompts | Python | `pip install promptlab-ai` |
| [consync](https://github.com/naveenkumarbaskaran/consync) | Bidirectional constant sync between spreadsheets and source code | Python | `pip install consync` |
| [claude-hooks-hub](https://github.com/naveenkumarbaskaran/claude-hooks-hub) | Curated, installable hooks for Claude Code — auto-test, cost alerts, guards | JS | `npx claude-hooks-hub` |
| [minichain](https://github.com/naveenkumarbaskaran/minichain) | Minimal blockchain in C++17 — proof of work, wallets, mining | C++ | See README |

---

## 🏗️ The PEOS Architecture

Most agents in this collection follow the **PEOS pattern** — the architecture behind production SAP AI agents:

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   Planner   │───▶│  Executor   │───▶│  Observer   │───▶│ Synthesiser │
│             │    │             │    │             │    │             │
│ Break task  │    │ Call tools, │    │ Check output│    │ Merge results│
│ into steps  │    │ APIs, agents│    │ score quality│   │ write summary│
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
        ▲                                                        │
        └────────────────────────────────────────────────────────┘
                           feedback loop
```

**Why PEOS over ReAct/CoT?**
- Separates *planning* from *execution* — each phase is testable independently
- Observer catches tool errors before they cascade
- Synthesiser produces structured output every time, not "it depends on the LLM"
- 60-80% token reduction vs naive agent loops

See [PEOSGraph](https://github.com/naveenkumarbaskaran/PEOSGraph) for a runnable LangGraph implementation.

---

## 🚀 Quickstart: Pick Your Pattern

**Just want to run an agent?**
```bash
pip install hive-agents
hive "Build a REST API with rate limiting"
```

**Want to connect an SAP OData service to AI?**
```bash
pip install odata-mcp
odata-mcp serve --url https://your-sap-system/odata/v4/service
```

**Want MCP + A2A together?**
```bash
pip install mcp-a2a-bridge
mcp-a2a-bridge start --mcp-server filesystem --port 8080
```

**Want to cut LLM costs?**
```bash
pip install tokenshield context-budget
# Drop-in wrappers — no refactoring required
```

---

## Contributing

Found a great agent repo that belongs here? PRs welcome.

1. Fork this repo
2. Add your entry to the right section (table format, same columns)
3. Make sure there's a working quickstart in the linked repo
4. Open a PR

See [CONTRIBUTING.md](CONTRIBUTING.md) for full guidelines.

---

## About

Curated by [Naveen Kumar Baskaran](https://github.com/naveenkumarbaskaran) — AI Agent Engineer at SAP Labs India.
Building multi-agent systems for enterprise SAP since before it was cool.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?logo=linkedin&logoColor=white&style=flat-square)](https://linkedin.com/in/iamnaveenkumarb)
[![Portfolio](https://img.shields.io/badge/Portfolio-222222?logo=github&logoColor=white&style=flat-square)](https://naveenkumarbaskaran.github.io/)
