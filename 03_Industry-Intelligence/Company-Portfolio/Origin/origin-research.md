# Origin — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  
**Official Reference:** https://www.originhq.com  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Founded** | 2020 (as Prelude Security) |
| **Rebranded** | 2026 — Prelude Security → Origin (legal entity: Prelude Research, Inc., d/b/a Origin Technology) |
| **HQ** | New York, NY |
| **Total funding (as Prelude)** | $70M raised across 6 rounds |
| **Notable investors** | Sequoia Capital, Brightmind Partners, Insight Partners, IA Ventures |
| **Category** | Endpoint AI observability |
| **Website** | https://www.originhq.com |

---

## Founders

### Spencer Thompson — Co-Founder & CEO

- Serial entrepreneur, previously founded Sokanu
- Led Prelude's original positioning around continuous, offensive-informed security testing before the pivot to AI observability

### David Hunt — Co-Founder & CTO

- Former security consultant for a U.S. government contractor
- Combined offensive security testing and endpoint security expertise with Thompson to found Prelude in 2020

---

## The Company's Evolution: From Prelude Security to Origin

### Original Product (Prelude Security, 2020–2025)

Prelude began as a **continuous security testing / adversary emulation platform** — letting organizations continuously validate their defenses by running ongoing assessments against their own systems, rather than relying on periodic pen tests.

In September 2025, Prelude raised $16M (bringing total funding to $45M) specifically to commercialize **runtime memory protection** — technology designed to detect and stop malicious code at the moment of execution, targeting the growing category of in-memory attacks that evade traditional file- and behavior-based detection (approximately 75% of advanced cyberattacks now operate exclusively in-memory, per the company's own framing at the time).

### The Pivot: Endpoint AI Observability (Origin, July 2026)

This was not a soft rebrand — it was a **full company refocus**. Per the CEO's own July 27, 2026 announcement, Prelude Security is being wound down entirely: existing customers are honored through the remainder of their current contracts, with the company hoping to migrate many of them to Origin, but the company's full attention moves to Origin exclusively.

**How they got there, in their own account:** offensive testing work at Prelude repeatedly showed endpoint-focused attack techniques succeeding — not from a single missing signature, but from structural limitations in how endpoint defenses were designed. That led to three conclusions that became Origin's founding architecture:

1. The future of endpoint technology will increasingly run in **user mode rather than depending on invasive kernel architectures**
2. **Signatures and known-malicious-pattern detection** will become less effective as AI produces novel, contextual, highly variable behavior
3. The next generation of endpoint security will be built around **trace-driven observability**

**A real technical credential worth noting:** the team wrote the definitive published technical book on EDR evasion (No Starch Press, *"Evading EDR"*) — meaning the pivot to observability-first architecture is grounded in genuine, published expertise on exactly how traditional endpoint defenses fail, not a marketing repositioning.

> "Origin is building the endpoint AI observability platform for AI-adopting organizations. We believe that organizations should not adopt AI on their endpoints without observability in place."

This is a sharp, well-timed pivot. As AI coding agents and browser copilots became standard tools running directly on employee machines throughout 2025–2026, a structural gap emerged: traditional Endpoint Detection and Response (EDR) was built around a single assumption — a human sits at a keyboard, and malicious activity looks different from normal activity. AI agents break that assumption completely.

---

## Third-Party Validation — The SACR Endpoint Market Map

On July 22, 2026, independent analyst firm **Software Analyst Cyber Research (SACR)** published a market map of the Endpoint Control and Prevention category — five zones covering the vendors securing the layer where AI agents now do real work. This is genuine third-party category placement, not Origin's own self-description.

**Origin was placed in Zone 3: "agent runtime observability"** — the zone answering what an agent actually did, distinct from Zone 1-2 (software posture, prevention) and covering the same territory Origin's own "Hybrid Workforce Observability" framing describes elsewhere in this KB.

**A specific quote worth remembering, sourced from a Brightmind Partners LinkedIn post referencing the report:** SACR called Origin **"the most technically differentiated Zone 3 vendor in the market,"** citing patented CPU-level telemetry, a local graph database running on every endpoint, and full prompt-to-action lineage for AI agent activity — architecturally notable specifically because it requires **no kernel driver and no cloud round trips**, a direct technical consequence of the user-mode design philosophy described above.

---

## What Origin Actually Does

### The Core Problem: EDR Wasn't Built for Agents

Origin's own framing of the gap is precise and worth understanding directly:

> "EDR records that a process spawned a child process. It does not record that an AI agent chose to refactor authentication middleware, read .env files, and triggered a network call to an unfamiliar endpoint. The causal chain, the why, is missing."

Traditional EDR heuristics turn into noise when an AI agent is doing legitimate work — reading files, writing code, spawning processes, opening connections are all *normal* agent behavior, not necessarily suspicious activity. What's missing is intent and causality, not just event logging.

### The Platform Has Three Solutions, One Underlying Data Layer

Origin's own product site organizes around three named solutions — Governance, Adoption, and Investment (marketed as "Spend") — all built on the same core capture layer: a user-mode sensor recording the full local trace of every agent action at the endpoint (prompt → tool call → file touched → network call → outcome), attributed to user, agent, and process.

#### 1. Governance — "What are they doing?"

Framework: **Discover → Detect → Investigate → Prove**

| Step | What It Does |
|---|---|
| **Discover** | Builds a live inventory of every AI tool, agent, model, and MCP server across endpoints — who's using them, what they can access, where unapproved technology creates exposure |
| **Detect** | Continuously analyzes activity for exposed credentials, sensitive files, destructive commands, and other patterns needing investigation |
| **Investigate** | Reconstructs the full chain from prompt to action — the exact prompt, the model's reasoning, the tool call, the file touched, the network call, the resulting action |
| **Prove** | Keeps a searchable, role-based-access-controlled record of activity and investigation evidence — audit-ready by default |

**A real cited stat:** enterprise teams uncover **3x more AI activity than their existing IT inventories show** once they deploy Origin.

**A concrete detection example, straight from their own product demo data:** a "credential material in prompt or tool output" signal flags API keys, tokens, private keys, and connection strings appearing in prompt text — values redacted before tagging, so the signal itself doesn't create new exposure.

#### 2. Adoption — "How is AI actually being used?"

Framework: **Map → Track → Watch → Reuse**

| Step | What It Does |
|---|---|
| **Map** | Organizes AI activity by team, project, topic, and workflow — is AI supporting product development, research, customer work, operations, sales? |
| **Track** | Identifies repeated work and emerging patterns — where teams are solving the same problem more than once without knowing it |
| **Watch** | Follows which workflows become part of daily work and where AI usage is gaining or losing ground over time |
| **Reuse** | Captures the artifact and context behind successful AI work — "the same work, done more than once, drafted into a skill the next person can run" |

**Why this matters — the direct Mimica.ai overlap:** this is genuinely task/process mining, just AI-scoped rather than all-desktop-activity-scoped. Where a tool like Mimica.ai mines *raw* desktop activity (any app, human-driven) to recommend *new* automation opportunities (RPA/IDP/GenAI) where none exists, Origin's Adoption solution mines *AI agent activity specifically* to find where AI-driven automation is *already happening organically* and help it spread and standardize into a reusable "skill." Different starting points, structurally similar end goal — turning observed repeated work into a codified, reusable process.

#### 3. Investment / Spend — "Where is our intelligence going?"

Origin's own internal name for this is **"Intelligence Allocation."** Framework: **Observe → Attribute → Optimize → Prove**

| Step | What It Does |
|---|---|
| **Observe** | Tracks usage and estimated cost across prompts, sessions, models, providers, tools, agents, and employees |
| **Attribute** | Clusters AI activity by team, topic, and workflow — spend arrives already grouped by what it actually bought, not just a vendor line item |
| **Optimize** | Surfaces where frontier (expensive) models are the default for routine work a cheaper model could handle identically, and where the same problem is being solved redundantly |
| **Prove** | Answers what was spent, where it went, and what it produced — pull requests opened, reviews completed, clusters of work, endpoints active |

**A real, specific, quotable customer result:** *"Origin turned our token telemetry into a savings plan. It showed what was driving the bill, and found savings without moving important work to weaker models."* — **$250K found in savings on a $1M annual AI bill.**

> "Token bills tell you what you spent. Origin tells you what you bought."

### Deployment Model

- Installs directly on the endpoint (laptop/workstation) — described as a 5-minute install
- Free tier available for individual visibility (see every AI agent on your own machine)
- Listed in the Anthropic Connectors Directory — meaning Claude itself can query Origin's data directly (e.g., asking Claude which projects are driving token spend, which unsanctioned agents are running, what happened in a specific anomalous session)
- AI usage is also exposed through Origin's own MCP server, so any agent already running in an environment can query the aggregated data directly — not just a human dashboard user

---

## The Company's Stated Vision

Origin's own positioning is explicit about not being "just another detection tool":

> "Not another detection tool tuned for human adversaries. An observability layer purpose-built for a workforce that is part-human and part-machine. We provide endpoint-native visibility into what agents exist, what they're doing, what they have access to, and whether their behavior looks like what you'd expect."

Their thesis: the CISO role is shifting from being primarily about adversaries to being about **safety architecture for a hybrid human/machine workforce** — baselining what "normal" agent behavior looks like so that deviation is visible before it becomes an incident, rather than after.

---

## Why This Is a Multi-Layer Company — Not Just "Endpoint"

Origin is a strong example of why organizing the ecosystem by **layer/pain solved** rather than by company category matters. On the surface, Origin looks like a pure Endpoint play. In practice, it operates across three layers simultaneously:

| Layer | How Origin Shows Up There |
|---|---|
| **Endpoint** | Primary surface — the sensor lives on the device, observes agents at the OS/process level |
| **Detection** | Behavioral drift detection, anomalous session flagging — functionally adjacent to what Artemis does at the cross-environment level, but Origin's vantage point is endpoint-native rather than aggregated across cloud/identity/network |
| **Identity** | The agent-vs-SSO commit identity mismatch example is a genuine identity governance signal — Origin is catching an access/identity problem that a pure IAM tool (Okta, Lumos, C1) would have no visibility into, because it happens at the endpoint before or alongside the identity layer's own logging |

This mirrors the same insight from the Dosu/Cyera comparison: **the interesting companies right now are rarely staying inside one clean product category.** Origin's endpoint vantage point gives it visibility other layers structurally can't get — it sees the *local* context (files, credentials, artifacts) before anything leaves the machine, which is something network-layer or cloud-layer tools cannot observe by design.

---

## Origin-Overpower: What Origin Adds on Top of Every ZTIA Layer

This section makes the strongest, most specific case for Origin's differentiation — not by replacing any layer, but by showing what each layer *cannot* see that Origin can. Origin doesn't compete with any single layer below; it sits underneath all of them, seeing the ground truth every other layer has to infer or go without.

| ZTIA Layer | What That Layer Already Does | What Origin Adds That Layer Cannot See |
|---|---|---|
| **Network** | Controls what can reach what — identity-verified connectivity, segmentation | Network tools see *that* a connection happened. Origin sees *why* — what prompted the agent to make that network call, what local file or credential it read into context first |
| **Identity & Access** | Governs whether an identity should be here — SSO, lifecycle, entitlement reviews | IAM tools trust that the identity making a request is who it claims to be. Origin catches the mismatch — an agent's commit identity not matching its SSO identity — a signal IAM tools have no visibility into because it happens at the endpoint, not the directory |
| **Discovery & Context — Data** (Cyera) | Discovers and classifies sensitive data across cloud, SaaS, on-prem | Cyera sees where data lives. Origin sees the moment a human or agent pastes that data into an AI session — the exact instant of exposure, before it becomes a data-at-rest problem anyone else can find |
| **Discovery & Context — Knowledge** (Dosu) | Grounds AI answers in real project context to prevent hallucination | Dosu ensures the agent understands the codebase correctly. Origin proves what the agent *actually did* with that understanding — the causal chain from correct (or incorrect) comprehension to real-world action |
| **Detection** (Artemis, CrowdStrike) | Correlates behavioral signals across environments into attack narratives | Detection tools work from what gets reported or logged. CrowdStrike's AI visibility depends on vendors choosing to expose activity via compliance APIs. Origin sees every agent regardless of vendor cooperation — including shadow agents nobody approved and nobody is reporting on |
| **Agent Construction** (LangChain) | Builds the orchestration and harness layer that makes an agent function | LangChain has no visibility into what happens after deployment. Origin is the only layer that observes the actual runtime behavior of anything LangChain builds, once it's running on a real endpoint |
| **Endpoint Visibility** (Tanium, Ivanti) | Tells you what's installed, whether it's compliant, what changed | This is the closest adjacent layer — and the difference is the whole point. Tanium/Ivanti give you state. Origin gives you causality. "A process ran" vs. "the agent chose to refactor authentication middleware, read .env files, and called an unfamiliar endpoint — and here's why" |
| **Secrets & Credentials** (1Password) | Vaults and rotates secrets, governs NHI credentials | 1Password protects secrets that are stored correctly. Origin catches the secret that was never supposed to leave the vault in the first place — pasted into a debug session, in plain text, mid-conversation |
| **AI Financial Visibility** (1Password AI Spend) | Tracks token spend by vendor, team, user, model | Spend tracking tells you the bill. Origin tells you what you bought — which specific agent action, on whose machine, produced that cost |
| **Cloud Posture** (Wiz, Orca) | Scans cloud environments for misconfiguration and exposure | Out of scope for Origin directly — but the *agents* that might introduce a cloud misconfiguration through automated actions are exactly what Origin is watching at the point of action, before the misconfiguration ever reaches the cloud layer for Wiz/Orca to find |
| **IT Workflow Orchestration** (ServiceNow) | Orchestrates automated remediation workflows from ground-truth data | ServiceNow acts on data fed to it. Origin is a candidate ground-truth source ServiceNow doesn't currently have — agent behavioral causality, not just endpoint compliance state |

**The pattern across every row:** every other layer either sees *state* (what exists, what's configured, what's compliant) or *reported activity* (what a vendor chose to log). Origin is the only layer that sees **intent and causality** — the actual reasoning chain connecting a prompt to a real-world action, on the actual device, regardless of which vendor or tool was involved.

> This is not a claim that Origin replaces any layer above. It's the opposite: every layer above becomes more effective with Origin's causal ground truth feeding into it — better Detection correlation, more precise Identity governance, faster root cause for Endpoint Visibility tools. Origin is infrastructure underneath the stack, not a layer competing within it.

**One genuine, direct overlap worth naming precisely — C1's Shadow AI Discovery:** C1 (formerly ConductorOne) launched endpoint scanning for local MCP configs, unsanctioned copilots, and plaintext credentials in July 2026 — nearly identical surface area to Origin's own core discovery claim. Where they diverge is what happens next: C1 turns a discovery into a governed access item (owner, review, deprovisioning). Origin turns it into a causal explanation (why did this happen, what was the intent). See `c1-research.md` for the full mechanism-level comparison — the honest read is that they're complementary more than competing in a mature stack, since C1 explicitly supports ingesting third-party causal findings via API.

---

## Watch This Space: Kernels, Canvases, and the OpenWiki Question

Origin posted a product demo (undated in this doc, no corresponding blog post found as of writing) describing a new capability:

> "You can run a query, save its logic as a kernel, add the results to a canvas, then keep it on hand as your data evolves... Canvases and kernels are stored in the cloud and shareable across your Origin tenant so you can build the analysis once and let the rest of the organization work from it."

**What this is today, as described:** a saved, reusable query (a "kernel") whose output persists on a shared, cloud-stored view (a "canvas") that stays current as underlying data changes — closer to a living saved search or a persistent Grafana panel than a knowledge base. Built for a human or team to keep checking, not (yet) for another system to consume as context.

**Why it's worth watching:** the distinction between "a saved search" and "an OpenWiki-style knowledge layer" isn't really about the saving mechanism — it's about what consumes the output. A saved search stays a saved search as long as a human is the one reading the canvas. It becomes something closer to LangChain's OpenWiki (a living, structured knowledge artifact an AI agent reads as grounding context, auto-updated as the underlying system changes) the moment an agent — Origin's own, or a customer's — starts consuming canvas output as context for its own reasoning, rather than a human glancing at a dashboard.

**The natural next step, if Origin goes this direction:** given Origin's own trajectory (endpoint observability → causal tracing → almost certainly its own agent for querying/summarizing findings eventually), kernels and canvases are well-positioned to become exactly that — a persistent, evolving, agent-consumable knowledge layer about an organization's own AI/endpoint activity, not just a dashboard. Worth revisiting this section once Origin ships an agent of its own, or once canvas output shows up as a documented input to any AI-consuming feature.

---

This is a direct, structural match to hands-on endpoint management experience:

- The core mechanism — device-level visibility, compliance posture, catching misconfigurations or unexpected behavior at the endpoint — is the same fundamental skill set as MDM work (Workspace ONE/Omnissa, Intune, Jamf), just applied to a new class of "user": AI agents instead of human employees
- The identity-mismatch example (agent commit identity ≠ SSO identity) is conceptually identical to catching a device out of compliance or a user session behaving unexpectedly — same pattern-recognition instinct, new object of observation
- Origin's own framing — "the causal chain, the why, is missing" from traditional EDR — is exactly the kind of gap that rewards someone who has spent years translating raw technical signals (compliance errors, ticket patterns) into root cause and proactive action, rather than someone purely building detection rules from a security engineering background

---

## Key Takeaways

- **Origin is a full company refocus, not a soft rebrand** — Prelude Security is being wound down entirely as of July 2026, with the company going all-in on Origin
- **The core insight:** traditional EDR was built assuming a human at the keyboard — AI agents break that assumption, leaving a causal-chain gap (the "why") that Origin is built to fill
- **The product traces the full chain** — prompt → reasoning → files touched → commands run → network calls → outcome — attributed to user, agent, and process, organized into three named solutions (Governance, Adoption, Investment) on one shared data layer
- **Third-party validation is real, not just self-description** — independent analyst firm SACR placed Origin in Zone 3 of its endpoint market map and called it "the most technically differentiated Zone 3 vendor in the market"
- **The Adoption solution has a genuine, specific overlap with Mimica.ai** — both are task/process mining tools; Origin is scoped to AI-mediated activity specifically and captures organically-emerging automation rather than recommending net-new automation from scratch
- **Origin is genuinely multi-layer** — Endpoint is the primary surface, but it surfaces real Detection and Identity governance signals other tools structurally cannot see from their own vantage point
- **Direct personal fit** — endpoint visibility and compliance pattern-recognition instincts translate almost directly onto this product category, just applied to agents instead of human end users

---

## Official References

| Source | Link |
|---|---|
| Origin official site | https://www.originhq.com |
| Origin — Governance Solution | https://www.originhq.com/solutions/ai-governance |
| Origin — Adoption Solution | https://www.originhq.com/solutions/ai-adoption |
| Origin — Investment/Spend Solution | https://www.originhq.com/solutions/ai-spend |
| Origin — Prelude Security Rebrand Notice | https://www.originhq.com/preludesecurity |
| Origin Blog — Prelude is now Origin | https://www.originhq.com/blog/prelude-is-now-origin |
| Origin Blog — SACR Maps Endpoint Observability | https://www.originhq.com/blog/sacr-maps-endpoint-observability |
| Origin Blog | https://www.originhq.com/blog |
| Prelude Security — $16M Investment Announcement (Sept 2025) | https://www.businesswire.com/news/home/20250925489179/en/Prelude-Security-Announces-Additional-$16M-Investment-Led-by-Brightmind-Partners-Along-With-Sequoia-Capital-and-Insight-Partners-To-Build-the-Next-Generation-of-Endpoint-Security |
| Prelude — Company & Funding Profile | https://startupintros.com/orgs/prelude |
