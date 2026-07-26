# ZTIA Ecosystem Map: Zero Trust Identity Access, Layer by Layer

**Document Type:** Knowledge Article / Interview Reference — Core Framework  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  

---

## The Core Thesis

Modern enterprise security isn't one product category — it's a stack of distinct layers, each solving a specific pain, each owned by different companies (sometimes the same company operating in more than one layer at once).

**Zero Trust Identity Access (ZTIA)** is the umbrella framework for organizing this stack. It answers three questions for any company, product, or capability:

1. **What pain does this actually solve?**
2. **What layer of the stack does it operate at?**
3. **What can it not do — and who fills that gap?**

This isn't a product catalog. A catalog lists what companies sell. An ecosystem map diagnoses what pain exists and who's actually solving each piece of it — including the reality that one company can show up in more than one layer, and that some layers currently have real, unfilled gaps.

---

## Why Layers, Not Companies

Organizing by company category breaks down fast — most of the interesting companies right now don't stay in one lane:

- **Origin** looks like an Endpoint tool but its real differentiation is causal observability, not device management
- **Dosu** looks like a dev tool but structurally solves the same "discovery + context" problem as **Cyera** — just for knowledge instead of data
- **1Password** spans Secrets/Credentials AND, as of July 2026, Financial/Spend visibility — two different jobs, one company
- **LangChain** looks like it should govern agents but explicitly does not — it builds them

Organizing by **layer and pain** instead of company name is what makes this an actual ecosystem map rather than a vendor list.

---

## The Full Layer Map

| Layer | Core Question It Answers | Companies | Notes |
|---|---|---|---|
| **Network** | What can reach what? | Tailscale, Twingate, ZeroTier | Network-as-gate — identity-verified connectivity, segmentation, least-privilege reachability |
| **Identity & Access** | Should this identity (human or agent) be here? | Okta, Microsoft Entra ID, ConductorOne, Lumos | Access governance, SSO, lifecycle management, entitlement reviews |
| **Discovery & Context — Data** | Do we know what sensitive data we have, and is it exposed? | Cyera | DSPM — discovery, classification, risk scoring for data |
| **Discovery & Context — Knowledge** | Does this agent actually understand what it's looking at? | Dosu | Grounds AI answers in real project context to prevent hallucination |
| **Detection** | Is something behaving wrong right now? | Artemis, CrowdStrike | Cross-domain behavioral detection and response — this is the job, regardless of deployment mechanism |
| **Telemetry Visualization & Aggregation** | Can we see and correlate signals across metrics, logs, and traces in one place? | Grafana Labs (LGTM stack) | General infrastructure observability, not identity-native — the layer other layers' data often gets visualized through; edging toward Detection as it adds SOC/security analytics capability |
| **Agent Construction** | How do we build the agent in the first place? | LangChain | Orchestration/development layer — the raw material other layers react to. Explicitly does NOT govern what it builds |
| **Endpoint Visibility** | What's on this machine, is it compliant, what changed? | Tanium, Ivanti | State snapshots, inventory, query-based — tells you *that* something happened, not *why* |
| **Hybrid Workforce Observability** | Why did this happen — what did a human or AI agent actually do, step by step? | Origin | Vendor-agnostic causal tracing (prompt → reasoning → action → outcome) across both human and AI activity — the layer nobody else operates at with this depth |
| **Secrets & Credentials** | Are secrets and non-human credentials protected? | 1Password, HashiCorp Vault | Vaulting, rotation, NHI governance |
| **AI Financial Visibility** | What are we actually spending on AI, and by whom? | 1Password (AI Spend and Consumption Management) | Financial/spend visibility ONLY — explicitly not behavioral or causal. "Token bills tell you what you spent. [Hybrid Workforce Observability] tells you what you bought." |
| **Cloud Posture** | Is our cloud environment misconfigured or exposed? | Wiz, Orca | CSPM — scans cloud resource configs for exposure |
| **IT Workflow Orchestration** | How do we turn ground-truth data into automated action? | ServiceNow (Now Assist AI Agents; also ITOM AI Prime powered by Tanium) | Consumes endpoint/data truth from other layers, orchestrates workflows and remediation on top of it — does not generate the ground truth itself |

---

## Layer Deep Dives

### Network

Network-as-gate, not network-as-sensor. Encryption has made deep packet inspection largely obsolete, but controlling *what can reach what* is more important than ever in a Zero Trust world.

Tailscale's specific differentiator: identity-first mesh networking at the IP layer, direct WireGuard tunnels, no chokepoints, no broadcast noise (unlike ZeroTier's Layer 2 emulated-switch model). ACLs enforce least-privilege reachability for both human and agentic connections (via tsnet).

**What this layer cannot do:** see what happens after a connection is made, govern SaaS OAuth tokens issued directly between browser and app, or inspect endpoint-level behavior.

---

### Identity & Access

The traditional core of IAM — but the agentic era breaks assumptions this layer was built on. Traditional IAM assumed identity = human, sessions are bounded, and accountability is inherent. Agents break all three: they're non-human identities, may run indefinitely, and require explicit audit design to be accountable at all.

Okta's agentic answer: three questions — where are my agents, what can they connect to, what can they do — anchored by discovery, least-privilege access, kill switches, and lifecycle governance.

**ConductorOne vs. Lumos — the closest head-to-head in this layer:** both are fast-deploying, AI-native IGA platforms explicitly governing human, non-human, and AI agent identities, positioned against slow, expensive legacy IGA (SailPoint, Saviynt). ConductorOne's core architecture is a real-time "Unified Identity Graph"; Lumos's is the Albus AI agent doing the analytical work on top of a static visibility layer. Founding pedigree differs too — ConductorOne's CEO ran Okta's own security/PAM product lines before building the disruptor; Lumos's founders came from outside the identity industry entirely. Neither has a clean structural advantage — this is genuinely a two-horse race, decided more by execution and specific integration fit than category positioning.

**The known gap:** Okta, ConductorOne, and Lumos all answer "should this agent be here." None of them answer "does this agent actually understand what it's looking at" (that's Dosu) or "what did this agent actually do, in causal detail" (that's Origin).

---

### Discovery & Context (Data vs. Knowledge)

Two companies solving the structurally identical problem for two different asset types:

| | Cyera | Dosu |
|---|---|---|
| Discovers | Sensitive *data* across cloud, SaaS, on-prem | Project *knowledge* across GitHub repos, issues, docs |
| Answers | "What data do we have, and is it exposed?" | "What does this codebase mean, and is the agent's understanding correct?" |
| Why it matters now | AI agents touching data they shouldn't, or misclassifying sensitivity | AI agents touching codebases they don't understand, hallucinating fixes |

Both are "you can't govern what you haven't discovered and correctly understood" — just applied to different objects.

**Dosu's key nuance:** the core grounding mechanism (indexing real project context to prevent hallucination) is separate from its A2A protocol work (letting other agents query that grounded knowledge). Grounding is the *how*; A2A is the *distribution*.

---

### Detection

Behavioral, cross-domain detection and response. Both Artemis and CrowdStrike belong here — full stop, regardless of deployment mechanism (an endpoint agent is just how the sensor gets deployed, not a separate capability).

| | Artemis | CrowdStrike |
|---|---|---|
| Approach | AI-native rebuild — federated queries, per-org dynamic detection model | Established platform (Falcon), AI (Charlotte) layered on top |
| AI activity visibility | Native to its detection model | Via Claude Compliance API integration — ingests official vendor-reported logs into Falcon Next-Gen SIEM |
| Key limitation | Newer, less proven at massive scale | Depends on vendors choosing to report through compliance channels — doesn't see shadow/unsanctioned agent activity the way Origin's endpoint-native approach does |

**The honest distinction with Origin:** CrowdStrike correlates what AI vendors choose to report. Origin observes what actually happens on the endpoint, independent of whether any vendor reports anything at all.

---

### Telemetry Visualization & Aggregation

Not an identity-native layer — Grafana Labs isn't a security company, it's a general infrastructure observability platform (the LGTM stack: Loki for logs, Grafana for visualization, Tempo for traces, Mimir for metrics). It's placed here because it's a genuinely common destination layer: Detection, Endpoint, and even Identity & Access tooling often pipe their telemetry into a Grafana-style dashboard for human-readable correlation, rather than every layer building its own visualization from scratch.

**Why it's worth tracking in this ecosystem specifically:** Grafana's 2026 roadmap includes expanding its "All-in-One" suite into more advanced SOC/security analytics — a real signal the company is edging toward overlap with the Detection layer, not staying purely infrastructure-focused. Worth revisiting this placement as that expansion matures.

**A live, relevant case study:** Grafana itself suffered a real GitHub breach in May 2026 — a misconfigured GitHub Action (a "Pwn Request" vulnerability) exposed a token that let an attacker download the company's codebase, caught only via an internal canary token. The compromise was later traced to the broader TanStack npm supply chain attack. It's a clean, current illustration of CI/CD pipeline risk — directly relevant to the same governance-gap thread running through this whole ecosystem map, just realized at a company that builds observability tooling rather than identity tooling.

---

### Agent Construction

LangChain builds the orchestration and harness layer that turns a raw model into a working agent — prompts, tools, memory, planning, middleware. This is the "operating system" bet (per NVIDIA's Jensen Huang): most enterprises won't build their own agent orchestration from scratch, they'll build on top of a framework like LangChain.

**Critical distinction:** Agent Construction is explicitly NOT governance. LangChain and its competitors (CrewAI, AutoGen, LlamaIndex) have no native approval gates, policy enforcement, or audit trail before an agent acts on production systems. This is the seam where Identity & Access, Detection, and Hybrid Workforce Observability layers become necessary *alongside* a construction framework, not instead of it.

---

### Endpoint Visibility

Tanium and Ivanti generate state and inventory truth — is the device compliant, what's installed, what changed, who touched it. Query-based, real-time at scale (Tanium's specific historic differentiator), feeding into patch/asset/vulnerability management.

**What this layer cannot do:** explain *why* something happened, trace causal chains, or reason about intent. It can tell you a process ran or a file changed — it cannot tell you what an agent was trying to accomplish or what it read into context before acting.

---

### Hybrid Workforce Observability

Origin's own language, used deliberately as the layer name: observability built for *"a workforce that is part-human and part-machine."*

This is a distinct layer from Endpoint Visibility, not a subset of it. The distinction mirrors the classic **visibility vs. observability** split from monitoring/SRE practice — visibility is state snapshots, observability is causal tracing:

| | Endpoint Visibility (Tanium/Ivanti) | Hybrid Workforce Observability (Origin) |
|---|---|---|
| Question | What's on this machine? | Why did this happen? |
| Data shape | State snapshots, inventory, query results | Causal chain — prompt → reasoning → action → outcome |
| Depth | A process ran, a file changed | Why the agent touched that file, what it was trying to do, what it read into context first |
| Vendor scope | Vendor-agnostic query tool | Vendor-agnostic causal tracer — sees Claude, Cursor, Copilot, ChatGPT, local models, sanctioned or shadow |

**Why this layer is called out specifically:** nobody else operates here with this depth. It sits adjacent to Detection and Identity & Access (an agent's commit identity not matching its SSO identity is a real identity governance signal, surfaced only because Origin sees the endpoint causally) but its core job — reconstructing intent and causality for both human and AI activity — is unique enough to deserve its own layer rather than being folded into Endpoint Visibility or Detection.

---

### Secrets & Credentials / AI Financial Visibility

1Password spans two distinct jobs, worth keeping separate:

| Job | What It Does | Layer |
|---|---|---|
| **Secrets & Credentials** | Vaulting, rotation, NHI governance, SSH key elimination-adjacent capabilities | Secrets & Credentials |
| **AI Spend and Consumption Management** (launched July 14, 2026, public preview) | Tracks AI token spend across Anthropic, Cursor, OpenAI via admin API keys — consumption by vendor, team, user, model, with budget alerts | AI Financial Visibility |

**Critical distinction, in Origin's own words:** *"Token bills tell you what you spent. [We] tell you what you bought."* 1Password's new capability is financial visibility only — it does not trace behavioral causality, what an agent actually did, or why. This is not a knock on the product; it's simply a different layer solving a different pain (budget forecasting vs. causal governance).

---

### Cloud Posture

Wiz and Orca scan cloud environments for misconfigurations, exposed storage, overly permissive IAM policies. Out of scope for Network, Endpoint, or Observability layers entirely — a distinct surface.

---

### IT Workflow Orchestration

ServiceNow doesn't generate ground-truth data — it consumes truth from other layers and turns it into automated workflows and remediation actions.

**Two distinct ServiceNow-adjacent things, not to be confused:**

| | Now Assist AI Agents | ITOM AI Prime powered by Tanium |
|---|---|---|
| What it is | ServiceNow's own native AI agent product | A joint partnership — Tanium's real-time endpoint truth feeds ServiceNow's ITOM workflows for autonomous remediation |
| Ownership | Fully ServiceNow | Tanium (Endpoint Visibility) + ServiceNow (Orchestration), partnered |

The partnership pattern here is the same shape as LangChain: **the orchestration layer needs ground truth from somewhere else to act on.** ServiceNow orchestrates; Tanium (or other endpoint tools) supplies the facts it orchestrates around.

---

## The Governance Gap — The Thread Tying Every Layer Together

Across nearly every layer above, a consistent gap keeps appearing: **agent construction, orchestration, and even detection frequently lack native governance** — pre-action approval gates, policy enforcement, and audit trails before an agent acts.

- LangChain builds powerful agents but doesn't govern them
- Dosu makes agents smarter but doesn't govern them either
- Traditional Endpoint Visibility tools can't explain agent intent at all
- Even Detection tools depend heavily on what gets reported or observed after the fact

**This gap is where Identity & Access (Okta, ConductorOne, Lumos), Hybrid Workforce Observability (Origin), and the emerging agentic governance thinking all converge.** It's also the exact seam explored in the "Agentic vs. Human Identity" POV piece elsewhere in this KB — agents don't decide, they meet conditions, and the risk is unchecked execution of those conditions without enough visibility to catch when they're wrong.

---

## Key Takeaways

- **ZTIA is a layer map, not a company catalog** — the same pain can be solved by different companies, and one company can operate in multiple layers
- **Visibility and observability are not the same thing** — Endpoint Visibility (Tanium, Ivanti) tells you *what* happened; Hybrid Workforce Observability (Origin) tells you *why*
- **Detection is Detection, regardless of deployment mechanism** — CrowdStrike and Artemis are the same layer; an endpoint agent is just how the sensor gets deployed
- **Discovery & Context splits cleanly by asset type** — Cyera for data, Dosu for knowledge, same structural problem
- **Agent Construction is explicitly not governance** — LangChain builds, it doesn't police what it builds
- **Origin's differentiation is real and specific** — vendor-agnostic, causal, covers both human and AI activity, sees shadow agents nobody else can see
- **The governance gap is the connective tissue** — nearly every layer eventually runs into "who approves this, who audits this, who can kill this" — and that gap is where identity security expertise becomes the differentiator
- **ConductorOne and Lumos are the closest head-to-head in Identity & Access** — both AI-native, both fast-deploying, execution and fit decide it more than category positioning
- **Telemetry Visualization (Grafana) sits underneath, not beside, the security-native layers** — it's where other layers' data often gets seen, and it's a live example of CI/CD supply chain risk in its own right (the May 2026 GitHub breach)

---

## Official References

| Source | Link |
|---|---|
| Tailscale — How It Works | https://tailscale.com/blog/how-tailscale-works |
| Okta for AI Agents | https://www.okta.com/blog/2026/04/okta-for-ai-agents/ |
| Artemis Security | https://artemissecurity.com |
| CrowdStrike — Claude Activity Visibility & Monitoring | https://www.crowdstrike.com/en-us/press-releases/crowdstrike-delivers-visibility-and-monitoring-for-claude-activity/ |
| LangChain | https://www.langchain.com |
| Dosu | https://www.dosu.dev |
| Origin | https://www.originhq.com |
| 1Password — AI Spend and Consumption Management | https://1password.com/press/2026/july/1password-introduces-ai-spend-and-consumption-management |
| Tanium & ServiceNow — ITOM AI Prime Partnership | https://www.businesswire.com/news/home/20260506341909/en/Tanium-Combines-Forces-with-ServiceNow-to-Deliver-New-Autonomous-IT-Solution-Powered-by-Industry-Leading-Platforms |
| ConductorOne | https://www.conductorone.com |
| Grafana Labs | https://grafana.com |
| Grafana Labs — GitHub Breach Coverage | https://www.securityweek.com/grafana-confirms-breach-after-hackers-claim-they-stole-data/ |
