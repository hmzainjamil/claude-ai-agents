# claude-ai-agents
HMZ's production agent roster — autonomous Claude agents for marketing, lead gen, and agency ops

![DigiMinds](https://img.shields.io/badge/DigiMinds-Agency_OS-6C3EE8?style=flat&labelColor=000) ![Claude](https://img.shields.io/badge/Claude-Sonnet_4.6-orange?style=flat&labelColor=555) ![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat&labelColor=555) ![Agents](https://img.shields.io/badge/agents-50%2B-blue?style=flat&labelColor=555)

Part of the [HMZ AI Infrastructure](https://github.com/hmzainjamil) stack — the agent layer powering DigiMinds (digiminds.org) autonomously.

---

## 🧠 ARCHITECTURE

| Layer | Component | Role |
|-------|-----------|------|
| Orchestration | Paperclip AI CEO | Routes tasks, monitors KPIs, self-improves every 6h |
| Execution | Scheduled Agents | Lead gen, content, intel, KPI monitor — 24/7 |
| Memory | `~/.claude/projects/memory/` | Cross-session persistence |
| Tools | MCP Servers + Skills | Apollo, Vibe Prospecting, Apify, Gmail, Notion |
| Infrastructure | LaunchAgent `ai.hmz.paperclip` | Always-on, auto-restarts |

## ⚙️ AGENT ROSTER

| Division | Agents | Specialization |
|----------|--------|----------------|
| C-Suite | CFO, CMO, CTO, CSO | P&L, brand, tech stack, security |
| Engineering | 6 agents | Full-stack, AI/ML, backend, frontend, DevOps x2 |
| Marketing | 6 agents | Creative director, performance creative, SEO, content, copywriter |
| Sales/BDM | 4 agents | BDM lead, AE, lead researcher, partnership manager |
| Client Services | 4 agents | PM x2, QA lead, campaign QA |
| Paid Media | 4 agents | Google Ads, Meta Ads, programmatic, analytics |
| Operations | 4 agents | Ops manager, finance ops, legal, HR |
| AI R&D | 4 agents | AI research, prompt engineer, MCP engineer, competitive intel |
| Growth | 4 agents | Growth hacker, email, paid social, community |

## 💡 AUTONOMOUS LOOPS

■ **Scheduled Tasks (6 always-running)**

| Task ID | Schedule | What it does |
|---------|----------|--------------|
| `paperclip-ceo-autonomous-loop` | Every 6h | Web intel → create tasks → hire new agents if skill gap |
| `paperclip-lead-enrichment-engine` | 7:30 AM daily | 10+ leads sourced, scored, enriched → outreach drafted |
| `paperclip-linkedin-content-engine` | 8:00 AM daily | 1 trending post generated → saved to ~/Downloads |
| `paperclip-competitor-intel-engine` | 10:00 AM daily | Competitor pricing, positioning, gaps logged |
| `paperclip-kpi-health-monitor` | 6:00 PM daily | KPI audit → corrective tasks for any miss |
| `paperclip-market-trends-scanner` | 6 AM Mon/Wed/Fri | Global AI + marketing trends → opportunity tasks |

## ☠️ WHAT THIS REPLACES

| Manual Task | Agent |
|-------------|-------|
| Daily lead research | `paperclip-lead-enrichment-engine` |
| LinkedIn content | `paperclip-linkedin-content-engine` |
| Competitor monitoring | `paperclip-competitor-intel-engine` |
| KPI tracking | `paperclip-kpi-health-monitor` |
| Market research | `paperclip-market-trends-scanner` |

---
Built by [HMZ](https://github.com/hmzainjamil) · [DigiMinds](https://digiminds.org) · Operated by Paperclip AI CEO
