# claude-ai-agents
> 210 specialist agents across 15 divisions — Engineering, Marketing, Sales, Design, Legal, Finance and more.

[![agents](https://img.shields.io/badge/agents-210-blue?style=flat&labelColor=555)](agents/)
[![divisions](https://img.shields.io/badge/divisions-15-green?style=flat&labelColor=555)](agents/)
[![mae](https://img.shields.io/badge/MAE-swarm-purple?style=flat&labelColor=555)](agents/)
[![tier0](https://img.shields.io/badge/routing-tier0-orange?style=flat&labelColor=555)](.)
[![license](https://img.shields.io/badge/license-MIT-lightgrey?style=flat&labelColor=555)](LICENSE)

[concepts](#concepts) · [architecture](#architecture) · [tips](#tips) · [startups](#startups) · [star](#star)

---

## 🧠 CONCEPTS <a id="concepts"></a>

| Feature | Location | Description |
|---|---|---|
| [**Engineering Division**](agents/engineering/) | `agents/engineering/` | 29 agents — Backend Architect, DevOps, SRE, Security, Code Reviewer, etc. |
| [**Marketing Division**](agents/marketing/) | `agents/marketing/` | 30 agents — SEO Specialist, Content Creator, Social Media, Growth Hacker |
| [**Specialized Division**](agents/specialized/) | `agents/specialized/` | 41 agents — AI Engineer, Data Engineer, Blockchain, Mobile, XR |
| [**Paid Media Division**](agents/paid-media/) | `agents/paid-media/` | 7 agents — PPC Strategist, Meta Ads, Google Ads, Programmatic Buyer |
| [**Sales Division**](agents/sales/) | `agents/sales/` | 8 agents — Discovery Coach, Deal Strategist, Account Strategist, SDR |
| [**MAE Swarm Routing**](agents/routes.json) | `agents/routes.json` | Keyword → agent routing — 13 patterns covering all task types |
| [**Agent Registry**](agents/agent-registry.json) | `agents/agent-registry.json` | 18 registered agents with model assignments and capabilities |
| [**all-agents skill**](agents/all-agents/) | `agents/all-agents/` | Single skill that activates all 210 agents simultaneously |

### 🔥 Hot

| Feature | Location | Description |
|---|---|---|
| [**Codex Agent Pattern**](agents/engineering/codex-agent.md) | `agents/engineering/` | OpenAI Codex-style agent: reads codebase → edits → runs → tests → proposes diffs |
| [**Deer Flow Agent**](agents/research/deer-flow.md) | `agents/research/` | ByteDance deep research pipeline — multi-step web + synthesis |
| [**OpenCLI Agent**](agents/browser/opencli-agent.md) | `agents/browser/` | Zero-cost browser automation — 90+ site adapters, zero LLM per call |

---

## ⚙️ ARCHITECTURE <a id="architecture"></a>

```
User prompt
     │
skill-auto-activate (keyword match)
     │
┌────▼──────────────────────────────────────────────┐
│                   MAE SWARM                        │
│                                                    │
│  researcher  strategist  copywriter  analyst       │
│  tactician   critic      optimizer                 │
│       ↓           ↓           ↓         ↓          │
│   Groq-70B    Gemini     DeepSeek    Kimi-K2.6     │
└────────────────────────┬──────────────────────────┘
                         │
                  Groq synthesis
                         │
                   Final output
```

| Division | Count | Routing keyword | Top model |
|---|---|---|---|
| Engineering | 29 | code/bug/build/deploy | DeepSeek-V3 |
| Marketing | 30 | ads/seo/content/brand | Gemini Flash |
| Specialized | 41 | ai/data/blockchain/mobile | Kimi K2.6 |
| Sales | 8 | lead/crm/prospect/deal | Groq 70B |
| Legal | 6 | contract/nda/compliance | Kimi K2.6 |
| Finance | 5 | budget/p&l/forecast | Groq 70B |

---

## 💡 TIPS AND TRICKS (16) <a id="tips"></a>

[agent-activation](#tips-activate) · [swarm](#tips-swarm) · [routing](#tips-route) · [custom-agents](#tips-custom)

<a id="tips-activate"></a>
■ **Agent Activation (4)**

| Tip | Source |
|---|---|
| `/all-agents` activates all 210 simultaneously — use for complex multi-domain tasks | [hmzainjamil](https://github.com/hmzainjamil) |
| `~/.claude/bin/skill-search <keyword>` finds the right agent before activating | [hmzainjamil](https://github.com/hmzainjamil) |
| `~/.claude/bin/skill-on <name>` activates one agent; `skill-off` deactivates after task | [hmzainjamil](https://github.com/hmzainjamil) |
| Never leave non-core skills active — deactivate after every task to prevent context bloat | [hmzainjamil](https://github.com/hmzainjamil) |

<a id="tips-swarm"></a>
■ **Swarm Execution (4)**

| Tip | Source |
|---|---|
| `mae run "goal"` auto-assigns the best agent per sub-task based on routes.json | [hmzainjamil](https://github.com/hmzainjamil) |
| Wave batching: agents run in concurrent groups sized by free RAM — never freezes machine | [hmzainjamil](https://github.com/hmzainjamil) |
| Each specialist agent uses a different Tier 0 model — zero model overlap = max diversity | [hmzainjamil](https://github.com/hmzainjamil) |
| Synthesis always uses Groq 70B — fastest high-quality model for final merge | [Groq](https://groq.com) |

<a id="tips-route"></a>
■ **Routing (4)**

| Tip | Source |
|---|---|
| `grep -i "keyword" ~/.claude/tcc-routes/routes.json` to find routing pattern for any task | [hmzainjamil](https://github.com/hmzainjamil) |
| apify route: any "scrape/extract/actor" task goes to Apify MCP — zero Claude tokens | [Apify](https://apify.com) |
| paperclip route: "ceo/company/goals/budget" tasks go to Paperclip CEO layer | [Paperclip AI](https://github.com/paperclipai) |
| claude-code-subagent route: complex coding tasks spawn isolated Claude subagent | [Anthropic](https://anthropic.com) |

<a id="tips-custom"></a>
■ **Custom Agents (4)**

| Tip | Source |
|---|---|
| Agent files are Markdown — add `# Role`, `## Capabilities`, `## Instructions` sections | [Claude Code SDK](https://docs.anthropic.com) |
| Place agent in `~/.claude/agents/` to make it globally available across all sessions | [hmzainjamil](https://github.com/hmzainjamil) |
| Name agents descriptively: `senior-ppc-analyst.md` not `agent1.md` | [hmzainjamil](https://github.com/hmzainjamil) |
| Test new agents with `mae run "simple task" --agent my-new-agent` before adding to swarm | [hmzainjamil](https://github.com/hmzainjamil) |

---

## ☠️ STARTUPS / BUSINESSES <a id="startups"></a>

| Feature | Replaced |
|---|---|
| **210-agent specialist swarm** | [AutoGPT](https://autogpt.net), [CrewAI](https://crewai.com), [LangGraph](https://langgraph.com) |
| **Agent routing table** | [LangChain Router](https://langchain.com), [Semantic Router](https://github.com/aurelio-labs/semantic-router) |
| **Zero-cost per-agent execution** | [AgentOps](https://agentops.ai), [LangSmith](https://smith.langchain.com) |
| **MAE 12-agent swarm synthesis** | [SuperAGI](https://superagi.com), [MetaGPT](https://github.com/geekan/MetaGPT) |
| **Division-based agent org** | [Relevance AI](https://relevanceai.com), [Crew AI Enterprise](https://crewai.com) |

---

## Star History <a id="star"></a>

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/claude-ai-agents&type=Date)](https://star-history.com/#hmzainjamil/claude-ai-agents&Date)
