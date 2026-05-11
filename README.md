# claude-ai-agents
50-agent autonomous organization operating DigiMinds agency — 8 divisions, 20 goals, 28 KPI tasks, zero daily human input required.

![agents](https://img.shields.io/badge/agents-50_deployed-blue?style=flat&labelColor=555) ![divisions](https://img.shields.io/badge/divisions-8-green?style=flat&labelColor=555) ![goals](https://img.shields.io/badge/goals-20_active-orange?style=flat&labelColor=555) ![kpis](https://img.shields.io/badge/KPIs-28_tracked-red?style=flat&labelColor=555) [![company](https://img.shields.io/badge/DigiMinds-agency-white?style=flat&labelColor=555)](https://digiminds.org)

[Concepts](#-concepts) · [Hot](#-hot) · [Org Chart](#️-organization) · [Tips](#-tips-and-tricks-22) · [Replaced](#️-startups--businesses) · [Stars](#star-history)

---

## 🧠 CONCEPTS

| Feature | Location | Description |
|---------|----------|-------------|
| [**CEO Loop Agent**](agents/ceo-loop.md) | `agents/ceo-loop.md` | Autonomous CEO running every 6h — reviews goals, re-assigns agents, logs decisions. Escalates to HMZ on critical-only |
| [**Lead Engine Agent**](agents/lead-engine.md) | `agents/lead-engine.md` | Scrapes + enriches + ICP-scores leads from LinkedIn, Apollo, Indeed — runs daily 7:30 AM |
| [**Content Engine Agent**](agents/content-engine.md) | `agents/content-engine.md` | Generates + schedules daily LinkedIn posts — trend → angle → copy → quality gate → publish |
| [**Intel Engine Agent**](agents/intel-engine.md) | `agents/intel-engine.md` | Monitors competitor ads (Meta Ad Library, Google Transparency), LinkedIn signals, Clutch reviews — daily 10 AM |
| [**KPI Monitor Agent**](agents/kpi-monitor.md) | `agents/kpi-monitor.md` | Checks 28 KPIs against thresholds every 6 PM — RED = CEO escalation, GREY = data gap alert |
| [**Trends Scanner Agent**](agents/trends-scanner.md) | `agents/trends-scanner.md` | Mon/Wed/Fri 6 AM — scans platform changes, market signals, macro trends |
| [**BDM Division (8)**](agents/bdm/) | `agents/bdm/` | Business development agents: LinkedIn outreach, Apollo sequences, job board monitoring |
| [**PPC Division (9)**](agents/ppc/) | `agents/ppc/` | Google Ads + Meta Ads campaign execution, optimization, reporting agents |
| [**Paperclip API**](https://github.com/hmzainjamil/hmz-digiminds-ceo) | `http://127.0.0.1:3100/api` | Central command: all 50 agents read/write state here. Company ID: `c5066522-bacc-4a28-b700-6590cbe366ec` |

### 🔥 Hot

| Feature | Location | Description |
|---------|----------|-------------|
| [**Agent authority matrix**](agents/authority.md) | `agents/authority.md` | Budget <$500 = agent autonomous · $500-2K = propose to HMZ · >$2K = HMZ only. Deterministic, no ambiguity |
| [**Tier 0 agent routing**](agents/routing.md) | `agents/routing.md` | All 50 agents use Groq/Gemini/DeepSeek — never Claude for agent sub-tasks. 75-95% cost savings |
| [**Agent health dashboard**](agents/health.md) | `http://127.0.0.1:3100/api/agents` | Live agent status, last run time, output quality score — real-time via Paperclip API |

---

## ⚙️ ORGANIZATION

```
HMZ (Founder / Board) — final authority
        │
        ▼
 Paperclip AI CEO (port 3100)
        │
   ┌────┴────┬───────┬───────┬───────┬───────┬───────┬────────┐
   ▼         ▼       ▼       ▼       ▼       ▼       ▼        ▼
  BDM    Content   PPC   SEO/GEO   Ops   Intel  Finance  Client
  (8)     (7)     (9)    (6)      (6)    (5)    (5)      (4)
```

| Division | Focus | Agents | Key Output |
|----------|-------|--------|------------|
| BDM | Outreach, lead gen | 8 | Qualified leads, sequences |
| Content | LinkedIn, email, blog | 7 | Daily posts, newsletters |
| PPC | Google + Meta execution | 9 | Campaign performance, ROAS |
| SEO/GEO | Organic + AI visibility | 6 | Rankings, citations |
| Operations | Systems, automation | 6 | Uptime, efficiency |
| Intelligence | Competitor, market | 5 | Intel briefs, alerts |
| Finance | Revenue, billing | 5 | MRR tracking, invoices |
| Client Success | Retention, NPS | 4 | Reports, onboarding |

---

## 💡 TIPS AND TRICKS (22)

[CEO](#tips-ceo) · [Lead](#tips-lead) · [Content](#tips-content) · [PPC](#tips-ppc) · [Ops](#tips-ops) · [Debug](#tips-debug)

<a id="tips-ceo"></a>■ **CEO Loop (5)**

| Tip | Source |
|-----|--------|
| CEO loop is the master context — all 6 engines report back to it every cycle | [Architecture](https://github.com/hmzainjamil/hmz-paperclip-ceo-loop) |
| `curl -X POST http://127.0.0.1:3100/api/ceo-loop/trigger` for on-demand CEO review | [API ref](https://github.com/hmzainjamil/hmz-digiminds-ceo) |
| Check `/api/decisions?date=today` to see what the CEO decided in the last 24h | [Transparency](https://github.com/hmzainjamil/hmz-digiminds-ceo) |
| CEO never acts on budget >$500 without HMZ approval — hardcoded authority limit | [Authority matrix](agents/authority.md) |
| CEO loop is idempotent — safe to trigger manually without risk of duplicate actions | [Design principle](https://github.com/hmzainjamil/hmz-digiminds-ceo) |

<a id="tips-lead"></a>■ **Lead Engine (5)**

| Tip | Source |
|-----|--------|
| Geo blacklist: never include India, Pakistan, Bangladesh, Philippines, Israel | [HMZ blacklist](https://github.com/hmzainjamil) |
| ICP score 80+ = hot outreach · 50-79 = nurture sequence · <50 = discard | [ICP rules](agents/lead-engine.md) |
| Companies posting PPC job roles = best DigiMinds leads — budget without execution | [Prospecting SOP](agents/lead-engine.md) |
| Deduplication by LinkedIn URL — engine never creates duplicate CRM entries | [Design](agents/lead-engine.md) |
| Apollo bulk enrich 10x faster than individual enrichment — always batch | [Apollo API](https://github.com/hmzainjamil/hmz-paperclip-lead-engine) |

<a id="tips-content"></a>■ **Content Engine (4)**

| Tip | Source |
|-----|--------|
| Hook must have a number or shocking claim — first 2 lines decide LinkedIn reach | [LinkedIn algorithm](agents/content-engine.md) |
| Rotation: Mon insight → Tue case study → Wed hot take → Thu tip → Fri story | [Content calendar](https://github.com/hmzainjamil/hmz-paperclip-content-engine) |
| Quality gate fails → post goes to draft queue, not published — safe failure mode | [Error handling](agents/content-engine.md) |
| Best publish time: 10-11 AM weekdays — engine auto-targets this | [Analytics](agents/content-engine.md) |

<a id="tips-ppc"></a>■ **PPC Division (4)**

| Tip | Source |
|-----|--------|
| PPC agents run on client Google Ads/Meta accounts — never HMZ's own accounts | [Access control](agents/ppc/) |
| All campaign changes logged to Paperclip API before execution — full audit trail | [Ops rule](agents/ppc/) |
| ROAS below 2.0 triggers automatic budget pause + HMZ alert | [Guard rails](agents/ppc/) |
| Google Ads changes batched to off-peak hours — avoids learning phase disruption | [Campaign rule](agents/ppc/) |

<a id="tips-ops"></a>■ **Ops (2)**

| Tip | Source |
|-----|--------|
| `launchctl list \| grep paperclip` — verify Paperclip CEO is running every session | [Startup check](automations/) |
| All agent logs at `~/Library/Logs/paperclip-*.log` — tail for live monitoring | [Log location](automations/) |

<a id="tips-debug"></a>■ **Debug (2)**

| Tip | Source |
|-----|--------|
| API 503 = Paperclip not running → `launchctl start ai.hmz.paperclip` | [Runbook](https://github.com/hmzainjamil/hmz-digiminds-ceo) |
| Agent count mismatch → refresh `/api/agents` — CEO may have reassigned roles | [API ref](https://github.com/hmzainjamil/hmz-digiminds-ceo) |

---

## ☠️ STARTUPS / BUSINESSES

| Feature | Replaced |
|-|-|
| **50-agent autonomous org** | [Devin](https://devin.ai), [SWE-agent](https://swe-agent.com), [AutoGPT](https://autogpt.net) — single-agent, not org-scale |
| **CEO autonomous decision loop** | Hiring a human COO/CEO ($150K+/yr) + Trello/Asana manual boards |
| **Lead engine (daily 7:30 AM)** | Manual LinkedIn prospecting (2h/day), [Apollo](https://apollo.io) manual searches |
| **Content engine (daily 8 AM)** | [Buffer](https://buffer.com), [Hootsuite](https://hootsuite.com) — scheduling only, no generation |
| **Competitor intel (daily 10 AM)** | Manual ad library checks, [Similarweb](https://similarweb.com) manual reports |
| **KPI monitor (daily 6 PM)** | Google Sheets dashboards, [Databox](https://databox.com) — passive, no escalation |
| **Authority matrix** | Unstructured "ask HMZ about everything" — bottleneck |

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/claude-ai-agents&type=Date)](https://star-history.com/#hmzainjamil/claude-ai-agents&Date)