# C1 (formerly ConductorOne) — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  
**Official Reference:** https://www.c1.ai  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Founded** | 2020, San Francisco, CA |
| **Stage** | Series B |
| **Total funding** | $111M across 4 rounds |
| **Latest round** | $79M Series B (Oct 2025), led by Greycroft, with CrowdStrike Falcon Fund, Accel, Felicis Ventures |
| **Team size** | ~142 employees (2026) |
| **Category** | AI-native identity security platform — unifies IGA, IAM, and PAM |
| **Notable customers** | DoorDash, Instacart, Zscaler, Ramp, DigitalOcean, Qualtrics |
| **Website** | https://www.conductorone.com |

---

## Founders

- **Alex Bovee (Co-Founder & CEO)** — previously a product leader at Okta, where he led authentication, security, and privileged access management product lines, plus Okta's overarching Zero Trust product strategy. Also held senior product roles at Lookout on enterprise device security.
- **Paul Querna (Co-Founder & CTO)** — technical/engineering leadership background, founder of one other company prior to ConductorOne.

**Why the founding team matters:** Bovee's background running Okta's own security and PAM product lines means ConductorOne was built by someone who saw the gaps in the market-leading platform from the inside — a similar "insider builds the disruptor" pattern seen elsewhere in this space (e.g., Cyera's founders and Unit 8200, Tina Kung at Nue having built the CPQ systems Nue now disrupts).

---

## Growth Trajectory

- 4x revenue growth cited in a February 2025 press release
- Appointed William Bengtson as CISO (January 2026)
- Launched "AI Access Management" product extension in March 2026, ahead of RSAC 2026
- Launched C1 Headless Identity Infrastructure (May 2026) — a programmable substrate unifying identity governance, vaulting, credentials, real-time authorization, and agent identity into one graph, one policy engine, one audit trail
- Launched C1 Autonomous Worker / C1AW (June 2026) — a governed AI agent purpose-built for identity work itself (revoking stale grants, building access reviews, pulling audit evidence), operating under the same policy engine that governs human users
- Rebranded from ConductorOne to **C1** (2026) — "a new name for a new era of identity... where AI agents outnumber humans and the identity platform must govern both"
- **C1 Launch Week (July 27–30, 2026)** — four sequential product launches completing what C1 calls the "Agentic Control Plane" (full breakdown below)

---

## Core Platform — The Unified Identity Graph

ConductorOne's central architectural concept: consolidating identity, resource, and permissions data into a real-time graph, providing visibility and policy-driven automation across systems that were previously siloed. This underpins the platform's stated mission — "secure identity at scale by minimizing the tasks humans need to touch."

**Core capabilities:**
- Identity lifecycle management
- Just-in-time provisioning
- Dynamic, context-aware access controls
- Automated access reviews
- Continuous posture monitoring
- No-code connectors across cloud, on-premise, and custom/homegrown systems (hundreds of integrations)
- Developer-friendly APIs and Terraform support

### AI Access Management (Launched March 2026)

A unified control plane extending governance to AI tools, agents, and Model Context Protocol (MCP) connections. The core design principle: make the **governed path faster than the ungoverned one** — end users can request and receive access to an AI tool in under 60 seconds via self-service, while IT/security retain full visibility and policy control over every AI tool, agent, and MCP connection in the environment.

**The stated problem this solves:** shadow AI proliferation — employees adopting AI tools without any governed path, because the governed path is typically slower or more cumbersome than just signing up directly.

---

## The Founding Thesis on Non-Human and AI Identity

"Non-human identities and emerging technologies like AI agents are the unknown unknowns for many organizations today. Security leaders are often unable to identify how many of these entities are operating within their environments — let alone who is responsible for managing them — making it all but impossible to secure this expanding attack surface." (Bovee)

**Supporting data point cited:** Non-human identities now outnumber human identities roughly 20:1 in many organizations, growing at an estimated 24% annually.

**On identity as the security foundation generally:** "In a world where the perimeter no longer truly exists, identity is the only real foundation of security." (Bovee)

**On AI agents specifically breaking traditional IAM:** the company's own framing is explicit that traditional IAM fails AI agents — identity must shift from governing static accounts to governing machine execution and intent.

---

## Customer Proof Points

- **DoorDash** — unified security across 300,000+ identities for real-time, policy-driven access
- **Instacart** — moved 100% of privileged access to just-in-time provisioning
- **Qualtrics** — automates tens of thousands of access changes per month
- **Ramp** — deployed intelligent access reviews that significantly reduced manual oversight

**A notable customer quote (Infrastructure Security Team Leader, Instacart):** "I've had experience with legacy vendors in this space and it's a night and day difference — in the way you can use the product, in the onboarding time, in the time to value, and how you're treated as a customer."

---

## C1 Launch Week (July 27–30, 2026) — The Agentic Control Plane

Four sequential launches, one per day, building toward what C1 branded the **"Agentic Control Plane."** Each post explicitly built on the previous day's release — this was a coherent, sequenced product story, not four disconnected feature drops.

### Day 1 — Shadow AI Discovery (July 27)

Finds unsanctioned AI across two surfaces:

- **Endpoint:** scans devices for AI tool configs, MCP servers (including local `stdio` traffic invisible to network scanners/proxies), and credential files (recorded by type/location, not exposed)
- **Cloud & identity providers:** connectors enumerate AI agents running in platforms like Salesforce Agentforce and AWS Bedrock AgentCore, plus the broader non-human population (service principals, managed identities, app registrations, tokens) across Entra, Okta, GCP, GitHub, Snowflake, Active Directory

**The key move:** a discovered agent, MCP server, or credential doesn't just get flagged — it becomes a real access item on the same governance plane as employee access. Owner assigned, routed through request/approval, certified in review, deprovisioned when stale. Governance becomes a lifecycle, not a one-time switch.

**Cited stat:** IBM's *Cost of a Data Breach Report 2025* — 1 in 5 organizations reported a breach due to shadow AI; among those breached via an AI model/application, 97% lacked proper AI access controls.

### Day 2 — Agentic Vault (July 28)

A secrets vault built directly into the identity platform — people, AI agents, and service accounts are all first-class secret holders, governed through the same request/approval/audit path as any other access.

**Workload federation (the core mechanism):** agents authenticate via a signed identity matching a defined trust condition, exchanging it for a short-lived, scoped credential. The agent never receives the raw, long-lived secret — meaning a prompt-injected or compromised agent has no key to leak, because it was never given one. Engineers get the same treatment via desktop app/CLI — request, use, expire.

**Post-quantum from day one:** key exchange via X-Wing (X25519 + ML-KEM-768, NIST-standardized). Directly tied to a real regulatory driver — a June 22, 2026 White House executive order directing federal agencies toward post-quantum cryptography migration. The framing: a secret encrypted under legacy cryptography today is a "harvest now, decrypt later" breach already in progress, just waiting on quantum hardware to mature.

**Decoys:** planted fake credentials (client IDs, secrets, tokens) placed where a real one would sit. Any attempted use triggers a high-confidence "Decoy credential used" finding with source IP, time, and fingerprint — identity-native honeypots.

**Cited stat:** GitGuardian's *State of Secrets Sprawl 2026* — 28.65M new secrets leaked on public GitHub in 2025 (+34% YoY), leaked AI-service credentials specifically up 81%.

### Day 3 — Agent Runtime Governance (July 29)

Every AI agent tool call routes through a single governed gateway. Each agent is scoped to only the tools its job requires (least privilege at the tool level); every call is scored for risk in real time and can be blocked, held for human approval, or have sensitive fields redacted from the result — before it executes.

**The risk model — Simon Willison's "lethal trifecta":** private data (agent can access it) + untrusted content (a hidden instruction, e.g. buried in a support ticket) + external communication path (agent can send data out). When all three converge in one session, C1 flags it. This is a real, credited framework from outside security research, not proprietary marketing language.

**Key differentiator claim vs. a plain AI firewall/prompt filter:** every decision is tied to a governed agent identity and accountable owner. A standalone monitor can flag suspicious behavior; it can't attribute the decision to a specific governed identity and the policy that permitted or stopped it.

**Rollout model:** policies can start in "observe mode" (record projected decisions without changing execution) before being enforced — and once enforced, fail closed (if the guardrail check can't run, the call is held, not allowed).

### Day 4 — Agentic Security & Intelligence (July 30)

Detects identity risk across people, service accounts, workloads, and agents — raises findings for conditions like an agent/service account with no owner, an account misclassified as human, name-shadowing, or a connector with anomaly detection disabled. Each finding links to that identity's full access graph (blast radius across apps, accounts, entitlements).

**Remediation routing:** straightforward findings can auto-resolve; sensitive ones route to an owner for approval through existing governance; findings can also generate tickets directly in ServiceNow, Jira, or PagerDuty via webhook. C1 can also **ingest findings from other security tools via API** — imported findings get the same routing, tagging, and audit trail as native ones.

**Standout stat:** Palo Alto Networks' *2026 Identity Security Landscape* — organizations now manage **109 machine identities (including AI agents) per human identity**, up from 82:1 the year prior.

**How Day 4 differs from Day 1, in C1's own framing:** *"Day 1 answers 'what's running here?' Day 4 answers 'which identities need attention, and how do I remediate the risk?'"*

---

## Competitive Landscape

| Competitor | Position vs. C1 |
|---|---|
| **Lumos** | Closest direct competitor in core Identity & Access governance — similar positioning as an autonomous/AI-native identity platform. See detailed comparison below |
| **SailPoint, Saviynt (legacy IGA)** | Deeper entitlement granularity in some cases, but months-long deployment cycles and significantly higher cost |
| **Okta IGA** | Okta is the identity provider itself; C1 (like Lumos) is positioned as identity-provider agnostic |
| **1Password** | Since Agentic Vault (Launch Week Day 2), a genuine head-to-head on agent-specific credential security — workload federation, post-quantum crypto, decoys are arguably more sophisticated than 1Password's current agent-focused offering |
| **Origin** | Genuine overlap on endpoint shadow AI discovery specifically; diverges sharply beyond that — see detailed comparison below |
| **Artemis, CrowdStrike** | Partial overlap via Agentic Security & Intelligence, but narrower in scope — identity-configuration risk (ownership gaps, misclassification) rather than broad cross-environment behavioral correlation |
| **Tailscale Aperture** | Same "identity replaces secrets" philosophy, applied at the network layer instead of the identity-platform layer — narrower in scope (AI/LLM gateway traffic specifically), not really a substitute |
| **Auth0, RSA** | Cited among top competitors by market trackers, though positioned in adjacent rather than directly overlapping categories |

*The four comparisons below (Origin, 1Password, Artemis/CrowdStrike, Tailscale Aperture) go deeper than any other company doc in this KB — C1's Launch Week genuinely touches four different ZTIA layers at once, so each comparison is doing real cross-layer work. See `ztia-ecosystem-map.md` for the higher-level layer map these all plug into.*

### ConductorOne vs. Lumos — Detailed Comparison

Both companies pursue an extremely similar thesis: modern, fast-deploying, AI-native identity governance replacing legacy IGA, with explicit focus on governing non-human and AI agent identities alongside humans.

| Dimension | ConductorOne | Lumos |
|---|---|---|
| **Founding team background** | Alex Bovee ran security/PAM product at Okta directly | Andrej Safundzic, Alan Flores Lopez, Leo Mehr — met in a Stanford ethics/policy class, not from an incumbent identity vendor |
| **Total funding** | $111M | $65M+ |
| **Core architecture concept** | Unified Identity Graph — real-time graph of identity, resource, and permission data | Albus (AI agent) + visibility/observability split — Albus does the analytical work, platform provides the static visibility layer |
| **AI agent governance framing** | AI Access Management — governs agent and MCP access as an extension of the identity graph | Agentic UARs — Albus specifically automates the access review workflow itself |
| **Investor signal** | CrowdStrike Falcon Fund as a strategic investor — a notable security-industry endorsement | Scale Venture Partners, a16z — more traditional enterprise SaaS VC profile |
| **Customer profile cited** | DoorDash, Instacart, Zscaler, Ramp — mix of consumer-scale and security-native companies | Pinterest, GitHub, MongoDB, Roku — broader consumer/tech mix |

**The honest assessment:** these two companies are close enough in positioning that choosing between them likely comes down to execution speed, specific integration depth for a given customer's stack, and which AI-agent-governance framing (a unified graph vs. an AI analyst) resonates more with a specific buyer. Neither has a structural advantage that clearly settles the comparison — this is a genuine two-horse race in the "modern, fast, AI-native IGA" sub-category.

### C1 vs. Origin — Governance vs. Observability, Not a Clean Win Either Way

Post-Launch-Week, C1 and Origin have real overlap worth naming precisely, and a real divergence that keeps them from being pure substitutes.

**Where they genuinely overlap:** C1's Shadow AI Discovery (Day 1) scans devices for local MCP configs, unsanctioned copilots, and plaintext credentials in `.env` files — nearly identical surface area to Origin's own core discovery claim.

**Where they diverge, and it matters:**

| | C1 Runtime Governance | Origin (Hybrid Workforce Observability) |
|---|---|---|
| **Model** | Prevention via gateway — every tool call for agents *routed through C1* is scored and can be blocked, held, or redacted before execution | Passive causal observation at the endpoint — explains *why*, for any agent, sanctioned or shadow |
| **Enrollment requirement** | Only governs traffic actively routed through C1's gateway | Sees everything on the endpoint regardless of enrollment — no onboarding required |
| **Core question answered** | "Should this action be allowed to happen?" | "Why did this happen, what was the intent behind it?" |
| **What it can't do** | An agent that never routes through the gateway is simply ungoverned — no visibility into it at all | Doesn't block anything — explains after or during, doesn't prevent |

**The honest synthesis:** C1 is building a *governance* control plane — discover, vault, enforce, remediate — but it requires bringing an agent's traffic *into* its system to govern it. Origin is building an *observability* control plane that works *beside* any system, including C1, without requiring enrollment. In a mature stack these read as complementary rather than competing: C1 enforces hard policy on what it governs; Origin explains what actually happened — including shadow agents C1 hasn't onboarded yet, or *why* a blocked call was even attempted in the first place. Notably, C1 explicitly supports ingesting third-party findings via API (per Day 4) — meaning Origin's causal output could realistically feed *into* C1's remediation queue rather than compete head-on with it.

### C1 vs. 1Password — Fetch-and-Deliver vs. Never-Deliver-At-All

Since Agentic Vault (Launch Week Day 2), C1 is a genuine competitor to 1Password specifically for agent-facing credential security. The two platforms solve overlapping problems with meaningfully different architectures.

| | 1Password (Connect API / Secrets Automation) | C1 (Agentic Vault) |
|---|---|---|
| **How an agent gets a credential** | Fetches it dynamically via the Connect API at runtime — avoids hardcoding, but the agent (or the calling code) does receive the actual secret value | Workload federation — a signed identity matching a trust condition is exchanged for a short-lived, scoped credential; the agent never receives the raw, long-lived secret at all |
| **Exposure model** | Reduces *static* exposure (no secret sitting in a config file) but the credential still enters the agent/application's runtime context at the moment of use | Eliminates exposure structurally — there is no raw secret for a compromised or prompt-injected agent to leak, because it was never issued one |
| **Post-quantum readiness** | Not a stated feature as of this writing | Post-quantum-hybrid from day one (X-Wing: X25519 + ML-KEM-768), explicitly tied to the June 2026 White House executive order on quantum-safe migration |
| **Breach deterrence mechanism** | Standard vaulting, rotation, audit logging via the Events API | Adds decoy credentials — fake secrets planted in likely-exposure locations (`.env`, CI variables) that trigger a high-confidence alert the instant anyone attempts to use them |
| **Governance model** | Vault access governed through 1Password's own permission model | Membership *is* the access control — each vault is a cryptographic group; granting access adds a member cryptographically, revoking access re-keys the entire group, so there's no separate governance system to reconcile after an incident |
| **What 1Password still does that C1 doesn't** | Broader legacy footprint (consumer + enterprise password management), Unified Access (SaaS discovery + password manager combined), **AI Spend and Consumption Management** (token spend visibility by vendor/team/user) — C1 has no equivalent financial-visibility feature | — |

**The honest read:** 1Password's Connect API represents the *previous* generation of the "avoid hardcoding secrets" pattern — dynamic fetch instead of static storage, which was a real improvement over `.env` files but still ultimately delivers the credential into the agent's context. C1's Agentic Vault (and the broader industry pattern it's part of — Infisical's competing Agent Vault product uses the identical "agent never possesses the credential" philosophy) represents the newer architectural bet: if the agent never holds the secret, prompt injection and compromise can't extract what was never given. This is a real, structural difference, not just marketing language — but 1Password retains real breadth C1 doesn't touch, particularly AI spend visibility and its much larger existing enterprise footprint outside of pure agent use cases.

### C1 vs. Artemis / CrowdStrike — Identity Hygiene vs. Behavioral Detection

Agentic Security & Intelligence (Launch Week Day 4) put C1 into Detection-adjacent territory, but the overlap with Artemis and CrowdStrike is narrower than it might first appear — the two are answering genuinely different questions.

| | Artemis / CrowdStrike (Detection layer) | C1 (Agentic Security & Intelligence) |
|---|---|---|
| **Core question** | "Is something behaving wrong *right now*?" — active, in-progress anomalous behavior across environments | "Is this identity's *configuration* wrong?" — static risk conditions on known identities |
| **What triggers a finding** | Behavioral anomalies: unusual login patterns, abnormal API call volume, privilege escalation sequences, correlated cross-domain attack signals | Configuration risk: an agent/service account with no owner, an account misclassified as human, a name shadowing a real account, a connector with anomaly detection switched off |
| **Data sources** | Federated queries across identity, cloud, network, and endpoint telemetry (Artemis); Falcon sensor + Claude Compliance API ingestion (CrowdStrike) | C1's own identity graph, plus third-party findings ingested via API |
| **Output** | Correlated attack narratives — "here's a sequence of events that looks like an active compromise" | Discrete, scoped findings — "this specific identity has this specific configuration problem," each independently addressable |
| **Remediation path** | Typically routes to incident response — contain, investigate, respond | Routes through *existing identity governance* — assign owner, revoke, right-size, same request/approval/audit path as normal access changes |

**The honest read:** this is much closer to **identity posture management** — a DSPM-style hygiene scan applied to identity configuration rather than data — than it is to true behavioral detection and response. Artemis and CrowdStrike are trying to catch an attack *as it happens* or reconstruct one *after the fact* across a wide surface. C1's Day 4 product is trying to catch *structural governance gaps* before they become exploitable — closer in spirit to a continuous compliance/hygiene check than a SIEM. They're not really competing for the same buying decision: a CISO evaluating "do we have a detection platform" and a CISO evaluating "is our identity governance clean" are asking different questions, even though both now technically produce "findings." Worth noting C1 explicitly supports *ingesting* findings from tools like Artemis or CrowdStrike via API — suggesting C1 sees itself as the remediation/governance layer downstream of detection, not a replacement for it.

### C1 vs. Tailscale Aperture — Identity Platform Gateway vs. Network Gateway

Aperture (Tailscale's AI governance gateway, alpha Jan 2026) and C1's Agent Runtime Governance solve a strikingly similar problem — replacing raw API keys with identity, and putting a governed gateway in front of AI/LLM traffic — but they approach it from opposite ends of the stack.

| | Tailscale Aperture | C1 (Agentic Vault + Agent Runtime Governance) |
|---|---|---|
| **Where it sits** | Network layer — runs directly on the Tailnet | Identity platform layer — a dedicated gateway independent of any specific network |
| **What it replaces** | Raw provider API keys (OpenAI, Anthropic, Gemini) with Tailscale identity | Raw long-lived credentials with short-lived, scoped, workload-federated credentials |
| **Core mechanism** | A single provider key stays contained within the gateway itself; access is governed by Tailscale identity and ACLs | Every tool call routed through an identity-aware gateway, scored against the "lethal trifecta," credentials issued per-use via workload federation |
| **Scope of coverage** | AI/LLM provider traffic specifically (OpenAI, Anthropic, Gemini, self-hosted) — tied to coding tools (Claude Code, Codex, Gemini CLI, Roo Code, Cline) | Broader — governs any tool call an agent makes, not just LLM provider API calls, plus the full surrounding lifecycle (discovery, vaulting, remediation) |
| **Underlying philosophy** | "Identity eliminates the need for secrets" — same logic as Tailscale SSH, applied to LLM API keys | Same core philosophy — "govern every secret like an identity" — applied at the identity-platform layer instead of the network layer |
| **What it doesn't do** | No credential vaulting for non-AI secrets, no identity risk detection, no broader access governance — Aperture is scoped specifically to AI/LLM gateway traffic | Requires routing through C1's gateway specifically; doesn't provide network-layer connectivity or segmentation the way Tailscale does |

**The honest read:** these aren't really substitutes — they're the same "identity replaces secrets" philosophy implemented at two different layers of the stack, and a mature deployment could plausibly run both simultaneously without conflict. Aperture governs *how AI traffic reaches the network* (a Tailscale-native problem, solved with Tailscale identity). C1 governs *the full lifecycle of every credential and tool call an agent makes*, independent of which network it's running on. If anything, Aperture is narrower in scope by design — it's an AI gateway feature bolted onto Tailscale's existing network product, not a standalone identity governance platform the way C1 is. The genuinely interesting overlap is philosophical, not competitive: both companies independently arrived at "identity should replace static secrets" as the answer to the AI credential sprawl problem, just from completely different starting points (network vs. identity platform).

---

## ZTIA Layer Placement

**Primary layer: Identity & Access (Governance)** — same core layer as Lumos and Okta IGA.

**Since Launch Week, C1 is genuinely multi-layer**, not just Identity & Access:

| ZTIA Layer | How C1 Shows Up There |
|---|---|
| **Identity & Access** | Core, original positioning — Unified Identity Graph, access reviews, lifecycle management |
| **Discovery & Context** | Shadow AI Discovery (Day 1) — finds unowned agents, MCP servers, credentials across endpoint and cloud |
| **Secrets & Credentials** | Agentic Vault (Day 2) — direct 1Password competitor for agent-specific credential security |
| **Detection (narrow slice)** | Agentic Security & Intelligence (Day 4) — identity-configuration risk findings, narrower than Artemis/CrowdStrike's broad behavioral correlation |

This mirrors the same pattern already seen with 1Password (Secrets/Credentials + AI Financial Visibility) and Origin (Endpoint + Detection + Identity) — the companies worth tracking closely right now rarely stay inside one clean layer. See `ztia-ecosystem-map.md` for the full layer breakdown.

---

## Key Takeaways

- **C1 rebranded from ConductorOne in 2026** — "a new name for a new era of identity," reflecting the shift from pure workforce IGA to governing both humans and agents
- **ConductorOne was built by an Okta security-product insider** — Alex Bovee ran the exact product lines (auth, security, PAM, Zero Trust strategy) that C1 now positions against
- **The Unified Identity Graph is the core architectural bet** — real-time consolidation of identity, resource, and permission data into one graph, rather than a static, periodically-synced view
- **Launch Week (July 27–30, 2026) completed the "Agentic Control Plane"** — Discover (Shadow AI Discovery) → Secure (Agentic Vault) → Govern (Agent Runtime Governance) → Detect & Remediate (Agentic Security & Intelligence), a coherent four-day product arc, not scattered feature drops
- **C1 is now genuinely multi-layer** — Identity & Access remains core, but Launch Week added real footprint in Discovery, Secrets & Credentials, and a narrow slice of Detection
- **C1 and Origin overlap on endpoint shadow AI discovery specifically, but diverge sharply beyond that** — C1 governs/enforces via a gateway (requires enrollment), Origin observes/explains at the endpoint (works regardless of enrollment). Complementary more than competing in a mature stack
- **Agentic Vault vs. 1Password is a genuine, structural architecture difference, not just a feature gap** — 1Password's Connect API still delivers the actual secret to the agent at runtime (dynamic fetch); C1's workload federation never gives the agent the raw secret at all. 1Password retains real breadth C1 lacks (AI spend visibility, broader enterprise footprint)
- **Agentic Security & Intelligence is identity posture management, not behavioral detection** — it answers "is this identity's configuration wrong," not "is something attacking us right now." Genuinely narrower than Artemis/CrowdStrike, and C1 explicitly positions itself to ingest their findings rather than replace them
- **C1 and Lumos remain genuinely close competitors** in core Identity & Access — both AI-native, both fast-deploying; the real differentiation is execution and specific-fit rather than a clear category advantage
- **CrowdStrike's strategic investment** is a notable signal of security-industry confidence, distinct from Lumos's more traditional enterprise SaaS investor profile

---

## Official References

| Source | Link |
|---|---|
| C1 | https://www.c1.ai |
| C1 — We Are C1 (Rebrand Announcement) | https://www.c1.ai/blog/wearec1 |
| C1 — Introducing Shadow AI Discovery | https://www.c1.ai/blog/introducing-shadow-ai-discovery |
| C1 — Introducing Agentic Vault | https://www.c1.ai/blog/introducing-agentic-vault |
| C1 — Introducing Agent Runtime Governance | https://www.c1.ai/blog/introducing-agent-runtime-governance |
| C1 — Introducing Agentic Security and Intelligence | https://www.c1.ai/blog/introducing-agentic-security-and-intelligence |
| C1 — Headless Identity Infrastructure Announcement | https://www.globenewswire.com/news-release/2026/05/06/3288899/0/en/c1-launches-headless-identity-infrastructure-for-the-agentic-enterprise.html |
| C1 — Autonomous Worker (C1AW) Announcement | https://www.globenewswire.com/news-release/2026/06/15/3311817/0/en/C1-Launches-C1-Autonomous-Worker-a-Governed-AI-Agent-for-Enterprise-Identity-Work.html |
| ConductorOne — AI Access Management Launch | https://finance.yahoo.com/sectors/technology/articles/conductorone-launches-ai-access-management-130000647.html |
| Greycroft — Series B Announcement | https://www.greycroft.com/perspectives/building-the-future-of-ai-native-identity-security-greycroft-leads-conductorones-series-b/ |
| Tracxn — ConductorOne Profile | https://tracxn.com/d/companies/conductorone |
