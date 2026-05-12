# claude-ai-agents
Specialized Claude sub-agents — parallelized, cost-routed, domain-expert AI workers.

![agents](https://img.shields.io/badge/agents-20%2B-blue?style=flat&labelColor=555)
![tier0](https://img.shields.io/badge/routing-Tier0%20first-orange?style=flat&labelColor=555)
![parallel](https://img.shields.io/badge/execution-parallel-green?style=flat&labelColor=555)
![platform](https://img.shields.io/badge/platform-Claude%20Code-lightgrey?style=flat&labelColor=555)
![license](https://img.shields.io/badge/license-MIT-blue?style=flat&labelColor=555)

[Concepts](#-concepts) · [Architecture](#️-architecture) · [Tips](#-tips-and-tricks-20) · [Kills](#️-startups--businesses) · [Stars](#star-history)

## 🧠 CONCEPTS

| Feature | Location | Description |
|---------|----------|-------------|
| [**Explore Agent**](agents/explore) | `agents/explore` | Fast codebase explorer — Glob/Grep/Read without modifying files [![read-only](https://img.shields.io/badge/mode-read--only-yellow?style=flat&labelColor=555)] |
| [**Plan Agent**](agents/plan) | `agents/plan` | Software architect — designs implementation strategy, identifies critical files |
| [**General Purpose**](agents/general-purpose) | `agents/general-purpose` | Multi-step research + execution with full tool access |
| [**Ads Strategy Agent**](agents/ads-strategy) | `agents/ads-strategy` | Google/Meta/PPC campaign planning — ROAS focus |
| [**SEO Agent**](agents/seo) | `agents/seo` | Technical + content SEO — E-E-A-T, schema, crawlability |
| [**Legal Agent**](agents/legal) | `agents/legal` | Contract review, compliance checks, NDA triage |
| [**Market Research Agent**](agents/market-research) | `agents/market-research` | Competitor intel, trend analysis, audience mapping |
| [**Code Review Agent**](agents/code-review) | `agents/code-review` | Security-first review — OWASP top 10, performance, maintainability |
| [**Nimble Researcher**](agents/nimble-researcher) | `agents/nimble-researcher` | Fast data gathering — parallel searches, structured results |
| [**Nimble Analyst**](agents/nimble-analyst) | `agents/nimble-analyst` | Deep synthesis — cross-reference data, strategic assessment |

### 🔥 Hot

| Feature | Location | Description |
|---------|----------|-------------|
| [**Paperclip CEO Loop**](agents/paperclip-ceo-loop) | `agents/paperclip-ceo-loop` | Autonomous business operations agent — DigiMinds AI CEO at 127.0.0.1:3100 |
| [**All-Agents Orchestrator**](agents/all-agents) | `agents/all-agents` | Meta-agent — spawns and coordinates all domain agents in parallel |
| [**BDM Agent**](agents/bdm) | `agents/bdm` | Business development — LinkedIn + Indeed pipeline, cover letters, outreach |

## ⚙️ ARCHITECTURE

```
Agent execution model:
  User Prompt
      │
      ▼
  Orchestrator (Claude Sonnet — conversation layer only)
      │
      ├─── Explore Agent ─── Tier 0 (Groq/Gemini) ──→ file analysis
      ├─── Research Agent ── Tier 0 (DeepSeek) ────→ web research
      ├─── Code Agent ────── Tier 0 (GPT-4o-mini) →  code generation
      └─── Synthesis ──────── Claude (final layer) →  output to user
```

| Agent Type | Default Model | Fallback | Use Case |
|-----------|--------------|---------|---------|
| Explore | Groq Llama 3 | Gemini Flash | Read-only codebase scan |
| Research | DeepSeek-V3 | Groq | Web fetch + analysis |
| Code | GPT-4o-mini | Ollama CodeLlama | Generation + debug |
| Legal | Claude Haiku | GPT-4o-mini | Contract review |
| Final Output | Claude Sonnet | — | User-facing synthesis |

## 💡 TIPS AND TRICKS (20)

[parallel](#tips-parallel) · [routing](#tips-routing) · [prompting](#tips-prompting) · [tools](#tips-tools)

<a id="tips-parallel"></a>■ **Parallel Execution (5)**

| Tip | Source |
|-----|--------|
| Launch independent agents in a single message — one `<tool_calls>` block with N agents | [HMZ](https://github.com/hmzainjamil) |
| Use `run_in_background=true` for research agents while doing other work | [HMZ](https://github.com/hmzainjamil) |
| Foreground agents: when you need results before next step. Background: fire-and-forget | [HMZ](https://github.com/hmzainjamil) |
| Batch 3-5 Groq calls simultaneously — Groq free tier = 30 req/min, use it all | [Groq](https://console.groq.com) |
| Agent context is isolated — pass only what the agent needs, not full conversation | [HMZ](https://github.com/hmzainjamil) |

<a id="tips-routing"></a>■ **Cost Routing (5)**

| Tip | Source |
|-----|--------|
| Sub-agents NEVER use Claude — always Tier 0 (Groq, Gemini, DeepSeek, GPT-4o-mini) | [HMZ](https://github.com/hmzainjamil) |
| `llm-burst` CLI routes to cheapest available cloud model automatically | [HMZ](https://github.com/hmzainjamil) |
| Ollama local agents cost $0 — use for any task that doesn't need internet | [HMZ](https://github.com/hmzainjamil) |
| Kimi K2.5 at $0.15/1M input is the best Opus replacement for long-context tasks | [Moonshot](https://platform.moonshot.cn) |
| Always caveman-compress agent outputs before returning to orchestrator | [HMZ](https://github.com/hmzainjamil) |

<a id="tips-prompting"></a>■ **Agent Prompting (5)**

| Tip | Source |
|-----|--------|
| Tell agent whether to write code or just research — ambiguity wastes tokens | [HMZ](https://github.com/hmzainjamil) |
| Include 3-5 word description in Agent tool call — shows in user-visible output | [HMZ](https://github.com/hmzainjamil) |
| Subagent_type=Explore for codebase scans — specialized, faster than general-purpose | [HMZ](https://github.com/hmzainjamil) |
| Provide complete task description — agent starts fresh with no prior context | [HMZ](https://github.com/hmzainjamil) |
| Use isolation=worktree for agents making code changes — prevents branch conflicts | [HMZ](https://github.com/hmzainjamil) |

<a id="tips-tools"></a>■ **Tool Selection (5)**

| Tip | Source |
|-----|--------|
| Explore agent uses Glob/Grep — never Agent tool for simple file searches | [HMZ](https://github.com/hmzainjamil) |
| code-review-graph MCP before Grep/Glob for codebase exploration — semantic search | [HMZ](https://github.com/hmzainjamil) |
| Apify MCP for all web data extraction — no Claude tokens consumed | [Apify](https://apify.com) |
| Use WebSearch → WebFetch pipeline: search for URLs, then fetch specific pages | [HMZ](https://github.com/hmzainjamil) |
| Plan agent returns step-by-step plans — use before any non-trivial implementation | [HMZ](https://github.com/hmzainjamil) |

## ☠️ STARTUPS / BUSINESSES

| Feature | Replaced |
|-|-|
| **Parallel Sub-Agent System** | [CrewAI](https://crewai.com), [AutoGen](https://github.com/microsoft/autogen), [LangGraph](https://langgraph.com) |
| **Cost-Routed Agent Execution** | [LangChain](https://langchain.com), [LlamaIndex](https://llamaindex.ai) |
| **Domain Expert Agents** | [Relevance AI](https://relevanceai.com), [AgentOps](https://agentops.ai) |
| **BDM / Outreach Agent** | [Apollo.io](https://apollo.io), [Outreach](https://outreach.io), [Salesloft](https://salesloft.com) |
| **CEO Loop / Autopilot** | [Lindy AI](https://lindy.ai), [Beam AI](https://beam.ai), [Artisan](https://artisan.co) |

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/claude-ai-agents&type=Date)](https://star-history.com/#hmzainjamil/claude-ai-agents&Date)
