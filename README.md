# claude-ai-agents

![v](https://img.shields.io/badge/version-2.0-blue?style=flat&labelColor=555) ![s](https://img.shields.io/badge/status-active-brightgreen?style=flat&labelColor=555) ![l](https://img.shields.io/badge/license-MIT-orange?style=flat&labelColor=555)

> 210 specialist AI agents across 15 divisions — Engineering, Marketing, Sales, Finance, Legal, Design, Product, Support, Game Dev, Spatial Computing, and more. Tier 0 routing, zero Claude tokens for sub-tasks.

---

## 🧠 CONCEPTS

| Feature | Location | Description |
|---|---|---|
| [Agent Registry](agents/registry.json) | `agents/registry.json` | JSON manifest of all 210 agents — name, division, model, trigger keywords |
| [Engineering Division](agents/engineering/) | `agents/engineering/` | 29 agents: backend, frontend, DevOps, security, SRE, data engineering, embedded |
| [Marketing Division](agents/marketing/) | `agents/marketing/` | 30 agents: SEO, PPC, content, social, email, brand, growth, influencer |
| [Sales Division](agents/sales/) | `agents/sales/` | 8 agents: SDR, AE, sales engineer, deal strategist, RevOps, pipeline analyst |
| [Finance Division](agents/finance/) | `agents/finance/` | 5 agents: FP&A, bookkeeper, tax strategist, investment researcher, controller |
| [Legal Division](agents/legal/) | `agents/legal/` | 6 agents: contract review, compliance, IP, billing, intake, doc review |
| [Strategy Division](agents/strategy/) | `agents/strategy/` | 6 agents: GTM, product, brand guardian, chief of staff, exec summary, trend |
| [Product Division](agents/product/) | `agents/product/` | 5 agents: PM, sprint prioritizer, feedback synthesizer, experiment tracker, UX |
| [Design Division](agents/design/) | `agents/design/` | 8 agents: UI, UX researcher, visual storyteller, motion, inclusive visuals, brand |
| [Support Division](agents/support/) | `agents/support/` | 6 agents: customer service, healthcare, retail returns, loan officer, hospitality |
| [Game Dev Division](agents/gamedev/) | `agents/gamedev/` | 10 agents: game designer, narrative, level, audio, Unity, Unreal, Godot, Roblox |
| [Spatial Computing](agents/spatial/) | `agents/spatial/` | 6 agents: XR developer, visionOS, WebXR interface architect |
| [Paid Media Division](agents/paidmedia/) | `agents/paidmedia/` | 7 agents: PPC, programmatic, paid social, search query, ad creative, ASO |
| [Testing Division](agents/testing/) | `agents/testing/` | 8 agents: QA, API tester, accessibility, performance benchmarker, model QA |
| [Specialized Division](agents/specialized/) | `agents/specialized/` | 41 agents: psychologist, anthropologist, historian, geographer, narratologist |
| [MAE Bridge](agents/mae-bridge.sh) | `agents/mae-bridge.sh` | Routes any mae run goal to the correct specialist agent automatically |
| [Keyword Routing](agents/routing.json) | `agents/routing.json` | Keyword → agent → model mapping — auto-loaded by skill-router on every prompt |
| [Model Rules](agents/model-rules.md) | `agents/model-rules.md` | Which model each agent uses: Groq/Gemini/DeepSeek/Ollama — never Claude |
| [Division Mode](agents/division.sh) | `agents/division.sh` | Single command activates full specialist division for complex domain tasks |
| [Agent Blast](agents/blast.sh) | `agents/blast.sh` | Fire ALL 210 agents on one goal — synthesizes best result |
| [Output Synthesis](agents/synthesize.py) | `agents/synthesize.py` | Groq-70B synthesizer merges all agent outputs into one production result |
| [Paperclip Sync](agents/paperclip-sync.sh) | `agents/paperclip-sync.sh` | Auto-saves every agent run to Paperclip AI — zero-human company memory |
| [Health Monitor](agents/health.sh) | `agents/health.sh` | Pings all 210 agents — verifies each model is live and responding |
| [Custom Agent Builder](agents/builder.py) | `agents/builder.py` | Scaffold a new specialist agent from template in under 60 seconds |
| [Session Memory](agents/session-mem.py) | `agents/session-mem.py` | Per-session memory so agents retain context across 12-step workflows |

### 🔥 Hot

| Feature | Location | Description |
|---|---|---|
| [MAE 12-Agent Swarm](agents/mae-bridge.sh) | `agents/mae-bridge.sh` | 12 agents fire in parallel, Groq-70B synthesizes result in ~8 seconds |
| [All-Agents Blast](agents/blast.sh) | `agents/blast.sh` | All 210 agents on one goal — maximum intelligence, maximum synthesis |
| [Tier 0 Routing](agents/model-rules.md) | `agents/model-rules.md` | Every sub-task → Groq/Gemini/DeepSeek → 0 Claude tokens consumed |
| [Keyword Auto-Detect](agents/routing.json) | `agents/routing.json` | Prompt scanned on every UserPromptSubmit → correct agent auto-activated |
| [Division Mode](agents/division.sh) | `agents/division.sh` | One command activates full specialist division for complex domain tasks |

---

## ⚙️ ARCHITECTURE

```
┌─────────────────────────────────────────────────────────────────┐
│                CLAUDE-AI-AGENTS v2.0                           │
│                                                                 │
│  User Prompt → skill-router → keyword match → agent activated  │
│                       │                                         │
│       ┌───────────────▼────────────────┐                       │
│       │        MAE ORCHESTRATOR        │                       │
│       │  Phase 1: Groq decomposes goal │                       │
│       │  Phase 2: 12 specialist agents │                       │
│       │  Phase 3: cross-LLM blast      │                       │
│       │  Phase 4: Groq-70B synthesizes │                       │
│       └────────────────────────────────┘                       │
│                       │                                         │
│  ┌──────────┬─────────┬─────────┬─────────┬──────────┐        │
│  │Engineer  │Marketing│  Sales  │ Finance │  Legal   │        │
│  │ 29 agents│30 agents│ 8 agents│ 5 agents│ 6 agents │        │
│  └──────────┴─────────┴─────────┴─────────┴──────────┘        │
└─────────────────────────────────────────────────────────────────┘
```

| Layer | Technology | Purpose |
|---|---|---|
| Orchestration | MAE + TCC | Decompose → swarm → synthesize any goal |
| Model Layer | Groq / Gemini / DeepSeek | Tier 0 — zero Claude tokens for sub-tasks |
| Memory | Paperclip AI + tcc-logs/ | Persistent cross-session agent memory |
| Routing | skill-router + routing.json | Keyword → agent auto-activation |

---

## 🚀 Quick Start

```bash
# Fire 12-agent swarm on any goal
mae run "write a cold email sequence for B2B SaaS"

# Activate full marketing division
~/.claude/agents/division.sh marketing "audit our Google Ads account"

# Blast all 210 agents on one goal
~/.claude/agents/blast.sh "what is our best GTM strategy for Q3"

# Check agent health
~/.claude/agents/health.sh

# Build a custom agent in 60 seconds
~/.claude/agents/builder.py --name "fintech-analyst" --division finance --model groq
```

---

## 💡 TIPS AND TRICKS (72)

<a id="tips-mae_orchestration_6"></a>
### ■ **MAE Orchestration (6)**
| Tip | Source |
|---|---|
| mae run 'goal' = 12-agent swarm + synthesis in ~8 seconds — default | [MAE](https://github.com/hmzainjamil/claude-ai-system) |
| tcc blast 't1' 't2' = parallel fire multiple tasks — 8x faster than sequential | [TCC](https://github.com/hmzainjamil/claude-ai-system) |
| mae daily = full DigiMinds agency operations automated in one command | [MAE](https://github.com/hmzainjamil/claude-ai-system) |
| tcc fire all = execute entire pending queue in parallel wave batches | [TCC](https://github.com/hmzainjamil/claude-ai-system) |
| tcc-dashboard = full system status: queue, RAM, model health, last run | [tcc-dashboard](https://github.com/hmzainjamil/claude-ai-system) |
| All MAE outputs auto-saved to ~/.claude/tcc-logs/ as timestamped Markdown | [tcc-logs](https://github.com/hmzainjamil/claude-ai-system) |

<a id="tips-model_routing_6"></a>
### ■ **Model Routing (6)**
| Tip | Source |
|---|---|
| Always Tier 0 first — Ollama→Groq→Gemini→Bytez→OpenRouter→DeepSeek→Claude | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| Groq llama3-70b: sub-500ms, best for synthesis and analysis tasks | [Groq](https://console.groq.com) |
| Gemini 2.0 Flash: free, 1M context — use for long document analysis | [Google AI](https://ai.google.dev) |
| DeepSeek-V3 via OpenRouter: best free code model, beats GPT-4o on code | [OpenRouter](https://openrouter.ai) |
| Bytez API: 100+ free models — cb4a7065a586ec6ca26394724ce5ec49 | [Bytez](https://bytez.com) |
| caveman compression: 60-80% token savings on every response automatically | [caveman](https://github.com/hmzainjamil/claude-ai-skills) |

<a id="tips-token_savings_6"></a>
### ■ **Token Savings (6)**
| Tip | Source |
|---|---|
| 75-95% Claude token savings via Tier 0 routing — enforced on every task | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| Never re-read files already in context — agent state persists per session | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| Batch all parallel tasks in one tcc blast — fewer round-trips = fewer tokens | [TCC](https://github.com/hmzainjamil/claude-ai-system) |
| Use --jq on GH API calls — returns only the field needed, not full JSON | [gh CLI](https://cli.github.com) |
| Wave batching: cloud APIs first, Ollama last (if RAM > 2GB free) | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| Skip verification steps on internal code — trust framework guarantees | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |

<a id="tips-memory_6"></a>
### ■ **Memory (6)**
| Tip | Source |
|---|---|
| ~/.claude/projects/ MEMORY.md index loads every session — full context | [MEMORY.md](https://github.com/hmzainjamil/claude-ai-system) |
| Paperclip AI ingests all outputs — searchable company OS across sessions | [Paperclip](https://paperclip.ai) |
| Auto-learn hook writes learnings to session-queue.jsonl on every prompt | [auto-learn](https://github.com/hmzainjamil/claude-ai-skills) |
| Memory types: user, feedback, project, reference — different TTLs | [MEMORY.md](https://github.com/hmzainjamil/claude-ai-system) |
| Never save code patterns to memory — read code directly every session | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| Stale memories: verify before acting — git log / grep for current state | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |

<a id="tips-hooks_6"></a>
### ■ **Hooks (6)**
| Tip | Source |
|---|---|
| UserPromptSubmit → skill-auto-activate → keyword scan → correct skill loaded | [hooks](https://github.com/hmzainjamil/claude-ai-system) |
| PostToolUse Write/Edit → auto-github-push → bin/ and skills/ auto-synced | [hooks](https://github.com/hmzainjamil/claude-ai-system) |
| Stop hook → session-queue.jsonl → memory files updated for next session | [hooks](https://github.com/hmzainjamil/claude-ai-system) |
| compact-guard hook fires before context overflow — prevents wasteful re-runs | [compact-guard](https://github.com/hmzainjamil/claude-ai-skills) |
| All hooks run async < 200ms — never block the main conversation thread | [settings.json](https://github.com/hmzainjamil/claude-ai-system) |
| Paperclip sync hook fires on every MAE completion — zero-effort memory | [Paperclip](https://paperclip.ai) |

<a id="tips-skills_6"></a>
### ■ **Skills (6)**
| Tip | Source |
|---|---|
| Core 10 skills always active — never deactivate caveman/compact-guard/etc | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| skill-auto-activate runs on every prompt — correct skill auto-loaded | [skill-router](https://github.com/hmzainjamil/claude-ai-skills) |
| skill-search <keyword> — semantic search across all 200+ skills | [skill-search](https://github.com/hmzainjamil/claude-ai-skills) |
| skill-on/skill-off toggle — moves between active and skills-archive/ | [skill-on](https://github.com/hmzainjamil/claude-ai-skills) |
| Always deactivate non-core skills after task — collapse back to baseline | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| skills-lock.json: blockchain manifest — dep tracking, version hashes | [skills-lock](https://github.com/hmzainjamil/claude-ai-skills) |

<a id="tips-launchagents_6"></a>
### ■ **LaunchAgents (6)**
| Tip | Source |
|---|---|
| KeepAlive=true + RunAtLoad=true = always-on service that survives reboots | [launchd](https://developer.apple.com) |
| Set HOME + PATH in EnvironmentVariables — scripts find all tools | [launchd](https://developer.apple.com) |
| Log stdout/stderr to /tmp/ — check if LaunchAgent crashes silently | [launchd](https://developer.apple.com) |
| Reload: launchctl unload then load — applies plist config changes | [launchd](https://developer.apple.com) |
| ThrottleInterval=10 — prevents restart loop on persistent crash | [launchd](https://developer.apple.com) |
| launchctl list | grep ai.hmz — verify all services are running | [launchd](https://developer.apple.com) |

<a id="tips-opencli_6"></a>
### ■ **OpenCLI (6)**
| Tip | Source |
|---|---|
| v1.7.18 installed: /Users/mc/.nvm/versions/node/v24.14.1/bin/opencli | [npm](https://npmjs.com) |
| 90+ site adapters — GitHub, LinkedIn, Notion, Jira, Figma, Confluence, Slack | [OpenCLI](https://github.com/jackwener/opencli) |
| Zero LLM cost — Chrome session + adapter, no AI API calls consumed | [OpenCLI](https://github.com/jackwener/opencli) |
| Persistent Chrome session — never triggers re-login flows between calls | [OpenCLI](https://github.com/jackwener/opencli) |
| opencli linkedin search — lead scraping without LinkedIn API rate limits | [OpenCLI](https://github.com/jackwener/opencli) |
| Wire OpenCLI actions into MAE: mae run triggers opencli adapters for data | [MAE](https://github.com/hmzainjamil/claude-ai-system) |

<a id="tips-git_/_github_6"></a>
### ■ **Git / GitHub (6)**
| Tip | Source |
|---|---|
| Always use GitHub Contents API for README pushes — avoids symlink conflicts | [gh CLI](https://cli.github.com) |
| Re-fetch SHA before every PUT — never cache SHA across multiple pushes | [GitHub API](https://docs.github.com) |
| auto-github-push hook: Write/Edit to ~/.claude/bin/ → auto-synced | [hooks](https://github.com/hmzainjamil/claude-ai-system) |
| Conventional commits: feat/fix/docs/chore — searchable history | [git](https://conventionalcommits.org) |
| Never push secrets — auto-github-push hook scrubs API keys before commit | [hooks](https://github.com/hmzainjamil/claude-ai-system) |
| Use git worktrees for parallel feature work — isolated branches per agent | [git](https://git-scm.com) |

<a id="tips-n8n_workflows_6"></a>
### ■ **n8n Workflows (6)**
| Tip | Source |
|---|---|
| 8,159 workflows in index — grep before building any automation from scratch | [n8n](https://github.com/hmzainjamil/hmz-n8n-workflows) |
| Error workflow: connect all nodes → Slack alert + retry on any failure | [n8n](https://n8n.io) |
| Queue mode + Redis: handles 1000+ concurrent workflow executions | [n8n](https://n8n.io) |
| Deploy any workflow: bash bin/deploy.sh workflows/my-flow.json | [n8n](https://github.com/hmzainjamil/hmz-n8n-workflows) |
| Split In Batches node: process 10K+ records without OOM errors | [n8n](https://n8n.io) |
| MAE bridge: mae run triggers n8n workflows for execution-heavy steps | [MAE](https://github.com/hmzainjamil/claude-ai-system) |

<a id="tips-debugging_6"></a>
### ■ **Debugging (6)**
| Tip | Source |
|---|---|
| tcc-dashboard — system status: queue depth, RAM, model health, last run | [tcc-dashboard](https://github.com/hmzainjamil/claude-ai-system) |
| ~/.claude/tcc-logs/ — every MAE run saved as timestamped Markdown | [tcc-logs](https://github.com/hmzainjamil/claude-ai-system) |
| mae plan 'goal' — preview decomposition before committing to full run | [MAE](https://github.com/hmzainjamil/claude-ai-system) |
| OODA on failures: Observe error → Orient cause → Decide fix → Act | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| health.sh pings all model endpoints — identifies dead APIs before blast | [health.sh](https://github.com/hmzainjamil/claude-ai-agents) |
| llm-burst --json 'prompt' — see all model scores before synthesis | [llm-burst](https://github.com/hmzainjamil/claude-ai-system) |

<a id="tips-paperclip_os_6"></a>
### ■ **Paperclip OS (6)**
| Tip | Source |
|---|---|
| Paperclip AI = always-on zero-human company OS — autopilot co-founder layer | [Paperclip](https://paperclip.ai) |
| All MAE run outputs auto-synced to Paperclip — full searchable audit trail | [Paperclip](https://paperclip.ai) |
| Set Paperclip to auto-approve low-risk decisions — true zero-human ops | [Paperclip](https://paperclip.ai) |
| Paperclip ingests n8n automation outputs via webhook → structured memory | [Paperclip](https://paperclip.ai) |
| Cross-session context: Paperclip + MEMORY.md = never lose context again | [Paperclip](https://paperclip.ai) |
| Paperclip dashboard shows all autonomous decisions — review weekly | [Paperclip](https://paperclip.ai) |

---

## ☠️ STARTUPS / BUSINESSES

| Feature | Replaced |
|---|---|
| 210 specialist AI agents | [Relevance AI](https://relevanceai.com) |
| Multi-agent orchestration | [CrewAI](https://crewai.com) |
| Tier 0 model routing | [LiteLLM](https://litellm.ai) |
| Division mode | [AutoGPT](https://autogpt.net) |
| Groq synthesis layer | [Together AI](https://together.ai) |
| Session memory | [Mem.ai](https://mem.ai) |
| Keyword auto-routing | [LangChain](https://langchain.com) |
| MAE orchestrator | [n8n](https://n8n.io) |
| Health monitoring | [Datadog](https://datadoghq.com) |
| Cross-LLM blast | [Helicone](https://helicone.ai) |
| Agent registry | [AgentOps](https://agentops.ai) |
| Custom agent builder | [Flowise](https://flowiseai.com) |
| Paperclip memory | [Mem.ai](https://mem.ai) |
| Wave batching | [BullMQ](https://bullmq.io) |
| Agent blast mode | [Autogen](https://microsoft.github.io/autogen/) |

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/claude-ai-agents&type=Date)](https://star-history.com/#hmzainjamil/claude-ai-agents&Date)
