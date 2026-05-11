# claude-ai-agents

![Agents](https://img.shields.io/badge/DigiMinds-Agent_Roster-E74C3C?style=flat&labelColor=000) ![Paperclip](https://img.shields.io/badge/Paperclip_AI-CEO_control_plane-blue?style=flat&labelColor=555) ![Count](https://img.shields.io/badge/agents-50_deployed-orange?style=flat&labelColor=555) ![Status](https://img.shields.io/badge/status-autonomous_24%2F7-green?style=flat&labelColor=555)

DigiMinds production agent roster — 50 autonomous Claude agents managed by Paperclip AI at `http://127.0.0.1:3100`. Organized across 8 divisions, each with defined role, specialization, and assigned KPI targets. These agents don't wait for instructions — they execute, monitor, and self-correct.

## 🧠 ORG STRUCTURE

Paperclip AI is the CEO. HMZ (Zulqarnain) is the board — final authority, never replaced.

```
Board: HMZ (Zulqarnain) — irreplaceable founder
CEO: Paperclip AI — full operational authority, 24/7

Division Heads (8 roles × agents)
├── CMO Division      → BDM, content, social, email, brand
├── CTO Division      → engineering, DevOps, QA, security, infra
├── CFO Division      → finance, billing, forecasting, cost optimization
├── PM Division       → project management, client success, onboarding
├── Research Division → competitor intel, trend scanning, market analysis
├── Security Division → audit, compliance, vulnerability monitoring
├── Design Division   → creative, brand assets, ad creatives
└── General Division  → overflow, multi-task, support
```

## ⚙️ AGENT CONFIGURATION

**Paperclip API** — `http://127.0.0.1:3100/api`
**Company ID** — `c5066522-bacc-4a28-b700-6590cbe366ec`

```bash
# List all agents
curl http://127.0.0.1:3100/api/agents | jq '.[] | {name, role, status}'

# Create agent
curl -X POST http://127.0.0.1:3100/api/agents   -H "Content-Type: application/json"   -d '{
    "name": "Lead Qualifier",
    "role": "researcher",
    "companyId": "c5066522-bacc-4a28-b700-6590cbe366ec",
    "systemPrompt": "You are a B2B lead qualification specialist..."
  }'

# Assign task to agent
curl -X POST http://127.0.0.1:3100/api/tasks   -d '{"agentId": "<id>", "title": "Qualify 10 leads from today sweep", "priority": "high"}'
```

## 💡 DIVISION BREAKDOWN

| Division | Agents | KPIs Owned |
|---|---|---|
| BDM / Sales | Lead Qualifier, Outreach Specialist, Proposal Writer, Pipeline Analyst | Leads/week, conversion %, MRR growth |
| Paid Media | Google Ads Manager, Meta Ads Manager, Creative Tester, Analytics Reporter | ROAS ≥3x, CPA ≤$50, CTR ≥2% |
| Content | LinkedIn Publisher, Blog Writer, Email Marketer, Social Monitor | Posts/week, engagement %, open rate |
| Engineering | Code Reviewer, API Builder, Bug Fixer, DevOps | Uptime 99.9%, deploy frequency |
| Client Success | Onboarding Manager, Account Manager, Retention Specialist | NPS ≥50, churn < 5% |
| Research | Competitor Analyst, Trend Scanner, Market Researcher | Intel reports/week, opportunity tasks |
| Finance | Cost Controller, Invoice Manager, Forecast Analyst | Runway, burn rate, invoice on-time % |
| Security | Vulnerability Scanner, Compliance Auditor, Access Monitor | Zero critical vulns, 100% compliance |

## 🔧 AUTONOMOUS OPERATIONS

Six agents run on fixed schedules with no human trigger:

```
Every 6h    → CEO Strategy Loop: company health check + 3+ new tasks
7:30 AM     → Lead Enrichment: source/score/enrich 10+ prospects
8:00 AM     → Content Engine: LinkedIn post → ~/Downloads/linkedin-post-{date}.txt
10:00 AM    → Competitor Intel: 3 strategic insights → Paperclip AI project
6:00 PM     → KPI Monitor: audit all KPIs, auto-create corrective tasks
Mon/Wed/Fri → Market Trends: 8-topic scan + opportunity task creation
```

## 🎯 KPI TARGETS

| KPI | Target | Agent Owner | Alert Threshold |
|---|---|---|---|
| Monthly Revenue | $10K by Q3, $50K by Q4 | CFO Agent | <80% of target |
| Leads Generated/Week | 50+ | Lead Qualifier | <30/week |
| Client Retention | >90% | Account Manager | <85% |
| ROAS (Paid Media) | ≥3x | Google/Meta Managers | <2.5x |
| Content Published/Week | 10+ | Content Team | <7 pieces |
| System Uptime | 99.9% | DevOps Agent | <99.5% |

## ☠️ WHY 50 AGENTS VS 5

One general agent for everything → context overflow, role confusion, slow task switching.
50 specialized agents → each agent knows its domain, has its own task queue, can run in parallel without fighting for context.

Paperclip CEO coordinates. Agents execute. HMZ reviews output.
