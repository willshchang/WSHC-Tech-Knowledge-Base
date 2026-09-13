# Artemis Security — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** May 2026  
**Official Reference:** https://artemissecurity.com  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Founded** | Late 2025 (approximately October 2025) |
| **Emerged from stealth** | April 15, 2026 |
| **HQ** | New York City, NY |
| **Team size** | ~30 people (targeting ~65 by end of 2026) |
| **Stage** | Series A |
| **Total funding** | $70M (Seed + Series A combined) |
| **Category** | AI-native detection & response / SIEM replacement |
| **Customers** | Mercury, Wix, Lemonade, Abnormal AI + enterprise banking/fintech |
| **Website** | https://artemissecurity.com |

---

## Founders

### Shachar Hirshberg — Co-Founder & CEO

- IDF Intelligence Corps — 5 years as intelligence officer
- IBM — early cybersecurity software development
- **Demisto** — development manager (Demisto created the SOAR category; acquired by Palo Alto Networks for ~$600M)
- Harvard Business School — MBA
- **AWS** — led **GuardDuty**, the largest cloud attack detection product in the world
- Founded Artemis to rebuild security ops from scratch for the AI era

### Dan Shiebler — Co-Founder & CTO

- **University of Oxford** — PhD in Machine Learning
- **TrueMotion** — designed patented sensor data analytics algorithms (company acquired for $650M+)
- **Twitter** — led web ads ML organization
- **Abnormal AI** — led AI/ML team and detection efficacy
- Core thesis: "The real breakthrough isn't just using better AI models, but in giving those models deep, structured understanding of how an organization functions."

> Both founders built detection and AI systems inside some of the most consequential security platforms in the industry for nearly a decade before starting Artemis.

---

## Funding

| Round | Amount | Lead | Co-Investors |
|---|---|---|---|
| **Seed** | $15M | Brightmind (co-led) | First Round Capital |
| **Series A** | ~$55M | Felicis | First Round Capital, Brightmind, Theory VC, Two Sigma, Lockstep |

**Notable angel investors:**  
Founders of Demisto and Abnormal AI, former CEO and CTO of Splunk, senior executives from CrowdStrike, Palo Alto Networks, Microsoft, and Okta.

**Traction at time of announcement:**
- Several seven-figure deals closed
- Multi-million ARR expected by end of 2026
- Processing **15,000TB daily** and **billions of events per hour**
- Mean time to detect and respond reduced by **94%** for early customers

---

## Product: What Artemis Actually Does

### The Problem They're Solving

Traditional SIEMs were built for human-speed attacks: static rules written by analysts over weeks, data ingested and stored upfront (costs scale linearly with data), manual investigation across fragmented tools.

AI-driven attacks now execute in minutes, adapt in real time, and never repeat the same pattern. Rules are obsolete before they ship. Security teams are left piecing together context after damage is done.

### Artemis's Approach — 4 Differentiators

**1. Dynamic data model (your org's "DNA")**  
Artemis builds a model from each customer's own telemetry — fusing behavioral logs across users, machines, cloud workloads, and applications with business context. It doesn't ask "is this anomalous?" It asks "does this make sense for *this specific organization*?"

**2. Federated query architecture (no upfront ingestion)**  
Data stays where it lives — existing SIEMs, data lakes, cloud-native stores. Artemis retrieves on-demand via federated queries. Result: full visibility at approximately **1/5 the cost** of traditional SIEM.

**3. AI-generated, continuously tuned detections**  
Detections are not static rules. They're generated and tuned autonomously to each customer's environment — and updated continuously as the environment changes. Even different business units within one enterprise can have distinct detection logic.

**4. Attack stories, not isolated alerts**  
Instead of flooding analysts with individual alerts, Artemis correlates signals across identity, cloud, endpoint, network, and SaaS into coherent **attack narratives**. Example: a privilege escalation in Okta + unusual API activity in AWS = one correlated story, not two disconnected alerts.

### Additional Capabilities

- **Automated response** — isolate a compromised identity before lateral movement, block IP addresses, rotate credentials — adjustable autonomy from advisory to fully automated
- **Shadow AI & posture hygiene** — surfaces over-privileged accounts, undocumented integrations, APIs called with elevated privileges, cloud spend waste
- **Natural language investigation** — analysts ask questions in plain English; no proprietary query language required
- **Agentic threat hunting** — proactively hunts suspicious activity without manual prompting

### How Artemis Is Built

> "99% of our code is written with AI. Every engineer ships 4-5 features per week — work that would have taken a strong engineer two to three months just a year ago."

30 people delivering the output of a 200-person engineering team. A new integration takes 1-2 days vs. 3-6 months at competitors.

Artemis is one of a select few cybersecurity companies working in **deep collaboration with Anthropic**, integrating Claude's reasoning capabilities directly into the platform.

---

## Market Position & Competitors

### The Market Shift

The SIEM category is undergoing structural disruption:
- Cisco's acquisition of Splunk triggered aggressive pricing and CISO frustration
- 60+ CISOs surveyed by Felicis listed SIEM as a top-3 priority to replace
- "AI-enabled" (AI bolted onto legacy) vs. "AI-native" (built from scratch) is the defining split

### Competitive Landscape

| Company | Category | Artemis Positioning vs. Them |
|---|---|---|
| **Splunk** (Cisco) | Legacy SIEM market leader | Expensive (cost scales with data), complex, slow — primary displacement target |
| **CrowdStrike Falcon** (Next-Gen SIEM via Humio) | Next-gen SIEM | Strong endpoint-centric; Artemis is cross-domain (identity + cloud + network) |
| **Microsoft Sentinel** | Cloud-native SIEM | Deep Azure integration; Artemis is cloud-agnostic and faster to value |
| **Palo Alto Cortex XSIAM** | AI-enabled SOC platform | "AI-enabled" on existing architecture vs. Artemis's "AI-native" rebuild |
| **Exabeam / LogRhythm** | Legacy SIEM / UEBA | Rule-based, human-speed — same generation as Splunk |
| **Anvilogic / Panther / Hunters.ai** | SIEM modernization | Adjacent but less agentic; Artemis goes further on autonomous investigation |

> Artemis's primary pitch is not "better SIEM." It's "SIEM built for a world where AI attacks AI."

---

## Anthropic / Claude Connection

- Artemis integrates **Claude's reasoning capabilities** directly into its detection and investigation platform
- They are among a select group of security companies in **deep collaboration with Anthropic**
- Anthropic published a **case study** on how Artemis uses Claude as a core engineering collaborator — every line of product code written by AI agents; engineers design systems and review outputs
- Artemis references Anthropic's Mythos Preview (autonomous AI-orchestrated cyber-espionage) as context for why their platform is necessary

> "We are one of a select few cybersecurity companies working in deep collaboration with Anthropic, integrating Claude's reasoning capabilities directly into the platform to defend against exactly these kinds of threats."

Reference: https://claude.com/customers/artemis

---

## ZTIA Layer Placement

**Layer: Detection**

Artemis is a Detection-layer company, alongside CrowdStrike — this is the job, regardless of deployment mechanism. See `ZTAI-ecosystem-map.md` for the full layer breakdown and how Detection connects to every other layer.

| Angle | Detail |
|---|---|
| **Telemetry as a data source** | Artemis's federated query architecture pulls telemetry from Network, Identity & Access, and Endpoint layers without upfront ingestion — device auth events, ACL matches, access anomalies all become correlation signals |
| **Shared customer base** | Targets modern, cloud-native tech companies (Mercury, Wix, Lemonade) — the same customer profile that adopts modern Network and Identity & Access layer tooling |
| **Identity signal correlation** | Artemis correlates identity signals (Okta privilege escalation, AWS API anomalies) — a direct connection to the Identity & Access layer, surfacing behavioral risk that access-governance tools alone wouldn't catch |
| **Agentic security** | Artemis explicitly tracks AI agents as entities in its data model — connecting Detection to the Agent Construction and Hybrid Workforce Observability layers as agentic activity becomes a larger share of what needs correlating |

> Natural integration story: ground-truth telemetry from Network, Identity & Access, and Endpoint layers feeding into Artemis's behavioral **Detection** layer.

**How this compares to identity-adjacent detection (C1):** C1's Agentic Security & Intelligence (launched July 2026) also produces "findings," but at a much narrower scope — identity-configuration risk (unowned accounts, misclassification) rather than Artemis's broad behavioral/attack correlation across environments. Different buying decision, and C1 explicitly supports ingesting Artemis-style findings via API rather than replacing them. See `c1-research.md` for the full comparison.

---

## Key Takeaways

- Artemis is a **$70M AI-native SIEM replacement** founded by veterans of AWS GuardDuty, Demisto (SOAR pioneer), Abnormal AI, and Twitter ML — out of stealth April 2026
- Core thesis: **AI vs. AI** — defenders need machine-speed detection to match machine-speed attacks
- Technical differentiator: **federated query architecture + per-org dynamic data model** — not generic rules, not static ingestion
- Already processing **15,000TB/day** and reducing MTTD/MTTR by **94%** for enterprise customers
- Deep **Anthropic/Claude** integration — one of a select few security companies in direct collaboration
- **Artemis sits in the ZTAI Detection layer** alongside CrowdStrike — federated telemetry from Network, Identity & Access, and Endpoint layers feeds its behavioral correlation model

---

## Official References

| Source | Link |
|---|---|
| Artemis website | https://artemissecurity.com |
| Anthropic case study | https://claude.com/customers/artemis |
| Fortune — $70M raise announcement | https://fortune.com/2026/04/15/exclusive-artemis-raises-70m-to-help-fight-ai-powered-attacks-with-ai/ |
| First Round Capital — founder interview | https://review.firstround.com/inside-artemis-ai-vs-ai-war-shachar-hirshberg-dan-shiebler-co-founders-artemis/ |
| Felicis — Series A thesis | https://www.felicis.com/blog/artemis-series-a-security-gets-a-new-brain |
| AlleyWatch — CEO interview | https://alleywatch.com/2026/04/artemis-ai-native-security-siem-replacement-autonomous-threat-detection-platform-shachar-hirshberg/ |
| SecurityWeek | https://www.securityweek.com/artemis-emerges-from-stealth-with-70-million/ |
| Ctech (Hebrew tech press) | https://www.calcalistech.com/ctechnews/article/h1eagbt311x |
