<p align="center">
  <img src="https://img.shields.io/badge/HMZ-AI%20AGENTS-20A34E?style=for-the-badge&logoColor=white" alt="HMZ AI Agents" height="60">
</p>

<h1 align="center">Claude AI Agents</h1>

<p align="center">
  <strong>210 production-grade specialist AI agents across 15 divisions — drop into Claude Code, Cursor, or any MCP-compatible IDE</strong>
</p>

<p align="center">
  <a href="https://github.com/hmzainjamil"><img src="https://img.shields.io/badge/By-HMZ-6C3EE8?style=for-the-badge" alt="By HMZ"></a>
  <a href="#divisions"><img src="https://img.shields.io/badge/Agents-210-20A34E?style=for-the-badge" alt="210 Agents"></a>
  <a href="#divisions"><img src="https://img.shields.io/badge/Divisions-15-246DFF?style=for-the-badge" alt="15 Divisions"></a>
  <a href="#"><img src="https://img.shields.io/badge/Claude%20Code-Native-15C1E6?style=for-the-badge" alt="Claude Code Native"></a>
  <a href="https://github.com/hmzainjamil/claude-ai-agents/stargazers"><img src="https://img.shields.io/github/stars/hmzainjamil/claude-ai-agents?style=for-the-badge&color=9D97F4&label=Stars" alt="Stars"></a>
</p>

<p align="center">
  <a href="#overview">Overview</a> &bull;
  <a href="#quick-start">Quick Start</a> &bull;
  <a href="#divisions">Divisions</a> &bull;
  <a href="#use-cases">Use Cases</a> &bull;
  <a href="#installation">Installation</a> &bull;
  <a href="#resources">Resources</a>
</p>

---

## Overview

**Claude AI Agents** is a collection of 210 specialist AI agents, each with deep domain expertise, calibrated personas, and pre-built toolchain integrations. Drop them into Claude Code and get instant access to an elite team — engineers, strategists, media buyers, designers, lawyers, and more.

Every agent is:
- **Task-specific** — focused on one domain, not a generalist
- **Tool-aware** — knows which MCP tools, APIs, and commands to use for its domain
- **Prompt-optimized** — calibrated instructions that elicit the best model output
- **Production-ready** — battle-tested across 100s of real client and agency tasks

---

## Quick Start

```bash
# In Claude Code — activate any agent
"Activate Paid Media Specialist"
"I need the DevOps Automator"
"Switch to Deal Strategist mode"

# Fire all 210 simultaneously
/all-agents

# Route by detected intent (auto — no command needed)
# Say: "audit my Meta ads" → Paid Media Specialist auto-activates
# Say: "write cold email sequence" → Email Intelligence Engineer auto-activates
# Say: "build REST API" → Backend Architect auto-activates
```

---

## Divisions

### Engineering (29 agents)
| Agent | Core capability |
|---|---|
| Backend Architect | System design, database architecture, API development, microservices |
| DevOps Automator | CI/CD pipelines, infrastructure automation, cloud operations |
| Security Engineer | Threat modeling, secure code review, vulnerability assessment |
| SRE | SLOs, error budgets, observability, chaos engineering |
| Frontend Developer | React/Vue/Angular, UI implementation, performance optimization |
| AI Engineer | ML model deployment, AI feature integration, data pipelines |
| Data Engineer | ETL/ELT, Spark, dbt, streaming, lakehouse architectures |
| Database Optimizer | Schema design, query optimization, PostgreSQL/MySQL tuning |
| +21 more | Mobile, Embedded, Blockchain, Smart Contracts, LSP, Terminal, XR... |

### Marketing (30 agents)
| Agent | Core capability |
|---|---|
| SEO Specialist | Technical SEO, content optimization, link building, organic growth |
| Content Creator | Multi-platform campaigns, editorial calendars, brand storytelling |
| Social Media Strategist | LinkedIn, Twitter, cross-platform campaigns, community building |
| Email Intelligence Engineer | Structured email extraction, automation systems |
| Growth Hacker | Viral loops, conversion funnels, rapid user acquisition |
| +25 more | Brand Guardian, Visual Storyteller, Video Specialist, Reddit, TikTok... |

### Paid Media (7 agents)
| Agent | Core capability |
|---|---|
| PPC Campaign Strategist | Google/Microsoft/Amazon, $10K–$10M+ monthly spend |
| Paid Social Strategist | Meta, LinkedIn, TikTok, Pinterest — full-funnel |
| Ad Creative Strategist | RSA copy, asset groups, creative testing frameworks |
| Paid Media Auditor | 200+ checkpoint audit across Google, Meta, Microsoft |
| Search Query Analyst | Negative keyword architecture, query-to-intent mapping |
| Programmatic & Display Buyer | DV360, trade desk, ABM display (Demandbase, 6Sense) |
| Tracking & Measurement | GTM, GA4, Meta CAPI, server-side, attribution modeling |

### Sales (8 agents)
| Agent | Core capability |
|---|---|
| Deal Strategist | MEDDPICC qualification, win planning, competitive positioning |
| Sales Coach | Rep development, pipeline review, call coaching, forecast accuracy |
| Outbound Strategist | Signal-based prospecting, ICP definition, multi-channel sequences |
| Account Strategist | Land-and-expand, QBR facilitation, net revenue retention |
| Discovery Coach | Question design, current-state mapping, gap quantification |
| Pipeline Analyst | Pipeline health, deal velocity, forecast accuracy |
| Sales Engineer | Technical discovery, demo engineering, POC scoping |
| Proposal Strategist | Win narratives, executive summaries, competitive positioning |

### + 11 more divisions
Finance · Legal · Design · Product · Strategy · Support · Testing · Academic · Spatial Computing · Game Dev · Project Management

---

## Use Cases

| Goal | Agent | Example prompt |
|---|---|---|
| **Full paid media audit** | Paid Media Auditor | "Audit my Google Ads — structure, quality scores, wasted spend, auction insights" |
| **Cold email sequence** | Email Intelligence Engineer | "Write 7-email cold sequence for digital agency services targeting e-com brands" |
| **Build a data pipeline** | Data Engineer | "Build ETL from Shopify → BigQuery → dbt → Looker for daily revenue reporting" |
| **Security audit** | Security Engineer | "Threat model this API — OWASP top 10, auth flaws, injection risks" |
| **Win a deal** | Deal Strategist | "Score this opportunity via MEDDPICC and build a 90-day win plan" |
| **Launch a product** | Chief of Staff + Product Manager | "Build full GTM plan — ICP, messaging, channels, launch calendar, KPIs" |
| **Scrape competitor data** | Data Engineer + SEO Specialist | "Pull competitor backlinks, traffic estimates, and top-ranking pages into Airtable" |
| **Write a legal NDA** | Legal Compliance Checker | "Draft a mutual NDA for a SaaS partnership — UK law, 2-year term" |

---

## Installation

### Claude Code

```bash
# Reference the agents directory
git clone https://github.com/hmzainjamil/claude-ai-agents.git ~/.claude/agents

# Or install via plugin
/plugin marketplace add https://github.com/hmzainjamil/claude-ai-agents
```

### Direct use in any MCP-compatible IDE

Point your agent system at the `agents/` directory. Each agent is a `.md` file with:
- Persona and expertise definition
- Tool and MCP integration instructions
- Output format requirements
- Domain-specific constraints

---

## Resources

- **[claude-ai-system](https://github.com/hmzainjamil/claude-ai-system)** — Full HMZ system (skills + agents + workflows)
- **[claude-ai-skills](https://github.com/hmzainjamil/claude-ai-skills)** — 45+ skills that power these agents
- **[hmz-n8n-workflows](https://github.com/hmzainjamil/hmz-n8n-workflows)** — 8,000+ automation workflows
- **[hmz-claude-code-best-practice](https://github.com/hmzainjamil/hmz-claude-code-best-practice)** — Claude Code patterns

---

## Support

- [Open an issue](https://github.com/hmzainjamil/claude-ai-agents/issues)
- [LinkedIn](https://linkedin.com/in/hmzainjamil)

## License

MIT

---

<p align="center">
  Built by <a href="https://github.com/hmzainjamil">Hafiz Muhammad Zulqarnain</a> &mdash; HMZ AI Agency
</p>