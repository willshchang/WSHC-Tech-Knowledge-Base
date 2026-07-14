# LangChain — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  
**Official Reference:** https://www.langchain.com  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Founded** | Late 2022 (started as an open-source side project) |
| **Incorporated as a company** | 2023 |
| **HQ** | San Francisco, CA |
| **Team size** | ~325 employees (as of mid-2026) |
| **Stage** | Series B |
| **Total funding** | $260M raised across 4 rounds |
| **Latest valuation** | $1.25B (October 2025) |
| **Revenue** | ~$16M ARR, ~1,000 customers |
| **Notable customers** | Klarna, LinkedIn, GitLab, Elastic, Workday, Rippling, Replit |
| **Category** | AI agent orchestration / agent engineering platform |
| **Website** | https://www.langchain.com |

---

## Founders

### Harrison Chase — Co-Founder & CEO

- Harvard University — bachelor's degree (2017)
- Sports Analytics Collective at Harvard — early exposure to statistics, data science, ML
- Machine Learning Engineer at **Kensho Technologies** (2017–2019)
- Joined **Robust Intelligence** (2019–2022) — worked on testing and validating ML models
- Built a Notion/Slack querying bot at a company hackathon — an early precursor to what became LangChain
- Released LangChain as a personal side project (~800 lines of Python) in October 2022, from his personal GitHub
- ChatGPT launched one month later (November 2022) — LangChain rode the first wave of LLM developer interest
- GitHub stars: 5K (Feb 2023) → 18K (Apr 2023) → 96K+ (Dec 2024) → ~118K (2026)

### Ankush Gola — Co-Founder

- B.S.E. in Electrical Engineering, Princeton University (2015)
- Software engineer at Facebook (2015–2019)
- Former co-worker of Chase's at Robust Intelligence
- Joined as co-founder once Chase incorporated LangChain as a company

---

## Funding History

| Round | Amount | Date | Lead | Valuation |
|---|---|---|---|---|
| Seed | $10M | April 2023 | Benchmark | — |
| Series A | $25M | April 2023 (week later) | Sequoia Capital | ~$200M |
| Series B | $100M | July 2025 | IVP | ~$1.1B |
| Series B extension | $125M | October 2025 | IVP (new investors: CapitalG, Sapphire Ventures; existing: Sequoia, Benchmark, Amplify) | $1.25B |

**Total raised:** $260M across 4 rounds from 15+ investors.

> LangChain went from a personal side project to a $1.25B unicorn in roughly 3 years — one of the fastest trajectories in the AI infrastructure space.

---

## The Origin Story: Why LangChain Exists

Early LLMs (GPT-3, early GPT-4) had a fundamental limitation: **they could only generate text based on their training data.** They couldn't:

- Search the web for current information
- Call external APIs
- Query a database
- Remember anything between separate calls
- Break a complex task into multiple steps and execute them in sequence

LangChain solved this by providing **composable abstractions** — building blocks that let developers wire an LLM up to tools, data sources, and multi-step logic without reinventing the plumbing every time.

> Think of it this way: an LLM by itself is a very smart person locked in a room with no phone, no internet, and no memory of yesterday. LangChain builds the door, the phone, and the notebook.

---

## Product Suite — Comprehensive Breakdown

LangChain's product suite covers the **entire lifecycle of building an AI agent** — from first prototype to production monitoring. Here's what each piece does and how they connect.

### 1. LangChain (the original framework)

The foundational open-source library. Provides the core abstractions:

- **Prompts** — reusable templates for instructing the LLM
- **Chains** — sequences of operations (prompt → LLM call → parse output → next step)
- **Memory** — ways for an agent to remember prior conversation turns or task steps
- **Tools** — wrappers that let an LLM call external functions, APIs, or databases
- **Retrievers** — connectors for pulling in outside data (documents, search results, databases)

**In plain English:** This is the "Lego set" — individual pieces you snap together to build an LLM-powered application.

### 2. LangGraph

A more advanced framework built on top of LangChain, designed specifically for **agents that need to survive real-world production conditions.**

| Problem It Solves | How |
|---|---|
| Agent crashes mid-task | State is persisted automatically — the agent picks up where it left off after a restart |
| Complex branching logic | Represents workflows as a **graph** (nodes and edges) instead of a straight-line sequence — supports loops, retries, conditional branches |
| Long-running tasks | Built-in checkpointing — the agent's progress is saved at each step |
| Human approval steps | First-class support for **human-in-the-loop** — the agent can pause and wait for a person to approve a step before continuing |

**LangGraph reached GA (general availability) in October 2025** with durable state, built-in persistence, and first-class HITL support. It's now considered the **default choice for complex, stateful agent workflows** across the industry.

**Analogy:** If LangChain is the Lego set, LangGraph is the instruction manual plus a "save game" feature — it makes sure your creation doesn't fall apart if the power goes out halfway through building it.

### 3. Deep Agents (also called "dcode" — Deep Agents Code)

The **harness layer** for long-running, complex agents. This is what handles:

- **Planning** — breaking a big task into smaller sub-steps
- **Tool use** — deciding which tool to call and when
- **Memory management** — tracking what's already been done
- **Task execution** — actually carrying out each step and handling errors

This is the layer NVIDIA tuned for Nemotron 3 Ultra (see NemoClaw section below).

### 4. LangSmith

The **observability and agent engineering platform** — this is where developers debug, evaluate, and improve their agents in production.

| Feature | What It Does |
|---|---|
| **Tracing** | Records every single step an agent takes — every tool call, every LLM response — so you can replay exactly what happened |
| **Evaluations** | Test agent outputs against datasets, using either fixed test cases or "LLM-as-judge" scoring |
| **Prompt management** | Version and test different prompt variations, similar to how developers version code |
| **Deployment** | Ship agents to production directly from the platform |
| **Cost tracking** | Unified view of cost across an entire agent workflow, not just individual LLM calls |

**Analogy:** If your agent is a new employee, LangSmith is the manager's dashboard — you can see every task they did, replay their exact steps when something goes wrong, and grade their work against a rubric.

### 5. LangSmith Fleet (formerly "Agent Builder")

A **no-code agent builder** — lets non-developers build and configure agents through a chat-like interface instead of writing code. Renamed from Agent Builder to Fleet in March 2026.

### 6. LangSmith Engine

The newest addition — an **automated failure-hunting system.** It watches your production agent traces, automatically clusters recurring failures, and opens pull requests with suggested fixes for a human to review.

> This is a meaningful shift: instead of a human manually digging through logs to find why an agent failed, the system finds the pattern and proposes the fix itself. The human's job becomes reviewing the fix, not hunting for the bug.

### 7. OpenWiki (what you saw referenced as "LangWiki" at the webinar)

An open-source CLI tool that solves a specific problem: **AI coding agents don't understand your codebase the way a human teammate does.**

- Traditional documentation (READMEs, docstrings) is written for humans to skim
- OpenWiki generates a **living wiki written specifically for LLMs to consume** — structured markdown, cross-references, and summaries optimized for how an AI agent reads context
- It auto-updates via a scheduled GitHub Action — scans commits since the last run, updates the wiki, and opens a pull request
- It automatically wires itself into `AGENTS.md` or `CLAUDE.md` so any coding agent working in the repo knows where to find this documentation

This is based on an idea from AI researcher **Andrej Karpathy**, called the "LLM Wiki" pattern — instead of the AI repeatedly searching through scattered docs (RAG), you maintain one living, agent-optimized wiki that the AI itself keeps up to date.

**Why this matters:** As AI coding agents take on bigger, more autonomous tasks, the bottleneck isn't the model's intelligence — it's whether the agent has the *context* to understand the codebase correctly. OpenWiki is LangChain's answer to that context problem.

---

## The NVIDIA Partnership: NemoClaw & the "Harness" Concept

In July 2026, LangChain and NVIDIA announced the **NemoClaw for LangChain Deep Agents** blueprint — a big moment for the "open agent stack" movement.

### What Happened

NVIDIA has an open-weight model called **Nemotron 3 Ultra**. LangChain's team ran it through their public Deep Agents benchmark, then did something important:

> Instead of retraining the model, they tuned the **harness** around it — adjusting system prompts, tool descriptions, and middleware.

**Result:** Nemotron 3 Ultra + a LangChain-tuned harness scored **0.86** on LangChain's agent evaluation suite — very close to Claude Opus's **0.87** — but at **10x lower inference cost** ($4.48 vs. $43.48 per benchmark run).

### The Three-Layer Blueprint

| Layer | Component | What It Provides |
|---|---|---|
| Model | NVIDIA Nemotron 3 Ultra | Open-weight model — enterprises can inspect and customize it, unlike closed models |
| Harness | LangChain Deep Agents Code | Planning, tool use, memory, task execution — tuned specifically for Nemotron 3 Ultra |
| Runtime | NVIDIA OpenShell | Secure sandbox for executing agent actions safely — policy-based control over what agents can touch |

Jensen Huang, NVIDIA's CEO: **"Super agents have arrived."**

Harrison Chase's framing was more nuanced — emphasizing that **building robust systems around models matters more than just scaling the models themselves.**

### What "Harness" Actually Means

This is the most important concept to understand from this whole story.

**A harness is everything wrapped around a raw AI model that turns it into a working, reliable agent.** The model alone is just a "brain" that can predict the next word. It cannot act on its own. The harness provides:

- **System prompts** — instructions telling the model how to behave and what its role is
- **Tool descriptions** — explanations of what functions/APIs the agent can call, and when to call them
- **Memory management** — how the agent tracks what it has already done across a long task
- **Planning logic** — how a big goal gets broken into smaller, ordered steps
- **Middleware** — code that sits between each step, adjusting inputs/outputs, adding guardrails, logging, or retry logic

**Analogy:** If the AI model is the engine, the harness is the entire car built around it: steering wheel, brakes, dashboard, seatbelts. The exact same engine can drive completely differently depending on the harness built around it.

**Why this discovery matters industry-wide:** LangChain proved that a cheaper, open-weight model can perform close to an expensive frontier model **purely by improving the harness** — without retraining the model itself. This changes the economics of enterprise AI: companies may not need the most expensive model if they invest in a great harness instead.

### Jensen Huang's "Operating System" Framing

Huang's broader argument (from his interview with Chase): AI has become genuinely useful in the last six months because of **agentic systems** — models that can autonomously use tools, manage memory, and iteratively complete tasks. His prediction:

> Enterprises should build their own proprietary "super agents" using open frameworks and their own domain-specific data — rather than outsourcing intelligence entirely to a single closed model provider.

The implication for LangChain specifically: **LangChain becomes the "operating system" layer for agents** — the orchestration and harness plumbing that any model plugs into. Just as most companies don't build their own OS (they build on Windows, macOS, Linux), Huang's bet is that most companies won't build their own agent orchestration from scratch — they'll build on LangChain's harness layer, bringing their own model and data.

---

## Market Position & Competitors

LangChain operates in a genuinely crowded and fast-moving space. Here's the landscape:

| Framework | Built By | Best For | How It Differs from LangChain |
|---|---|---|---|
| **LangGraph** (LangChain) | LangChain | Complex, stateful, production workflows | This is LangChain's own advanced framework, not a competitor |
| **LlamaIndex** | LlamaIndex | RAG (retrieval-augmented generation) — connecting LLMs to external data extremely well | LangChain is broader/general-purpose; LlamaIndex is retrieval-first and narrower |
| **CrewAI** | Joao Moura | Multi-agent systems organized by role (researcher, writer, editor) | Built specifically to be simpler than LangChain — faster to a working prototype |
| **AutoGen / AG2** | Microsoft Research | Conversational multi-agent systems — agents "talk" to each other | Treats workflows as conversations between agents rather than a structured graph |
| **Semantic Kernel** | Microsoft | Enterprise .NET/Java/Python environments | Lighter weight, strong Microsoft ecosystem integration |
| **OpenAI Agents SDK** | OpenAI | Vendor-native agent building tied to OpenAI models | Locked to OpenAI's ecosystem |
| **Claude Agent SDK** | Anthropic | Vendor-native agent building tied to Claude models | Gained significant traction in 2026; locked to Anthropic's ecosystem |

### Where LangChain Wins

- **Broadest tool integrations** — connects to more external tools and data sources than any competitor
- **Fastest model/provider swapping** — not locked to one AI vendor
- **Most widely adopted** — the default choice for complex, stateful workflows requiring branching, retries, and durable checkpoints
- **~118K GitHub stars** — the largest open-source community in this space

### An Important Industry Caveat

Analysts note a real gap across **all** of these frameworks, including LangChain: none of them natively provide **governance** — pre-dispatch approval gates, policy enforcement, or audit evidence before an agent acts on production systems.

> "None of them governs risky actions before they hit production, so pair your pick with an agent control plane for policy, approvals, and audit."

This is a meaningful gap — and it's exactly where identity and security tooling (Okta for AI Agents, Tailscale's network-layer scoping, and detection platforms like Artemis) becomes necessary *alongside* a framework like LangChain, not instead of it.

---

## Why LangChain Is a "Native" Builder (Your Framing, Verified)

Your instinct to separate LangChain and Artemis from point solutions like Cyera, ConductorOne, Lumos, and Okta is well-supported:

| Category | Examples | What They Actually Do |
|---|---|---|
| **Native / full-stack builders** | LangChain, Artemis | Built the underlying orchestration or detection *engine* from scratch — own the whole problem end-to-end |
| **Point solutions layered on top** | Cyera (DSPM), ConductorOne / Lumos (IGA), Okta (IAM) | Solve one specific slice of a larger problem — valuable, but built assuming other infrastructure (identity providers, cloud platforms, data stores) already exists underneath them |

LangChain didn't build "an AI feature for existing software" — it built the **plumbing that agentic AI runs on**, the same way Artemis rebuilt detection from the ground up instead of adding AI on top of a legacy SIEM. Both are "AI-native" in the truest sense: the AI capability *is* the product, not a feature bolted onto something older.

---

## Ecosystem & Tailscale Relevance

This is a genuinely new domain relative to your existing IAM/ZTNA focus, but the connection points are real:

| Angle | Detail |
|---|---|
| **Agent-to-environment connectivity** | LangChain agents (built with LangGraph/Deep Agents) still need to *reach* tools, APIs, and customer environments securely. That's a network and identity problem — exactly where Tailscale's tsnet model fits, the same way Cleric's agent uses tsnet for scoped access |
| **NVIDIA OpenShell vs. Tailscale** | OpenShell is a compute-level sandbox (controls what an agent can *do* once running). Tailscale is a network-level gate (controls what an agent can *reach*). These are complementary, not competing — a governed agent needs both |
| **The governance gap** | Analysts flagged that LangChain and its competitors don't natively provide approval gates or audit trails. This is the same gap Okta for AI Agents addresses at the identity layer, and where Tailscale's ACLs + audit logs contribute at the network layer |
| **OpenWiki as a context tool** | Interesting adjacent tooling to your own WSHC KB-building practice — LangChain built a tool that does programmatically what you're doing manually: maintaining a living, agent/human-optimized knowledge base |

---

## Key Takeaways

- **LangChain went from an 800-line personal side project (Oct 2022) to a $1.25B unicorn in under 3 years** — one of the fastest trajectories in AI infrastructure
- **The product suite covers the full agent lifecycle**: LangChain (build) → LangGraph (durable execution) → Deep Agents (harness) → LangSmith (observe/evaluate/deploy) → LangSmith Engine (auto-fix) → OpenWiki (codebase context)
- **"Harness" is the critical concept** — everything wrapped around a raw model (prompts, tools, memory, planning, middleware) that turns it into a working agent. Tuning the harness can close most of the performance gap to an expensive frontier model, at a fraction of the cost
- **NemoClaw (NVIDIA + LangChain)** proved this concretely — an open-weight model + tuned harness nearly matched Claude Opus at 10x lower cost
- **Jensen Huang's "operating system" framing** — LangChain aims to be the foundational orchestration layer every enterprise agent is built on top of, the way Windows/macOS/Linux underpin most software
- **LangChain is a "native" builder**, same tier as Artemis — it built the orchestration engine itself, not a feature layered on existing infrastructure
- **The real gap across the entire framework category**: none natively govern risky agent actions before production — no approval gates, no audit trail by default. This is exactly where identity, network, and security tooling (Okta, Tailscale, Artemis) becomes essential alongside a framework, not a replacement for one

---

## Official References

| Source | Link |
|---|---|
| LangChain official site | https://www.langchain.com |
| LangChain docs | https://docs.langchain.com |
| Harrison Chase — Three Years of Building LangChain | https://www.langchain.com/blog/three-years-langchain |
| NVIDIA Blog — Nemotron + LangChain Deep Agents | https://blogs.nvidia.com/blog/nemotron-langchain-agents-open-stack/ |
| LangChain Blog — NemoClaw Announcement | https://www.langchain.com/blog/langchain-and-nvidia-launch-the-nemoclaw-deep-agents-blueprint |
| 4sysops — NemoClaw Explained | https://4sysops.com/archives/what-is-nvidia-nemoclaw-nemotron-3-ultra-langchain-deep-agents-and-openshell-explained/ |
| GitHub — langchain-ai/openwiki | https://github.com/langchain-ai/openwiki |
| Times of AI — OpenWiki Explained | https://www.timesofai.com/news/what-is-openwiki-explained/ |
| Contrary Research — LangChain Business Breakdown | https://research.contrary.com/company/langchain |
| TechCrunch — LangChain Hits $1.25B Valuation | https://techcrunch.com/2025/10/21/open-source-agentic-startup-langchain-hits-1-25b-valuation |
| Tracxn — LangChain Company Profile | https://tracxn.com/d/companies/langchain |
| Atlan — AI Agent Frameworks Compared | https://atlan.com/know/ai-agents-frameworks-compared/ |
| Cordum — AI Agent Frameworks Comparison (Governance Gap) | https://cordum.io/blog/ai-agent-frameworks-comparison |
