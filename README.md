# claude-ai-agents
50 specialized AI agents. one company. zero human operators.

![Paperclip AI](https://img.shields.io/badge/Paperclip_AI-CEO_Control_Plane-E74C3C?style=flat&labelColor=000) ![Agents](https://img.shields.io/badge/agents-50_deployed-blue?style=flat&labelColor=555) ![Divisions](https://img.shields.io/badge/divisions-8-orange?style=flat&labelColor=555) ![API](https://img.shields.io/badge/API-127.0.0.1%3A3100-green?style=flat&labelColor=555) ![Status](https://img.shields.io/badge/status-autonomous_24%2F7-brightgreen?style=flat&labelColor=555)

DigiMinds production agent roster — 50 autonomous Claude agents managed by Paperclip AI at `http://127.0.0.1:3100`. Organized across 8 divisions. Each agent has a defined role, KPI ownership, task queue, and system prompt. They don't wait for instructions — they execute, monitor, and self-correct.

[Org Structure](#org) · [Agent Roster](#roster) · [API Reference](#api) · [Autonomous Loops](#loops) · [KPIs](#kpis) · [Tips](#tips) · [Gotchas](#gotchas)

## 🧠 COMPANY STRUCTURE

```
Board: HMZ (Zulqarnain) — irreplaceable founder, final authority
CEO:   Paperclip AI     — full operational control, 24/7 autonomous

8 Divisions (50 agents total):
├── BDM / Sales (6)      ← lead gen, outreach, proposals, pipeline
├── Paid Media (6)       ← Google Ads, Meta Ads, creative, analytics
├── Content (6)          ← LinkedIn, blog, email, social, brand
├── Engineering (7)      ← code review, API, DevOps, QA, security, infra
├── Client Success (6)   ← onboarding, account mgmt, retention, NPS
├── Research (5)         ← competitor intel, trends, market analysis
├── Finance (7)          ← billing, forecasting, cost control, runway
└── Security (7)         ← vuln scanning, compliance, access control
```

**Company:** DigiMinds | digiminds.org | ID: `c5066522-bacc-4a28-b700-6590cbe366ec`

<a id="org"></a>
## ⚙️ DIVISION BREAKDOWN

■ **BDM / Sales Division (6 agents)**

| Agent | Role | KPIs Owned |
|---|---|---|
| Lead Qualifier | researcher | 50+ leads/week, quality score ≥70 |
| Outreach Specialist | general | Reply rate ≥8%, open rate ≥35% |
| Proposal Writer | general | Proposals/week ≥5, win rate ≥25% |
| Pipeline Analyst | researcher | Pipeline velocity, deal stage tracking |
| BDM Orchestrator | cmo | Division coordination, weekly targets |
| LinkedIn Prospector | researcher | LinkedIn outreach volume, connections |

■ **Paid Media Division (6 agents)**

| Agent | Role | KPIs Owned |
|---|---|---|
| Google Ads Manager | researcher | ROAS ≥3x, CPA ≤$50, CTR ≥3% |
| Meta Ads Manager | researcher | ROAS ≥2.5x, CPM trends, frequency |
| Creative Tester | designer | A/B test velocity, winner rate |
| Analytics Reporter | researcher | Weekly performance reports, anomaly detection |
| Campaign Orchestrator | cmo | Budget allocation across platforms |
| Landing Page Optimizer | researcher | Conversion rate ≥3%, CRO tests |

■ **Content Division (6 agents)**

| Agent | Role | KPIs Owned |
|---|---|---|
| LinkedIn Publisher | general | 5+ posts/week, engagement ≥3% |
| Blog Writer | general | 2+ articles/week, SEO targeting |
| Email Marketer | general | Open rate ≥35%, click rate ≥5% |
| Social Monitor | researcher | Brand mention tracking, sentiment |
| Brand Guardian | designer | Brand consistency audits |
| Content Strategist | cmo | Editorial calendar, content mix |

■ **Engineering Division (7 agents)**

| Agent | Role | KPIs Owned |
|---|---|---|
| Code Reviewer | engineer | PR review time ≤2h, bug catch rate |
| API Builder | engineer | Endpoint delivery time, uptime |
| Bug Fixer | engineer | Bug resolution time ≤24h |
| DevOps Engineer | devops | Deploy frequency, incident rate |
| QA Specialist | qa | Test coverage ≥80%, regression rate |
| Security Auditor | security | Zero critical vulns |
| Infrastructure Manager | devops | Uptime 99.9%, cost optimization |

<a id="roster"></a>
## 💡 AGENT CONFIGURATION

**Valid roles in Paperclip API:**
`ceo, cto, cmo, cfo, security, engineer, designer, pm, qa, devops, researcher, general`

**Create an agent:**
```bash
curl -X POST http://127.0.0.1:3100/api/agents   -H "Content-Type: application/json"   -d '{
    "name": "Lead Qualifier Alpha",
    "role": "researcher",
    "companyId": "c5066522-bacc-4a28-b700-6590cbe366ec",
    "systemPrompt": "You are a B2B lead qualification specialist for DigiMinds. Score leads 0-100 based on: budget ($2K+/mo = 30pts), decision-maker (20pts), timing (now = 20pts), fit (agency client = 30pts). Return JSON: {score, tier, next_action}"
  }'
```

**Assign a task:**
```bash
curl -X POST http://127.0.0.1:3100/api/tasks   -H "Content-Type: application/json"   -d '{
    "title": "Qualify 10 leads from today LinkedIn sweep",
    "agentId": "<agent-id>",
    "projectId": "e6f971fb-6009-4b14-8d28-853272857c6a",
    "priority": "high",
    "dueDate": "2026-05-12T23:59:00Z"
  }'
```

<a id="api"></a>
## 🔧 API REFERENCE

**Base:** `http://127.0.0.1:3100/api`
**Company ID:** `c5066522-bacc-4a28-b700-6590cbe366ec`

| Endpoint | Method | Purpose |
|---|---|---|
| `/agents` | GET | List all agents |
| `/agents` | POST | Create agent |
| `/agents/:id` | PATCH | Update agent |
| `/tasks` | GET | List tasks (filter by project/agent) |
| `/tasks` | POST | Create task |
| `/tasks/:id` | PATCH | Update task status |
| `/projects` | GET | List all projects/divisions |
| `/goals` | GET | List strategic goals |
| `/goals` | POST | Create goal |
| `/health` | GET | API health check |

**Project IDs (division mapping):**
```
BDM:            e6f971fb-6009-4b14-8d28-853272857c6a
Paid Media:     262613c4-9105-4b16-9bae-8097207c1e41
Onboarding:     096aa167-076e-4ef1-866b-640d5a169ebe
Content:        8b8cf04f-ec26-440c-92b8-097ab62526ce
Reporting:      3ca9a91e-e433-4e0e-9ee1-b8768b937ab4
AI Automation:  5aebdbec-ef89-48f6-a4f2-b89435256a67
Finance:        febd0b11-df76-4771-9ef8-b9c6ef880da1
Security:       babe0ef1-1dd6-4a10-ae0a-8fc5fa48a632
```

<a id="loops"></a>
## 🔄 AUTONOMOUS SCHEDULED AGENTS

Six agents run without human trigger — every day, all day:

| Agent | Schedule | Output Location |
|---|---|---|
| CEO Strategy Loop | Every 6h | 3+ tasks/run · `~/.paperclip/ceo-decisions.log` |
| Lead Enrichment Engine | 7:30 AM daily | 10+ leads · `~/Downloads/outreach-{date}.txt` |
| LinkedIn Content Engine | 8:00 AM daily | Post draft · `~/Downloads/linkedin-post-{date}.txt` |
| Competitor Intel Engine | 10:00 AM daily | 3 insights → Paperclip AI project |
| KPI Health Monitor | 6:00 PM daily | Corrective tasks · `~/Downloads/paperclip-daily-summary-{date}.txt` |
| Market Trends Scanner | Mon/Wed/Fri 6AM | 8 trend signals + opportunity tasks |

All scheduled via `mcp__scheduled-tasks__create_scheduled_task` — run on Anthropic infrastructure even when machine is off.

<a id="kpis"></a>
## 📊 KPI DASHBOARD

| KPI | Target | Alert Threshold | Owner |
|---|---|---|---|
| Monthly Revenue | $10K (Q3) → $50K (Q4) | <80% of target | CFO Agent |
| Leads/Week | 50+ | <30 | Lead Qualifier |
| Client Retention | >90% | <85% | Account Manager |
| ROAS (Google) | ≥3x | <2.5x | Google Ads Manager |
| ROAS (Meta) | ≥2.5x | <2x | Meta Ads Manager |
| Content/Week | 10+ pieces | <7 | Content Strategist |
| Uptime | 99.9% | <99.5% | DevOps Agent |
| NPS | ≥50 | <40 | Account Manager |
| Invoice On-Time | 100% | <95% | Finance Agent |
| Bug Resolution Time | ≤24h | >48h | Bug Fixer |

<a id="tips"></a>
## 🧠 TIPS

■ **Agent Design (5)**

| Tip | Note |
|---|---|
| Keep system prompts under 500 tokens per agent — longer prompts dilute instruction following | Quality degrades above 1K tokens |
| Give each agent a specific output format requirement — `return JSON: {field: value}` — avoids parsing failures | Structured output is more reliable |
| One agent per KPI — don't give one agent 5 KPIs to track, split into 5 agents | Specialization > generality |
| Add a `[DAILY LIMIT]` marker in system prompt for agents that shouldn't loop infinitely | Prevents runaway task creation |
| Name agents with their specific scope: "Google Ads Campaign Builder" not "Ads Agent" | Specificity improves task routing |

■ **Task Design (5)**

| Tip | Note |
|---|---|
| Always include `projectId` in task creation — orphaned tasks (no project) never show in dashboards | |
| Use `priority: "high"` sparingly — if everything is high, nothing is | Max 20% of tasks should be high |
| Include a `dueDate` even for non-urgent tasks — undated tasks get deprioritized in Paperclip | |
| Add data sources in task description: "pull from GA4 dashboard, compare to last 30d" | Agents execute faster with explicit sources |
| Create a "Definition of Done" field in complex tasks — agents close tasks early without it | |

<a id="gotchas"></a>
## ☠️ GOTCHAS

| Gotcha | Fix |
|---|---|
| `reportsTo` field returns 404 on PATCH — org hierarchy not settable via API | Set org hierarchy in Paperclip UI only |
| Agents don't have memory between task executions — each task starts fresh | Pass context in task description, not via agent state |
| Paperclip API returns 413 if task description > ~10KB | Summarize long context before including in task |
| CEO Loop creates duplicate tasks if run twice in same session | Add existence check before task creation |
| Scheduled agents timeout after 5min — complex research tasks fail | Break long tasks into sub-tasks in task description |
