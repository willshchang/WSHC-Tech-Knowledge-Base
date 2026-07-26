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

### The Pivot: Endpoint AI Observability (Origin, 2026)

Origin represents a full repositioning: rather than general endpoint protection, the company now focuses specifically on **observing what AI agents do on employee endpoints.**

> "Origin is building the endpoint AI observability platform for AI-adopting organizations. We believe that organizations should not adopt AI on their endpoints without observability in place."

This is a sharp, well-timed pivot. As AI coding agents and browser copilots became standard tools running directly on employee machines throughout 2025–2026, a structural gap emerged: traditional Endpoint Detection and Response (EDR) was built around a single assumption — a human sits at a keyboard, and malicious activity looks different from normal activity. AI agents break that assumption completely.

---

## What Origin Actually Does

### The Core Problem: EDR Wasn't Built for Agents

Origin's own framing of the gap is precise and worth understanding directly:

> "EDR records that a process spawned a child process. It does not record that an AI agent chose to refactor authentication middleware, read .env files, and triggered a network call to an unfamiliar endpoint. The causal chain, the why, is missing."

Traditional EDR heuristics turn into noise when an AI agent is doing legitimate work — reading files, writing code, spawning processes, opening connections are all *normal* agent behavior, not necessarily suspicious activity. What's missing is intent and causality, not just event logging.

### How the Platform Works

| Capability | Description |
|---|---|
| **Discover shadow agents** | Detects new coding agents, browser copilots, and local tools the moment they appear on a machine — even ones IT has never approved or seen |
| **Intercept at the TLS layer** | Captures AI traffic with process attribution — tied to the specific process and user, not just network-level metadata |
| **Extract full session content** | Pulls prompts, responses, and tool calls out of every AI session |
| **Correlate intent to action** | Ties the original prompt to files touched, commands executed, services accessed, and final outcome — the full causal chain |
| **Map prompts to actions** | Follows a delegated task end-to-end: prompt → file reads → command execution → service access → outcome |
| **See local context before the wire** | Understands which files, credentials, and local artifacts an agent pulled into context *before* anything left the endpoint |
| **Spot behavioral drift** | Flags when an agent moves from expected work into unrelated systems, topics, or workflows — before it becomes a scattered mess of disconnected logs |

### Real Examples From Their Own Product Marketing

These are illustrative of exactly what the platform surfaces in practice:

- **Secrets exposure in AI sessions:** "Someone just pasted a .env file into an AI debugging session. Not intentionally. Just the usual 'here's my config, why won't this connect?' moment, complete with keys, tokens, passwords, and connection strings."
- **Identity mismatch detection:** "9 active agent ↔ GitHub auth pairs where the agent's commit identity doesn't match the SSO identity. All on Engineering machines." — this is a direct identity governance signal, surfaced at the endpoint layer, not the IAM layer
- **Shadow agent discovery:** "214 first-time agent installs this week. 18 are personal / unsanctioned. 196 came through the standard install path; the rest were side-loaded."
- **Spend attribution:** "Token bills tell you what you spent. Origin tells you what you bought." — clusters AI conversations by topic, team, and initiative so spend becomes legible to whoever approved the budget

### Deployment Model

- Installs directly on the endpoint (laptop/workstation) — described as a 5-minute install
- Free tier available for individual visibility (see every AI agent on your own machine)
- Listed in the Anthropic Connectors Directory — meaning Claude itself can query Origin's data directly (e.g., asking Claude which projects are driving token spend, which unsanctioned agents are running, what happened in a specific anomalous session)

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
| **Identity** | The agent-vs-SSO commit identity mismatch example is a genuine identity governance signal — Origin is catching an access/identity problem that a pure IAM tool (Okta, Lumos, ConductorOne) would have no visibility into, because it happens at the endpoint before or alongside the identity layer's own logging |

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

---

## Personal Relevance — Why This Space Fits Will's Background

This is a direct, structural match to hands-on endpoint management experience:

- The core mechanism — device-level visibility, compliance posture, catching misconfigurations or unexpected behavior at the endpoint — is the same fundamental skill set as MDM work (Workspace ONE/Omnissa, Intune, Jamf), just applied to a new class of "user": AI agents instead of human employees
- The identity-mismatch example (agent commit identity ≠ SSO identity) is conceptually identical to catching a device out of compliance or a user session behaving unexpectedly — same pattern-recognition instinct, new object of observation
- Origin's own framing — "the causal chain, the why, is missing" from traditional EDR — is exactly the kind of gap that rewards someone who has spent years translating raw technical signals (compliance errors, ticket patterns) into root cause and proactive action, rather than someone purely building detection rules from a security engineering background

---

## Key Takeaways

- **Origin is a rebrand and full repositioning of Prelude Security** (2020–2025), pivoting from general continuous security testing / runtime memory protection into a focused bet on **endpoint AI observability**
- **The core insight:** traditional EDR was built assuming a human at the keyboard — AI agents break that assumption, leaving a causal-chain gap (the "why") that Origin is built to fill
- **The product traces the full chain** — prompt → reasoning → files touched → commands run → network calls → outcome — attributed to user, agent, and process
- **Origin is genuinely multi-layer** — Endpoint is the primary surface, but it surfaces real Detection and Identity governance signals other tools structurally cannot see from their own vantage point
- **Small, not widely known yet** — genuinely early enough that being one of the first people in a target company's network with a clear grasp of the space is a real advantage
- **Direct personal fit** — endpoint visibility and compliance pattern-recognition instincts translate almost directly onto this product category, just applied to agents instead of human end users

---

## Official References

| Source | Link |
|---|---|
| Origin official site | https://www.originhq.com |
| Origin — Approach / Product | https://www.originhq.com/approach |
| Origin — Vision | https://www.originhq.com/vision |
| Origin — Prelude Security Rebrand Notice | https://www.originhq.com/preludesecurity |
| Origin Blog | https://www.originhq.com/blog |
| Prelude Security — $16M Investment Announcement (Sept 2025) | https://www.businesswire.com/news/home/20250925489179/en/Prelude-Security-Announces-Additional-$16M-Investment-Led-by-Brightmind-Partners-Along-With-Sequoia-Capital-and-Insight-Partners-To-Build-the-Next-Generation-of-Endpoint-Security |
| Prelude — Company & Funding Profile | https://startupintros.com/orgs/prelude |
