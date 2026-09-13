# Rootly — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** September 2026  
**Official Reference:** https://rootly.com  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Founded** | 2021, San Francisco, CA — via Y Combinator Summer 2021 batch |
| **Stage** | Series A (with subsequent smaller follow-on activity) |
| **Total funding** | ~$15.2–15.7M across Seed VC, Convertible Note, and Series A ($12M, August 2023) |
| **Investors** | Y Combinator, 8VC, Renegade Partners, Google Gradient Ventures, XYZ Ventures |
| **Team size** | ~68–75 employees (mid-2026), growing ~17% quarter-over-quarter |
| **Notable customers** | NVIDIA, Elastic, Grammarly, Canva, Figma, Tripadvisor, Cisco, Shell, LinkedIn, DoorDash, Replit, Webflow, Squarespace, Dropbox, Lattice, Faire — collectively managing ~60,000 incidents per year |
| **Recognition** | Top-10 on Deloitte's 2025 Technology Fast 50 (Canada) |
| **Category** | AI-native on-call and incident management — increasingly extending into AI agent reliability engineering |
| **Website** | https://rootly.com |

---

## Founders

- **JJ Tang (Co-Founder & CEO)** — worked on the enterprise product side at Instacart before founding Rootly. Named to Forbes 30 Under 30 (Enterprise Technology). Publicly active on how his own company operates — has spoken about running significant parts of Rootly's operations directly through Claude
- **Quentin Rousseau (Co-Founder & CTO/CISO)** — was a Site Reliability Engineer at Instacart, working the same underlying problem from the opposite end (keeping systems up, rather than building the enterprise product on top of them)

**The founding insight:** Tang and Rousseau built incident automation software internally at Instacart to increase uptime, then recognized the same underlying problem — coordinating a fast, effective response when something breaks — was universal, not specific to their employer. Rootly's own framing extends this to genuinely high-stakes territory: the platform is used not just by tech companies but by organizations running **911 call centers and suicide hotlines**, where incident response speed carries direct human safety consequences.

---

## What Rootly Actually Does

**Core positioning:** an AI-native, Slack-native (also Microsoft Teams) incident management platform covering the full lifecycle — alert routing, on-call scheduling, incident coordination, root cause analysis, and automated postmortem generation. Direct competitor to PagerDuty, Opsgenie, and incident.io.

**The core problem, in the founders' own words:** "Most enterprises today have a fire-alarm equivalent for discovering incidents, but are DIY for incident resolution — using paper checklists or relying on key individuals." Growing system complexity (microservices, third-party dependencies) means no single engineer can hold the full picture of what's happening during an incident anymore.

**Practical mechanics:**
- Setup in roughly 10 minutes, with 50+ integrations automating manual admin work — paging responders, incident channel creation, tracking action items and metrics, stakeholder communication, and generating retrospectives automatically
- **AI SRE** — the core AI capability: analyzes code changes, live telemetry, and incident history to identify root cause and propose a fix, even for code the responder didn't write themselves
- Cited outcome, per CEO JJ Tang: accelerates incident resolution times by **80% or more**
- Real, published security research: **"Investigating CVE-2026-66066 with the Rails Forensics Agent Skills"** — Rootly builds and publishes its own forensics tooling, not just incident coordination features

---

## The ThinkHive Acquisition (July 28, 2026) — A Direct Move Into Agentic Reliability

This is the most significant recent development, and it matters directly for how Rootly is placed in this KB's ecosystem thinking.

**What ThinkHive does, on its own:** an AI agent reliability platform — traces every step an agent takes and evaluates whether it actually accomplished its task, not just whether it returned *a* response. Correlates metrics, traces, and evaluations to catch the two failure modes that matter most in production: **hallucination and drift**. Clusters failures into patterns (rather than a wall of individual complaints), proposes fixes, and validates them with **shadow testing** before they ever reach a real user. Founded by Nour Alkhatib and Abdulwahab Omira.

**Why Rootly acquired it — stated dual purpose:**

1. **Internal:** Rootly's own AI SRE agent operates during high-stakes incident response. ThinkHive's framework (groundedness scoring, hallucination detection, shadow testing) is now used to verify Rootly's own agents are production-grade *before* they ever touch a real incident.
2. **Customer-facing:** the same rigor extends outward — Rootly customers now get agentic reliability capability (scoring the risk of a code change against a service's incident history and live telemetry *before* it pages someone; predicting probable incidents based on historical similarity patterns) as part of the core product.

**JJ Tang's framing of the underlying shift, worth remembering precisely:** *"A service going down trips every alarm you own. An AI agent that quietly starts giving wrong answers trips nothing. Latency is fine, the dashboard is green, and the agent has told customers the wrong refund policy. This type of situation is a reliability problem wearing a new disguise."*

**This is genuinely, directly the same territory as Lemma's core thesis** (see `lemma-research.md`) — silent semantic failures, causal trace-based root cause analysis, automated remediation validated before deployment. Post-acquisition, Rootly is a real, direct entrant into the same specific sub-category Lemma occupies, not merely an adjacent IT-workflow tool that happens to touch AI.

---

## ZTAI Layer Placement

**Genuinely dual-layer, and the second layer just got significantly stronger with the ThinkHive acquisition:**

| Layer | Rootly's Presence |
|---|---|
| **IT Workflow Orchestration** | Core on-call/escalation/postmortem workflow automation — same layer as ServiceNow |
| **Agentic Reliability — Observability** | Post-ThinkHive, a direct competitor to Lemma — causal trace-based detection of silent AI agent failures (hallucination, drift), with automated, shadow-tested remediation |

**The Rootly vs. Lemma comparison, worth being precise about:**

| | Rootly (via ThinkHive) | Lemma |
|---|---|---|
| **Origin** | Incident management platform that acquired agent-reliability technology to extend its own scope | Purpose-built from inception specifically for AI agent silent-failure detection |
| **Primary object watched** | Both an organization's own production incidents (broadly) *and* AI agent behavior specifically (via ThinkHive) | Exclusively a company's own shipped AI agent product |
| **Remediation model** | Proposes fixes, validated via shadow testing before reaching a user | Proposes fixes, delivered directly via PR or API |
| **Maturity/scale** | Established platform (60,000+ incidents/year across real customers), extending into this new territory | Pre-seed, 1M+ daily traces, unproven at Rootly's scale |

**Honest read:** Rootly enters this specific sub-category with the credibility and existing customer base of a mature incident-management platform, but the ThinkHive capability itself is newly acquired, not originally built for this purpose the way Lemma's entire existence is. Lemma is narrower and newer but purpose-built; Rootly is broader and established but bolting this capability on. See `ZTAI-ecosystem-map.md` for the full layer breakdown.

---

## Competitive Landscape

| Competitor | Position vs. Rootly |
|---|---|
| **PagerDuty, Opsgenie** | The legacy incumbents Rootly explicitly positions against ("Switch from PagerDuty" is literal site navigation) — Rootly's pitch is AI-native design from the ground up versus AI features retrofitted onto older platforms |
| **incident.io** | The closest direct peer competitor — similar AI-native, Slack-first positioning, competing head-to-head for the same mid-market SRE team buyer |
| **xMatters, Moogsoft, Blameless, ScienceLogic** | Other cited competitors in the broader incident/AIOps space, generally narrower or less AI-forward |
| **Lemma** | Not a direct incident-management competitor, but now a direct competitor specifically in AI agent reliability/observability, post-ThinkHive — see comparison above |

---

## Key Takeaways

- **Rootly's founding story is a clean "both sides of the problem" match** — an enterprise product person and an SRE, both from Instacart, building the tool they wished they'd had
- **The ThinkHive acquisition (July 2026) is the most important recent development** — it directly extends Rootly into the same Agentic Reliability — Observability territory Lemma occupies, with a stated dual purpose: harden Rootly's own AI SRE agent internally, and offer the same capability to customers
- **The core reframe worth remembering:** "an AI agent quietly giving wrong answers trips nothing" — the same fundamental insight Lemma calls "silent failures," independently arrived at and now directly acted on by Rootly through acquisition rather than from-scratch build
- **Real stakes, not just enterprise SaaS** — Rootly explicitly serves 911 call centers and suicide hotlines alongside tech companies, a genuinely different weight class of "incident" than typical B2B SaaS uptime concerns
- **Dual-layer placement is now stronger than before this research pass** — IT Workflow Orchestration (established, core business) plus a real, credible entry into Agentic Reliability — Observability (new, via acquisition)

---

## Official References

| Source | Link |
|---|---|
| Rootly | https://rootly.com |
| Rootly Blog — Why Rootly Acquired ThinkHive | https://rootly.com/blog/why-rootly-acquired-thinkhive |
| BusinessWire — Rootly Acquires ThinkHive Announcement | https://www.businesswire.com/news/home/20260728909768/en/Rootly-Acquires-ThinkHive-to-Bring-Reliability-Engineering-to-its-AI-Agents |
| TechCrunch — Rootly Raises $12M Series A | https://techcrunch.com/2023/08/10/incident-response-management-platform-rootly-secures-12m/ |
| Rootly — Investigating CVE-2026-66066 with Rails Forensics Agent Skills | https://rootly.com/blog |
