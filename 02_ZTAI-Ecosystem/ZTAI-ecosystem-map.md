# ZTAI Ecosystem Map: Zero Trust AI, Layer by Layer

**Document Type:** Knowledge Article / Interview Reference — Core Framework  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** September 2026  

---

## The Core Thesis

Modern enterprise security isn't one product category — it's a stack of distinct layers, each solving a specific pain, each owned by different companies (sometimes the same company operating in more than one layer at once).

**Zero Trust AI (ZTAI)** is the umbrella framework for organizing this stack. Originally built as ZTIA — Zero Trust Identity Access — the frame has evolved as the portfolio grew: identity was never the whole problem, just the first and most obvious layer of it. Grafana, Cribl, Cortex, and Lemma were never identity plays, and folding them in was correct — they're all genuinely part of the same underlying AI-era infrastructure problem. The name needed to catch up to what the map already was.

**"AI" here carries a deliberate double meaning** — **Artificial Intelligence** (the models, the agents, the tools) and **Agentic Infrastructure** (the plumbing, governance, and connective tissue that lets those agents operate safely at all). Both readings are correct simultaneously; that's the point.

ZTAI answers three questions for any company, product, or capability:

1. **What pain does this actually solve?**
2. **What layer of the stack does it operate at?**
3. **What can it not do — and who fills that gap?**

This isn't a product catalog. A catalog lists what companies sell. An ecosystem map diagnoses what pain exists and who's actually solving each piece of it — including the reality that one company can show up in more than one layer, and that some layers currently have real, unfilled gaps.

---

## Cross-Cutting Threads Worth Their Own Read

Four pieces of analysis cut across every layer below rather than belonging to any single one — all live as standalone docs so they can keep growing on their own:

- **[Agentic Reliability](agentic-reliability.md)** — the layer where "is the new AI workforce doing quality work without going rogue" gets asked most directly, plus the broader thesis that none of this is a new problem, just an old organizational discipline (role definition, data hygiene) applied to a workforce that doesn't sleep
- **[Platformization](platformization.md)** — the pattern of companies consolidating multiple layers under one platform rather than staying single-purpose, and the honest tradeoffs (lock-in, acquisition promises not always kept) that come with it
- **[Practical Observability](practical-observability.md)** — my own position that observability without a downstream purpose is just data; the false-observability problem (piecing logs back together after the fact isn't the same as continuous state reconstruction); and why some companies (Rootly, C1) are closing the loop while others (Origin, Cribl) are betting their data alone is defensible enough to stay standalone
- **[Agentic vs. Human Identity Governance](agentic-vs-human-identity-governance.md)** — my own position that agents don't decide, they meet conditions, and the real risk is unchecked execution of those conditions without enough visibility to catch when they're wrong

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
| **Network** | What can reach what? | [Tailscale](../03_Industry-Intelligence/Company-Portfolio/Tailscale/tailscale-research.md), Twingate, ZeroTier, Palo Alto Networks (Strata) | Network-as-gate — identity-verified connectivity, segmentation, least-privilege reachability. Palo Alto's Strata is the traditional enterprise NGFW/SASE incumbent, one piece of a genuinely multi-layer platform |
| **Identity & Access** | Should this identity (human or agent) be here? | [Okta](../03_Industry-Intelligence/Company-Portfolio/Okta/okta-research.md), Microsoft Entra ID, [C1 (formerly ConductorOne)](../03_Industry-Intelligence/Company-Portfolio/C1/c1-research.md), [Lumos](../03_Industry-Intelligence/Company-Portfolio/Lumos/lumos-research.md), [WorkOS](../03_Industry-Intelligence/Company-Portfolio/WorkOS/workos-research.md) | Access governance, SSO, lifecycle management, entitlement reviews. C1 has expanded well beyond this single layer since July 2026 — see deep dive. WorkOS occupies the B2B-developer-infrastructure sub-niche, with Airlock pushing into Agent Runtime Governance territory |
| **Discovery & Context — Data** | Do we know what sensitive data we have, and is it exposed? | [Cyera](../03_Industry-Intelligence/Company-Portfolio/Cyera/cyera-research.md) | DSPM — discovery, classification, risk scoring for data |
| **Discovery & Context — Knowledge** | Does this agent actually understand what it's looking at? | [Dosu](../03_Industry-Intelligence/Company-Portfolio/Dosu/dosu-research.md) | Grounds AI answers in real project context to prevent hallucination |
| **Detection** | Is something behaving wrong right now? | [Artemis](../03_Industry-Intelligence/Company-Portfolio/Artemis/artemis-security-research.md), CrowdStrike, Splunk, SentinelOne, [Elastic Security](../03_Industry-Intelligence/Company-Portfolio/Elastic/elastic-research.md), [Palo Alto Networks (Cortex)](../03_Industry-Intelligence/Company-Portfolio/Palo-Alto-Networks/palo-alto-networks-research.md) | Cross-domain behavioral detection and response — this is the job, regardless of deployment mechanism. Splunk is the dominant legacy SIEM every AI-native player positions against; SentinelOne is one of three EDR vendors now acquiring pipeline tooling directly (see Data Pipeline & Routing). Elastic's real differentiator is architectural (no per-byte indexing tax); Palo Alto's Cortex is one piece of a genuinely multi-layer platform |
| **Telemetry Visualization & Aggregation** | Can we see and correlate signals across metrics, logs, and traces in one place? | Grafana Labs (LGTM stack), [Elastic Observability](../03_Industry-Intelligence/Company-Portfolio/Elastic/elastic-research.md) | General infrastructure observability, not identity-native — the layer other layers' data often gets visualized through; edging toward Detection as it adds SOC/security analytics capability. Elastic runs Observability and Security on one shared underlying platform, a genuine Platformization example |
| **Data Pipeline & Routing** | How does telemetry actually get from every source to every destination, in a usable shape? | [Cribl](../03_Industry-Intelligence/Company-Portfolio/Cribl/cribl-research.md) | The pipe, not the destination — sits upstream of Telemetry Visualization, Detection, and every other layer that consumes telemetry. Vendor-neutral by design, though EDR vendors are increasingly acquiring competing pipeline tools to reduce dependency on neutral players |
| **Routing** | Which AI model should actually handle this request, and at what cost? | [OpenRouter](../03_Industry-Intelligence/Company-Portfolio/OpenRouter/openrouter-research.md) | A different object entirely from Data Pipeline & Routing — this routes live AI inference requests (cost/latency/quality optimization), not observability telemetry. Also distinct from Aperture/C1's AI gateways, which answer "is this traffic authorized," not "which model handles it best" |
| **Agent Construction** | How do we build the agent in the first place? | [LangChain](../03_Industry-Intelligence/Company-Portfolio/LangChain/langchain-research.md) | Orchestration/development layer — the raw material other layers react to. Explicitly does NOT govern what it builds |
| **Endpoint Visibility** | What's on this machine, is it compliant, what changed? | Tanium, Ivanti, [Axonius](../03_Industry-Intelligence/Company-Portfolio/Axonius/axonius-research.md) | State snapshots, inventory, query-based — tells you *that* something happened, not *why*. Axonius's actual scope extends beyond pure endpoint into full asset attack-surface visibility (CAASM) — devices, SaaS, cloud, identity, and OT/IoT |
| **Hybrid Workforce Observability** | Why did this happen — what did a human or AI agent actually do, step by step? | [Origin](../03_Industry-Intelligence/Company-Portfolio/Origin/origin-research.md) | Vendor-agnostic causal tracing (prompt → reasoning → action → outcome) across both human and AI activity — the layer nobody else operates at with this depth |
| **Agentic Reliability — Visibility** | Do we have an accurate, standards-scored inventory of our engineering services and assets? | [Cortex](../03_Industry-Intelligence/Company-Portfolio/Cortex/cortex-research.md) | Catalog + score + guided remediation for software services, APIs, and ML models — same function as Endpoint Visibility (Tanium/Ivanti), just applied to engineering assets instead of devices |
| **Agentic Reliability — Observability** | Is my own shipped AI agent product actually working correctly in production? | [Lemma](../03_Industry-Intelligence/Company-Portfolio/Lemma/lemma-research.md) | Causal trace-based detection of silent semantic failures in a company's own deployed agent, with automated remediation (PR/API) closing the loop |
| **Secrets & Credentials** | Are secrets and non-human credentials protected? | [1Password](../03_Industry-Intelligence/Company-Portfolio/1Password/1password-research.md), HashiCorp Vault, C1 (Agentic Vault), [CyberArk](../03_Industry-Intelligence/Company-Portfolio/CyberArk/cyberark-research.md), [BeyondTrust](../03_Industry-Intelligence/Company-Portfolio/BeyondTrust/beyondtrust-research.md) | Vaulting, rotation, NHI governance. CyberArk pioneered the category (1999), now part of Palo Alto Networks; BeyondTrust is the #2 incumbent. C1's Agentic Vault (July 2026) is a genuine new entrant using workload federation instead of credential delivery |
| **AI Financial Visibility** | What are we actually spending on AI, and by whom? | [1Password](../03_Industry-Intelligence/Company-Portfolio/1Password/1password-research.md) (AI Spend and Consumption Management) | Financial/spend visibility ONLY — explicitly not behavioral or causal. "Token bills tell you what you spent. [Hybrid Workforce Observability] tells you what you bought." |
| **Cloud Posture** | Is our cloud environment misconfigured or exposed? | Wiz, Orca, [Palo Alto Networks (Cortex Cloud)](../03_Industry-Intelligence/Company-Portfolio/Palo-Alto-Networks/palo-alto-networks-research.md) | CSPM — scans cloud resource configs for exposure. Cortex Cloud (formerly Prisma Cloud, merged Feb 2025) processes an estimated 1 trillion events every 24 hours |
| **IT Workflow Orchestration** | How do we turn ground-truth data into automated action? | ServiceNow (Now Assist AI Agents; also ITOM AI Prime powered by Tanium), [Rootly](../03_Industry-Intelligence/Company-Portfolio/Rootly/rootly-research.md) | Consumes endpoint/data truth from other layers, orchestrates workflows and remediation on top of it — does not generate the ground truth itself. Rootly's core business is here (on-call/incident automation), with its ThinkHive acquisition also pushing it into Agentic Reliability |

---

## Layer Deep Dives

### Network

Network-as-gate, not network-as-sensor. Encryption has made deep packet inspection largely obsolete, but controlling *what can reach what* is more important than ever in a Zero Trust world.

Tailscale's specific differentiator: identity-first mesh networking at the IP layer, direct WireGuard tunnels, no chokepoints, no broadcast noise (unlike ZeroTier's Layer 2 emulated-switch model). ACLs enforce least-privilege reachability for both human and agentic connections (via tsnet).

**What this layer cannot do:** see what happens after a connection is made, govern SaaS OAuth tokens issued directly between browser and app, or inspect endpoint-level behavior.

**Aperture vs. C1's identity-layer approach:** Tailscale's Aperture gateway and C1's Agentic Vault/Runtime Governance both replace raw API keys with identity for AI/LLM traffic — same philosophy, opposite ends of the stack (network vs. identity platform). Not real substitutes; more a sign the industry is converging on "identity replaces secrets" independently. Full comparison in [tailscale-research.md](../03_Industry-Intelligence/Company-Portfolio/Tailscale/tailscale-research.md) and [c1-research.md](../03_Industry-Intelligence/Company-Portfolio/C1/c1-research.md).

**Tailscale's first-ever acquisition — Border0 (March 2026)** extends this Network layer directly into Secrets & Credentials/PAM territory: one-click, time-scoped, session-recorded access to servers, databases, and Kubernetes clusters, sitting on top of existing tailnet identity. Puts Tailscale in direct territory with 1Password, C1's Agentic Vault, and CyberArk/BeyondTrust. Full breakdown in `tailscale-research.md`.

---

### Identity & Access

The traditional core of IAM — but the agentic era breaks assumptions this layer was built on. Traditional IAM assumed identity = human, sessions are bounded, and accountability is inherent. Agents break all three: they're non-human identities, may run indefinitely, and require explicit audit design to be accountable at all.

Okta's agentic answer: three questions — where are my agents, what can they connect to, what can they do — anchored by discovery, least-privilege access, kill switches, and lifecycle governance. **Agent SSO (GA August 2026)** productized this into a free, core Okta SSO feature, registering agents as first-class identities with short-lived governed tokens in place of static API keys. The underlying protocol, Cross App Access (XAA), was adopted the same month as MCP's own official Enterprise-Managed Authorization extension — a genuine cross-vendor standard, not just an Okta feature. Full breakdown, including a real Black Hat 2026 counterpoint (a GitHub issue alone reached CI secrets in Anthropic's and Google's own coding-agent repos, 2.5 weeks before Agent SSO's GA) in [okta-research.md](../03_Industry-Intelligence/Company-Portfolio/Okta/okta-research.md).

**[WorkOS](../03_Industry-Intelligence/Company-Portfolio/WorkOS/workos-research.md)'s Airlock** takes a genuinely different architectural approach worth comparing directly against C1's Runtime Governance — intent-based access control (a task is stated as an intent, compiled into an action, evaluated per call) rather than pre-defined roles/scopes. Its own team names a real, unsolved tension honestly: "if an agent evaluates the policies, who checks the checker?" An independent review (Aug 2026) assesses WorkOS's agentic identity packaging as less mature than Okta's Agent SSO, even though Airlock's underlying model is arguably more novel — full comparison table in `workos-research.md`.

**C1 vs. Lumos** — the closest head-to-head in this layer, both AI-native and fast-deploying against slow legacy IGA. Neither has a clean structural advantage; execution and integration fit decide it more than category positioning. Full mechanism-level comparison in [c1-research.md](../03_Industry-Intelligence/Company-Portfolio/C1/c1-research.md).

**C1's July 2026 Launch Week pushed it well beyond this layer** — Discovery & Context, Secrets & Credentials, and a narrow slice of Detection, in one coherent four-day rollout. Full breakdown and dedicated comparisons against Origin, 1Password, Artemis/CrowdStrike, and Tailscale Aperture in [c1-research.md](../03_Industry-Intelligence/Company-Portfolio/C1/c1-research.md).

**The known gap:** Okta, C1, and Lumos all answer "should this agent be here." None of them answer "does this agent actually understand what it's looking at" (that's Dosu) or "what did this agent actually do, in causal detail" (that's Origin) — though C1's Runtime Governance is the closest an Identity & Access player has come to touching that causal territory, via real-time enforcement rather than after-the-fact explanation.

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

Behavioral, cross-domain detection and response. Artemis, CrowdStrike, and Splunk all belong here — full stop, regardless of deployment mechanism (an endpoint agent is just how the sensor gets deployed, not a separate capability).

**Artemis vs. CrowdStrike, in one line:** Artemis is an AI-native rebuild with a per-org dynamic detection model; CrowdStrike is an established platform (Falcon) with AI (Charlotte) layered on top, and its AI-activity visibility depends on vendors choosing to report through compliance channels rather than observing directly. Full comparison table in [artemis-security-research.md](../03_Industry-Intelligence/Company-Portfolio/Artemis/artemis-security-research.md).

**Splunk's role:** the dominant legacy SIEM every AI-native Detection player positions against — expensive at scale, complex, slow to adapt. The "AI-enabled bolt-on vs. AI-native rebuild" distinction that runs through this whole category starts with Splunk as the reference point.

**The honest distinction with Origin:** CrowdStrike/Artemis correlate what gets reported or observed. Origin observes what actually happens on the endpoint, independent of whether any vendor reports anything at all.

**C1's Agentic Security & Intelligence is Detection-adjacent, not Detection proper** — identity-configuration risk findings, not broad behavioral correlation. Closer to identity posture management than a SIEM. Full comparison in [c1-research.md](../03_Industry-Intelligence/Company-Portfolio/C1/c1-research.md).

**[Elastic Security](../03_Industry-Intelligence/Company-Portfolio/Elastic/elastic-research.md)'s real differentiator is architectural, not marketing** — no per-byte indexing tax the way Splunk has, making it genuinely cost-competitive at high ingest volumes (10TB/day+), traded against needing real in-house Elasticsearch expertise.

**[Palo Alto Networks' Cortex](../03_Industry-Intelligence/Company-Portfolio/Palo-Alto-Networks/palo-alto-networks-research.md)** (XSIAM, XDR, XSOAR, Xpanse) is Detection as one piece of a genuinely multi-layer platform — see `platformization.md`.

**Closes the loop automatically?** Generally no — Detection-layer tools correlate and alert; response is typically routed to a human or a separate SOAR/incident-response workflow, not resolved automatically by the detection layer itself.

---

### Telemetry Visualization & Aggregation

Not an identity-native layer — Grafana Labs isn't a security company, it's a general infrastructure observability platform (the LGTM stack: Loki for logs, Grafana for visualization, Tempo for traces, Mimir for metrics). It's placed here because it's a genuinely common destination layer: Detection, Endpoint, and even Identity & Access tooling often pipe their telemetry into a Grafana-style dashboard for human-readable correlation, rather than every layer building its own visualization from scratch.

**Why it's worth tracking in this ecosystem specifically:** Grafana's 2026 roadmap includes expanding its "All-in-One" suite into more advanced SOC/security analytics — a real signal the company is edging toward overlap with the Detection layer, not staying purely infrastructure-focused. Worth revisiting this placement as that expansion matures.

**A live, relevant case study:** Grafana itself suffered a real GitHub breach in May 2026 — a misconfigured GitHub Action (a "Pwn Request" vulnerability) exposed a token that let an attacker download the company's codebase, caught only via an internal canary token. The compromise was later traced to the broader TanStack npm supply chain attack. It's a clean, current illustration of CI/CD pipeline risk — directly relevant to the same governance-gap thread running through this whole ecosystem map, just realized at a company that builds observability tooling rather than identity tooling.

---

### Data Pipeline & Routing

Genuinely distinct from Telemetry Visualization, even though the two are adjacent in the observability stack. Grafana is a *destination* — where telemetry gets visualized and correlated after it arrives. [Cribl](../03_Industry-Intelligence/Company-Portfolio/Cribl/cribl-research.md) is the *pipe* — it sits upstream of every destination, deciding what data gets routed where, in what shape, after being filtered and reduced. Cribl doesn't store or visualize data itself (aside from Cribl Lake as an optional cheap storage destination); it's infrastructure every other telemetry-consuming layer depends on.

**The core value proposition:** telemetry volume is growing ~29% annually per IDC, doubling roughly every 18 months while budgets stay flat. Cribl customers routinely cut data volumes 30-50% and can feed multiple destination tools (a SIEM, a cheap cold-storage bucket, a dashboard) from a single collection pass, without re-instrumenting anything.

**The important industry signal:** major EDR/Detection-layer vendors — CrowdStrike, Palo Alto Networks, and SentinelOne — all acquired competing pipeline tooling in Q4 2025 (Onum, Observe AI, and Chronosphere respectively) specifically to build direct ingestion lines into their own platforms. This creates a real structural tension: a vendor-owned pipeline is commercially incentivized to route the most data toward that vendor's own destination. A neutral pipeline like Cribl has no such incentive, since its business model depends on staying agnostic about where data ultimately lands — the same "neutral connective layer vs. platform-native alternative" tension that shows up elsewhere in this ecosystem (Tailscale's Network layer vs. platform-locked alternatives; C1's Agentic Vault vs. credential models tied to one identity platform).

**Cribl on agentic AI specifically:** CEO Clint Sharp has publicly framed agent-generated telemetry as needing the same routing and reduction discipline as any other observability data — just at much higher, less predictable volume as agent adoption scales.

---

### Routing

Genuinely distinct from Data Pipeline & Routing, despite the name overlap — the object being routed is fundamentally different. [OpenRouter](../03_Industry-Intelligence/Company-Portfolio/OpenRouter/openrouter-research.md) routes live AI inference requests across 400+ models and 80+ providers, optimizing for cost, latency, quality, and reliability per request — not observability telemetry. Different buyer (a developer choosing which model handles a task, not a security/ops team routing logs), different failure mode (a badly-routed request means a worse or wrong AI answer, not a security blind spot).

**Also distinct from Tailscale's Aperture and C1's Agent Runtime Governance** — those AI gateways answer "is this traffic authorized to happen at all" (identity/security). OpenRouter answers "which model should handle this, given cost and quality tradeoffs" (optimization, not security).

**A live example of the Platformization and Practical Observability theses converging:** OpenRouter, a pure neutral-routing layer, was acquired by Stripe for a reported ~$7.5B in August 2026 — a real, current instance of a data/routing-only layer getting absorbed by whoever owns the surrounding economic action layer (Stripe's billing, tax, and fraud infrastructure). See `openrouter-research.md`, `platformization.md`, and `practical-observability.md`.

---

### Agent Construction

LangChain builds the orchestration and harness layer that turns a raw model into a working agent — prompts, tools, memory, planning, middleware. This is the "operating system" bet (per NVIDIA's Jensen Huang): most enterprises won't build their own agent orchestration from scratch, they'll build on top of a framework like LangChain.

**Critical distinction:** Agent Construction is explicitly NOT governance. LangChain and its competitors (CrewAI, AutoGen, LlamaIndex) have no native approval gates, policy enforcement, or audit trail before an agent acts on production systems. This is the seam where Identity & Access, Detection, and Hybrid Workforce Observability layers become necessary *alongside* a construction framework, not instead of it.

---

### Endpoint Visibility

Tanium and Ivanti generate state and inventory truth — is the device compliant, what's installed, what changed, who touched it. Query-based, real-time at scale (Tanium's specific historic differentiator), feeding into patch/asset/vulnerability management.

**[Axonius](../03_Industry-Intelligence/Company-Portfolio/Axonius/axonius-research.md) sits here too, but with genuinely broader scope than pure endpoint** — created the CAASM category, agentless discovery across devices, SaaS, cloud, identity, and OT/IoT, correlated into one system of record. Where Tanium/Ivanti are endpoint-first, Axonius is asset-first across the entire attack surface. Its Verified Assets push makes the same "garbage in, garbage out" argument already seen with Lumos's upstream data quality thesis. Full breakdown in axonius-research.md.

**What this layer cannot do:** explain *why* something happened, trace causal chains, or reason about intent. It can tell you a process ran or a file changed — it cannot tell you what an agent was trying to accomplish or what it read into context before acting.

**Closes the loop automatically?** Partially — patch/remediation actions can be automated once a policy is defined (this is Tanium's core strength, and the basis of the ITOM AI Prime partnership with ServiceNow), but the underlying visibility itself is passive; automation lives in a connected orchestration layer, not the visibility layer itself.

---

### Hybrid Workforce Observability

Origin's own language, used deliberately as the layer name: observability built for *"a workforce that is part-human and part-machine."*

This is a distinct layer from Endpoint Visibility, not a subset of it — the same **visibility vs. observability** split from monitoring/SRE practice. Visibility is state snapshots (what's installed, what changed). Observability is causal tracing (why it happened, what the agent was trying to do). Full side-by-side comparison against Tanium/Ivanti in [origin-research.md](../03_Industry-Intelligence/Company-Portfolio/Origin/origin-research.md).

**Why this layer is called out specifically:** nobody else operates here with this depth. It sits adjacent to Detection and Identity & Access (an agent's commit identity not matching its SSO identity is a real identity governance signal, surfaced only because Origin sees the endpoint causally) but its core job — reconstructing intent and causality for both human and AI activity — is unique enough to deserve its own layer.

**C1's Runtime Governance is the closest a governance-layer product has come to this territory** — real-time enforcement per tool call, but requires the agent's traffic to route through C1's gateway. Origin requires no enrollment at all. Governance vs. observation, not a clean substitute either way — full comparison in [c1-research.md](../03_Industry-Intelligence/Company-Portfolio/C1/c1-research.md).

**Important boundary, worth being precise about:** Origin's scope is genuinely agent-specific, not just "AI usage" broadly — it covers coding/computer-use agents (Claude Code, Cursor, Copilot) acting on an employee's own endpoint, alongside direct human AI tool use. This is not the same territory as Agentic Reliability below — Origin watches *internal* tool use on *employee* machines; Agentic Reliability watches agents a company *built and shipped* as its own product. Different object, different environment, no real overlap.

**Closes the loop automatically?** No — Origin surfaces causal findings (via dashboard, or via query through Claude/MCP) for a human to act on. Deep, causal Observability does not automatically imply automated remediation — see the Agentic Reliability comparison table below for why this matters as a second, independent axis.

---

### Agentic Reliability

A new layer, genuinely distinct from Hybrid Workforce Observability despite the surface-level similarity (both watch "agent behavior"). Split into two sub-rows using the same **visibility vs. observability** distinction already established elsewhere in this map — [Cortex](../03_Industry-Intelligence/Company-Portfolio/Cortex/cortex-research.md) (Visibility) and [Lemma](../03_Industry-Intelligence/Company-Portfolio/Lemma/lemma-research.md) (Observability).

This layer is growing fast enough, and is analytically rich enough (a full three-way comparison against Origin, plus the broader thesis it's the sharpest current proof of), that it now has its own dedicated doc: **[agentic-reliability.md](agentic-reliability.md)**.

---

### Secrets & Credentials / AI Financial Visibility

1Password spans two distinct jobs, worth keeping separate: vaulting/rotation/NHI governance (Secrets & Credentials), and tracking AI token spend by vendor/team/user (AI Financial Visibility, launched July 2026). Full breakdown of both in [1password-research.md](../03_Industry-Intelligence/Company-Portfolio/1Password/1password-research.md).

**Critical distinction, in Origin's own words:** *"Token bills tell you what you spent. [We] tell you what you bought."* Financial visibility is not behavioral or causal — a different layer solving a different pain (budget forecasting vs. causal governance).

**C1's Agentic Vault vs. 1Password's Connect API:** a genuine architecture difference — 1Password's Connect API still delivers the actual secret to the agent at runtime; C1's workload federation never gives the agent the raw secret at all. Two generations of the same problem. Full comparison in [c1-research.md](../03_Industry-Intelligence/Company-Portfolio/C1/c1-research.md).

**The category's mature incumbents — CyberArk and BeyondTrust:** [CyberArk](../03_Industry-Intelligence/Company-Portfolio/CyberArk/cyberark-research.md) pioneered PAM in 1999 and was the #1 player until its acquisition by Palo Alto Networks (Feb 2026, ~$25B — see Platformization). [BeyondTrust](../03_Industry-Intelligence/Company-Portfolio/BeyondTrust/beyondtrust-research.md) sits at #2, directly behind CyberArk, with its own Pathfinder platform unifying PAM, Secrets Management, CIEM, and ITDR. Both represent decades of accumulated enterprise-hardened technical depth (100+ patents each in CyberArk's case), a genuinely different profile from the faster-deploying, newer entrants (C1, 1Password) also in this layer.

---

---

### Cloud Posture

Wiz and Orca scan cloud environments for misconfigurations, exposed storage, overly permissive IAM policies. Out of scope for Network, Endpoint, or Observability layers entirely — a distinct surface. [Palo Alto Networks' Cortex Cloud](../03_Industry-Intelligence/Company-Portfolio/Palo-Alto-Networks/palo-alto-networks-research.md) (formerly Prisma Cloud, merged with Cortex CDR in Feb 2025) is the platform-consolidated version of the same category — see `platformization.md`.

---

### IT Workflow Orchestration

ServiceNow doesn't generate ground-truth data — it consumes truth from other layers and turns it into automated workflows and remediation actions.

**Two distinct ServiceNow-adjacent things, not to be confused:**

| | Now Assist AI Agents | ITOM AI Prime powered by Tanium |
|---|---|---|
| What it is | ServiceNow's own native AI agent product | A joint partnership — Tanium's real-time endpoint truth feeds ServiceNow's ITOM workflows for autonomous remediation |
| Ownership | Fully ServiceNow | Tanium (Endpoint Visibility) + ServiceNow (Orchestration), partnered |

The partnership pattern here is the same shape as LangChain: **the orchestration layer needs ground truth from somewhere else to act on.** ServiceNow orchestrates; Tanium (or other endpoint tools) supplies the facts it orchestrates around.

**[Rootly](../03_Industry-Intelligence/Company-Portfolio/Rootly/rootly-research.md)** is the other real player here — an AI-native on-call/incident management platform (direct PagerDuty/Opsgenie competitor) whose core business is squarely in this layer. Its July 2026 acquisition of ThinkHive also pushes it into Agentic Reliability territory — see `agentic-reliability.md`.

---

## The Governance Gap — The Thread Tying Every Layer Together

Across nearly every layer above, a consistent gap keeps appearing: **agent construction, orchestration, and even detection frequently lack native governance** — pre-action approval gates, policy enforcement, and audit trails before an agent acts.

- LangChain builds powerful agents but doesn't govern them
- Dosu makes agents smarter but doesn't govern them either
- Traditional Endpoint Visibility tools can't explain agent intent at all
- Even Detection tools depend heavily on what gets reported or observed after the fact

**This gap is where Identity & Access (Okta, C1, Lumos), Hybrid Workforce Observability ([Origin](../03_Industry-Intelligence/Company-Portfolio/Origin/origin-research.md)), and the emerging agentic governance thinking all converge.** It's also the exact seam explored in the "Agentic vs. Human Identity" POV piece elsewhere in this KB — agents don't decide, they meet conditions, and the risk is unchecked execution of those conditions without enough visibility to catch when they're wrong.

---

## Key Takeaways

- **ZTAI is a layer map, not a company catalog** — the same pain can be solved by different companies, and one company can operate in multiple layers
- **Visibility and observability are not the same thing** — Endpoint Visibility (Tanium, Ivanti) tells you *what* happened; Hybrid Workforce Observability (Origin) tells you *why*
- **Detection is Detection, regardless of deployment mechanism** — CrowdStrike and Artemis are the same layer; an endpoint agent is just how the sensor gets deployed
- **Discovery & Context splits cleanly by asset type** — Cyera for data, Dosu for knowledge, same structural problem
- **Agent Construction is explicitly not governance** — LangChain builds, it doesn't police what it builds
- **Origin's differentiation is real and specific** — vendor-agnostic, causal, covers both human and AI activity, sees shadow agents nobody else can see
- **The governance gap is the connective tissue** — nearly every layer eventually runs into "who approves this, who audits this, who can kill this" — and that gap is where identity security expertise becomes the differentiator
- **C1 and Lumos are the closest head-to-head in Identity & Access** — both AI-native, both fast-deploying, execution and fit decide it more than category positioning
- **Telemetry Visualization (Grafana) sits underneath, not beside, the security-native layers** — it's where other layers' data often gets seen, and it's a live example of CI/CD supply chain risk in its own right (the May 2026 GitHub breach)
- **Data Pipeline & Routing (Cribl) is genuinely distinct from Telemetry Visualization** — the pipe vs. the destination, and the EDR vendors acquiring competing pipeline tools (CrowdStrike/Onum, Palo Alto/Observe AI, SentinelOne/Chronosphere) is a real structural signal about who wants to own the connective layer
- **Axonius extends Endpoint Visibility into full asset attack-surface visibility (CAASM)** — broader than Tanium/Ivanti's endpoint-first scope, and its Verified Assets push makes the same upstream-data-quality argument already seen with Lumos, applied to asset inventory instead of identity governance
- **Agentic Reliability is a genuinely new layer, not a subset of Hybrid Workforce Observability** — the object being watched is different: Origin watches internal employee tool use, Cortex/Lemma watch whether a company's own shipped AI product actually works. Full breakdown, including the Origin/Cortex/Lemma three-way comparison, now lives in `agentic-reliability.md`
- **Platformization is a real, recurring pattern worth its own read** — Palo Alto/CyberArk/Idira, C1's Launch Week, BeyondTrust's Pathfinder, Elastic's three pillars, and 1Password's Secrets+Spend combo are all evidence. Full thesis and honest tradeoffs (including a documented layoff-vs-promise gap) in `platformization.md`
- **CyberArk and BeyondTrust are the mature, patent-rich incumbents in Secrets & Credentials** — CyberArk pioneered PAM in 1999, now absorbed into Palo Alto Networks; BeyondTrust sits at #2 with its own unified Pathfinder platform
- **Routing (OpenRouter) is genuinely distinct from Data Pipeline & Routing (Cribl)** despite the name overlap — different object (AI inference requests vs. telemetry), different failure mode, different buyer. OpenRouter's own ~$7.5B acquisition by Stripe is a live example of the Platformization and Practical Observability theses converging

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
| Cribl — What is an Observability Pipeline | https://cribl.io/blog/the-observability-pipeline/ |
| Cortex | https://www.cortex.io |
| Lemma | https://www.uselemma.ai |
| Axonius — Adapt 2026 AI-Powered Remediation | https://www.axonius.com/newsroom/press-release/axonius-delivers-ai-powered-remediation |
| Tanium & ServiceNow — ITOM AI Prime Partnership | https://www.businesswire.com/news/home/20260506341909/en/Tanium-Combines-Forces-with-ServiceNow-to-Deliver-New-Autonomous-IT-Solution-Powered-by-Industry-Leading-Platforms |
| ConductorOne | https://www.conductorone.com |
| Grafana Labs | https://grafana.com |
| Grafana Labs — GitHub Breach Coverage | https://www.securityweek.com/grafana-confirms-breach-after-hackers-claim-they-stole-data/ |
| BeyondTrust | https://www.beyondtrust.com |
| Palo Alto Networks | https://www.paloaltonetworks.com |
| CyberArk | https://www.cyberark.com |
| Elastic | https://www.elastic.co |
| Rootly | https://rootly.com |
| OpenRouter | https://openrouter.ai |
| WorkOS | https://workos.com |
