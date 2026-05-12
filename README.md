# claude-ai-agents

![Version](https://img.shields.io/badge/version-2.0-blue?style=flat&labelColor=555)
![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat&labelColor=555)
![License](https://img.shields.io/badge/license-MIT-orange?style=flat&labelColor=555)
![Models](https://img.shields.io/badge/models-210%2B-purple?style=flat&labelColor=555)
![Agents](https://img.shields.io/badge/agents-210-red?style=flat&labelColor=555)

> **210 specialist AI agents** — engineering, marketing, sales, finance, legal, strategy, design, product, support, game dev, spatial computing, and more. Fully wired into MAE multi-agent orchestration with Tier 0 routing (zero Claude tokens for sub-tasks).

---

## 🧠 CONCEPTS

| Feature | Location | Description |
|---|---|---|
| [Agent Registry](agents/registry.json) | `agents/registry.json` | JSON manifest of all 210 agents — name, division, model, trigger keywords |
| [Engineering Division](agents/engineering/) | `agents/engineering/` | 29 agents: backend, frontend, DevOps, security, SRE, data engineering, embedded |
| [Marketing Division](agents/marketing/) | `agents/marketing/` | 30 agents: SEO, PPC, content, social, email, brand, growth, influencer |
| [Sales Division](agents/sales/) | `agents/sales/` | 8 agents: SDR, AE, sales engineer, deal strategist, RevOps, outbound |
| [Finance Division](agents/finance/) | `agents/finance/` | 5 agents: FP&A, bookkeeper, tax strategist, investment researcher, controller |
| [Legal Division](agents/legal/) | `agents/legal/` | 6 agents: contract review, compliance, IP, billing, intake, doc review |
| [Strategy Division](agents/strategy/) | `agents/strategy/` | 6 agents: GTM, product, brand guardian, chief of staff, exec summary, trend |
| [Product Division](agents/product/) | `agents/product/` | 5 agents: PM, sprint prioritizer, feedback synthesizer, experiment tracker, UX |
| [Design Division](agents/design/) | `agents/design/` | 8 agents: UI, UX researcher, visual storyteller, motion, inclusive visuals, brand |
| [Support Division](agents/support/) | `agents/support/` | 6 agents: customer service, healthcare, retail returns, loan officer, hospitality |
| [Game Dev Division](agents/gamedev/) | `agents/gamedev/` | 10 agents: game designer, narrative, level, audio, Unity, Unreal, Godot, Roblox |
| [Specialized Division](agents/specialized/) | `agents/specialized/` | 41 agents: psychologist, anthropologist, historian, geographer, narratologist |
| [Paid Media Division](agents/paidmedia/) | `agents/paidmedia/` | 7 agents: PPC, programmatic, paid social, search query, ad creative, ASO |
| [Spatial Computing](agents/spatial/) | `agents/spatial/` | 6 agents: XR developer, visionOS, WebXR, XR interface architect |
| [Testing Division](agents/testing/) | `agents/testing/` | 8 agents: QA, API tester, accessibility, performance benchmarker, model QA |
| [MAE Integration](agents/mae-bridge.sh) | `agents/mae-bridge.sh` | Routes any `mae run` goal to the correct specialist agent automatically |
| [Keyword Routing Map](agents/routing.json) | `agents/routing.json` | Keyword → agent → model mapping — auto-loaded by skill-router on every prompt |
| [Tier 0 Model Rules](agents/model-rules.md) | `agents/model-rules.md` | Which model each agent uses: Groq/Gemini/DeepSeek/Ollama — never Claude for sub-tasks |
| [Agent Blast Mode](agents/blast.sh) | `agents/blast.sh` | Fire ALL 210 agents simultaneously on a single goal — synthesizes best result |
| [Division Mode](agents/division.sh) | `agents/division.sh` | Activate a full division (e.g., "marketing mode") for focused multi-agent work |
| [Output Synthesis](agents/synthesize.py) | `agents/synthesize.py` | Groq-70B synthesizer merges all agent outputs into one production result |
| [Paperclip Sync](agents/paperclip-sync.sh) | `agents/paperclip-sync.sh` | Auto-saves every agent run to Paperclip AI for zero-human company memory |
| [Agent Health Check](agents/health.sh) | `agents/health.sh` | Pings all 210 agents — verifies each model is live and responding |
| [Custom Agent Builder](agents/builder.py) | `agents/builder.py` | Scaffold a new specialist agent from template in under 60 seconds |
| [Session Memory](agents/session-mem.py) | `agents/session-mem.py` | Per-session memory so agents remember context across 12-step workflows |

### 🔥 Hot

| Feature | Location | Description |
|---|---|---|
| [MAE 12-Agent Swarm](agents/mae-bridge.sh) | `agents/mae-bridge.sh` | Default execution mode — 12 agents fire in parallel, Groq synthesizes result in ~8s |
| [All-Agents Blast](agents/blast.sh) | `agents/blast.sh` | All 210 agents on one goal — maximum intelligence, maximum synthesis quality |
| [Tier 0 Routing](agents/model-rules.md) | `agents/model-rules.md` | Every sub-task → Groq/Gemini/DeepSeek → 0 Claude tokens consumed internally |
| [Keyword Auto-Detect](agents/routing.json) | `agents/routing.json` | Prompt scanned on every `UserPromptSubmit` → correct agent auto-activated |
| [Division Mode](agents/division.sh) | `agents/division.sh` | Single command activates full specialist division for complex domain tasks |

---

## ⚙️ ARCHITECTURE

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    CLAUDE-AI-AGENTS v2.0                                │
│                                                                         │
│  User Prompt → skill-router → keyword match → agent activated           │
│                                    │                                    │
│              ┌─────────────────────▼──────────────────────┐            │
│              │           MAE ORCHESTRATOR                  │            │
│              │  Phase 1: Groq decomposes → sub-tasks       │            │
│              │  Phase 2: 12 specialist agents fire         │            │
│              │  Phase 3: Cross-LLM blast (Groq+Gemini+DS)  │            │
│              │  Phase 4: Groq-70B synthesizes → output     │            │
│              └─────────────────────────────────────────────┘            │
│                                    │                                    │
│    ┌───────────┬───────────┬───────▼───┬───────────┬───────────┐       │
│    │Engineering│ Marketing │   Sales   │  Finance  │  Legal    │       │
│    │  29 agents│  30 agents│  8 agents │  5 agents │  6 agents │       │
│    └───────────┴───────────┴───────────┴───────────┴───────────┘       │
│                                    │                                    │
│              Tier 0 Model Routing (zero Claude tokens)                  │
│    Groq-70B · Gemini-Flash · DeepSeek-V3 · Ollama · OpenRouter         │
└─────────────────────────────────────────────────────────────────────────┘
```

| Layer | Technology | Purpose |
|---|---|---|
| Orchestration | MAE + TCC | Decompose → swarm → synthesize any goal |
| Model Layer | Groq / Gemini / DeepSeek | Tier 0 — zero Claude tokens for sub-tasks |
| Memory | Paperclip AI + ~/.claude/tcc-logs/ | Persistent cross-session agent memory |
| Routing | skill-router + routing.json | Keyword → agent auto-activation |
| Output | Markdown + JSONL | Structured synthesis saved to tcc-logs |

---

## 🚀 Quick Start

```bash
# Fire 12-agent swarm on any goal
mae run "write a cold email sequence for B2B SaaS"

# Activate full marketing division
~/.claude/agents/division.sh marketing "audit our Google Ads account"

# Blast all 210 agents
~/.claude/agents/blast.sh "what is our best GTM strategy for Q3"

# Check agent health
~/.claude/agents/health.sh

# Build a custom agent in 60s
~/.claude/agents/builder.py --name "fintech-analyst" --division finance --model groq
```

---

## 💡 TIPS AND TRICKS (48)

<a id="tips-routing"></a>
### ■ **Routing (6)**
| Tip | Source |
|---|---|
| Use `mae run` not `/agent` — MAE auto-routes to correct specialist | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| Add custom keywords to `routing.json` — agent auto-activates on next prompt | [routing.json](https://github.com/hmzainjamil/claude-ai-agents) |
| Division mode costs 0 extra tokens — uses same Tier 0 model pool | [model-rules.md](https://github.com/hmzainjamil/claude-ai-agents) |
| `tcc blast` fires tasks in parallel — 8x faster than sequential agent calls | [TCC](https://github.com/hmzainjamil/claude-ai-system) |
| Groq-70B is the default synthesis model — fastest cloud LLM available | [Groq](https://console.groq.com) |
| Agent blast mode synthesizes top 3 outputs — not average of all 210 | [blast.sh](https://github.com/hmzainjamil/claude-ai-agents) |

<a id="tips-tokens"></a>
### ■ **Token Savings (6)**
| Tip | Source |
|---|---|
| Every sub-agent → Tier 0 model → 0 Claude tokens consumed internally | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| Caveman compression on all outputs — cuts token count 60-80% | [caveman](https://github.com/hmzainjamil/claude-ai-skills) |
| Never re-read files already in context — agent state persists per session | [session-mem.py](https://github.com/hmzainjamil/claude-ai-agents) |
| Use `--jq` on GH API calls — returns only the field needed, not full JSON | [GitHub CLI](https://cli.github.com) |
| Batch all parallel tasks in one `tcc blast` call — fewer round-trips | [TCC](https://github.com/hmzainjamil/claude-ai-system) |
| Paperclip syncs outputs — no need to re-summarize in next session | [Paperclip](https://paperclip.ai) |

<a id="tips-models"></a>
### ■ **Model Selection (6)**
| Tip | Source |
|---|---|
| Code generation → DeepSeek-V3 via OpenRouter — best free coding model | [OpenRouter](https://openrouter.ai) |
| Research/analysis → Gemini 2.0 Flash — free, 1M context, fast | [Google AI](https://ai.google.dev) |
| Fast chat/synthesis → Groq llama3-70b — lowest latency cloud LLM | [Groq](https://console.groq.com) |
| Long doc analysis → Kimi-k2.5 (262K context) — replaces Opus at 5% cost | [Moonshot](https://api.moonshot.ai) |
| Local/offline → Ollama llama3 — zero cost, runs on Mac GPU | [Ollama](https://ollama.com) |
| 100+ free models → Bytez.com API — add as Tier 0 fallback | [Bytez](https://bytez.com) |

<a id="tips-agents"></a>
### ■ **Agent Design (6)**
| Tip | Source |
|---|---|
| Single responsibility per agent — one domain, one model, one output format | [builder.py](https://github.com/hmzainjamil/claude-ai-agents) |
| Use `--json` output format — downstream agents parse structured data | [registry.json](https://github.com/hmzainjamil/claude-ai-agents) |
| Health check before blast mode — skip dead model endpoints automatically | [health.sh](https://github.com/hmzainjamil/claude-ai-agents) |
| Synthesis agent always runs last — never let a sub-agent output raw to user | [synthesize.py](https://github.com/hmzainjamil/claude-ai-agents) |
| Division mode > individual agents for complex domain tasks | [division.sh](https://github.com/hmzainjamil/claude-ai-agents) |
| Register new agents in registry.json — MAE picks them up automatically | [registry.json](https://github.com/hmzainjamil/claude-ai-agents) |

<a id="tips-memory"></a>
### ■ **Memory & State (6)**
| Tip | Source |
|---|---|
| ~/.claude/tcc-logs/ — every MAE run auto-saved as timestamped Markdown | [MAE](https://github.com/hmzainjamil/claude-ai-system) |
| Paperclip AI is the always-on company OS — zero-human memory layer | [Paperclip](https://paperclip.ai) |
| session-mem.py persists agent context across 12-step workflows | [session-mem.py](https://github.com/hmzainjamil/claude-ai-agents) |
| Auto-learn hook writes learnings to ~/.claude/session-queue.jsonl | [auto-learn](https://github.com/hmzainjamil/claude-ai-skills) |
| MEMORY.md index loads on every session — agent history always available | [MEMORY.md](https://github.com/hmzainjamil/claude-ai-agents) |
| Stop hook processes session-queue → permanent memory files | [hooks](https://github.com/hmzainjamil/claude-ai-system) |

<a id="tips-orchestration"></a>
### ■ **Orchestration (6)**
| Tip | Source |
|---|---|
| MAE daily = full DigiMinds daily ops — all 12 divisions run in sequence | [mae](https://github.com/hmzainjamil/claude-ai-system) |
| tcc fire all — execute entire pending queue in parallel wave batches | [tcc](https://github.com/hmzainjamil/claude-ai-system) |
| Wave batching auto-scales to available RAM — cloud APIs = 0 RAM | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |
| Cross-LLM blast = Groq + Gemini + DeepSeek simultaneously on same task | [mae](https://github.com/hmzainjamil/claude-ai-system) |
| Groq-70B synthesis judge picks best response — not averaging outputs | [synthesize.py](https://github.com/hmzainjamil/claude-ai-agents) |
| Phase decomposition: Groq breaks goal → tasks → specialist routing | [mae-bridge.sh](https://github.com/hmzainjamil/claude-ai-agents) |

<a id="tips-hooks"></a>
### ■ **Hooks (6)**
| Tip | Source |
|---|---|
| UserPromptSubmit → skill-auto-activate → keyword scan → agent loaded | [settings.json](https://github.com/hmzainjamil/claude-ai-system) |
| PostToolUse → auto-github-push → bin/ files auto-synced to repos | [hooks](https://github.com/hmzainjamil/claude-ai-system) |
| Stop hook → session-queue processor → memory files updated | [hooks](https://github.com/hmzainjamil/claude-ai-system) |
| SessionStart hooks: MAE status, RAM check, model availability ping | [hooks](https://github.com/hmzainjamil/claude-ai-system) |
| compact-guard hook prevents context overflow on long agent runs | [compact-guard](https://github.com/hmzainjamil/claude-ai-skills) |
| All hooks run in < 200ms — never block the main conversation | [settings.json](https://github.com/hmzainjamil/claude-ai-system) |

<a id="tips-debug"></a>
### ■ **Debugging (6)**
| Tip | Source |
|---|---|
| `tcc-dashboard` — full system status: queue, RAM, model health, last run | [tcc-dashboard](https://github.com/hmzainjamil/claude-ai-system) |
| Check ~/.claude/tcc-logs/ for raw agent outputs if synthesis looks wrong | [tcc-logs](https://github.com/hmzainjamil/claude-ai-system) |
| Run health.sh before blast — identifies dead endpoints before wasting calls | [health.sh](https://github.com/hmzainjamil/claude-ai-agents) |
| `mae plan "goal"` — preview decomposition before committing to full run | [mae](https://github.com/hmzainjamil/claude-ai-system) |
| `llm-burst --json "prompt"` — see all model scores before synthesis | [llm-burst](https://github.com/hmzainjamil/claude-ai-system) |
| OODA loop on failures — observe error, orient cause, decide fix, act | [CLAUDE.md](https://github.com/hmzainjamil/claude-ai-system) |

---

## ☠️ STARTUPS / BUSINESSES

| Feature | Replaced |
|---|---|
| 210 specialist AI agents | [Relevance AI](https://relevanceai.com) agent marketplace |
| Multi-agent orchestration | [CrewAI](https://crewai.com) crew management |
| Tier 0 model routing | [LiteLLM](https://litellm.ai) model proxy |
| Division mode | [AutoGPT](https://autogpt.net) agent teams |
| Groq synthesis layer | [Together AI](https://together.ai) inference API |
| Session memory + Paperclip | [Mem.ai](https://mem.ai) AI memory |
| Keyword auto-routing | [LangChain](https://langchain.com) agent routing |
| MAE orchestrator | [n8n](https://n8n.io) workflow engine |
| Health monitoring | [Datadog](https://datadoghq.com) APM |
| Cross-LLM blast | [Helicone](https://helicone.ai) LLM gateway |
| Agent registry | [AgentOps](https://agentops.ai) agent registry |
| Custom agent builder | [Flowise](https://flowiseai.com) no-code builder |

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/claude-ai-agents&type=Date)](https://star-history.com/#hmzainjamil/claude-ai-agents&Date)
