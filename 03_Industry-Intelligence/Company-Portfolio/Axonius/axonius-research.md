# Axonius — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  
**Official Reference:** https://www.axonius.com  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Founded** | 2017, New York, NY |
| **Stage** | Late Stage / Series E Extension |
| **Total funding** | $595M–$700M+ across 7 rounds (sources vary slightly) |
| **Latest valuation** | $2.6B (Series E, March 2024) |
| **Revenue** | Surpassed $200M ARR (May 2026), doubled revenue in two years |
| **Team size** | ~700 employees |
| **Category** | Cyber Asset Attack Surface Management (CAASM) — creators of the category; also SaaS Management Platform (SMP) and SaaS Security Posture Management (SSPM) |
| **Website** | https://www.axonius.com |

---

## Founders & Leadership

- **Dean Sysman** — Co-founder, led as CEO until February 2026, now Executive Chairman
- **Ofri Shur** — Co-founder
- **Avidor Bartov** — Co-founder
- **Joe Diamond** — President since earlier in 2026, became CEO in May 2026 as Axonius surpassed the $200M ARR milestone

**The founding thesis, from Sysman:** every connected device poses a security risk, yet organizations lack visibility into their total inventory. Sysman explained Axonius was built to focus on foundational cybersecurity needs — asset visibility — rather than chasing flashier innovation.

---

## What Axonius Actually Does

**The core problem:** with over 100 million workers globally in hybrid work arrangements, and 78% of employers anticipating widespread hybrid adoption by 2026, organizations must secure an ever-expanding, fragmented array of endpoints, SaaS applications, cloud resources, and increasingly OT/IoT devices — most without a single accurate inventory of what actually exists.

**Axonius Asset Cloud** — the core platform, built on an agentless architecture (a fundamental design choice distinguishing it from traditional agent-based asset management):

- Continuous, agentless discovery of devices, users, applications, cloud resources, and identities
- 1,400+ integrations ("adapters") aggregating data from existing IT and security tools rather than replacing them
- 45+ asset types tracked, on-premises and in the cloud
- Correlates data into a single system of record — device, identity, software, SaaS app, vulnerability, and security control, plus the *relationships* between them
- Deploys in days, not months — a direct architectural consequence of being agentless

**What organizations actually do with it:** mitigate threats, navigate risk, decrease incident response time, automate remediation action, and inform business-level security strategy — while eliminating the manual, repetitive cross-referencing that asset visibility gaps otherwise require.

---

## 2026 Product Expansion — Adapt 2026 (April 15, 2026)

A major platform expansion, announced at Axonius's own Adapt 2026 event:

### Axonius Exposures
AI-powered exposure management, extending beyond traditional CVE-based vulnerability tracking:
- **Security Finding Rules** — extends coverage to any policy-defined condition: identity hygiene gaps, SaaS misconfigurations, certificate issues, custom risk conditions — not just CVEs
- **Remediation Ownership** — every finding gets an assigned owner with defined SLAs from day one
- **AI-Driven Recommended Remediations** — early access as of April 2026, general availability targeted July 2026
- **Attack Path Analysis** and **threat intelligence enrichment**

**The problem this addresses directly, per the Axonius 2026 Actionability Report (with the Ponemon Institute, 662 IT/security professionals surveyed):** 55% of companies still track remediation in spreadsheets. Only 45% of organizations consolidate asset and exposure data into a single view.

**Joe Diamond's framing:** *"Findings pile up because the data isn't trusted, ownership isn't clear, and entire asset classes aren't even in the picture."*

### Axonius Cyber-Physical Assets
Extends the platform into IoT, OT, and industrial environments — identifying and fingerprinting cyber-physical assets, enriching them with contextual attributes, and correlating them into the same Asset Cloud alongside traditional IT assets. Cited stat: 96% of OT incidents start from an IT compromise, making a unified IT/OT view a genuine security necessity rather than a nice-to-have.

### Axonius Verified Assets
A new "data trust" standard for asset management — in preview as of April 2026, targeting general availability August 2026. Directly addresses a problem specific to the AI-agent era: **automated workflows and AI agents that act on unverified asset data compound errors at machine speed.** A ghost asset, duplicate record, or stale entry that would be a minor annoyance for a human analyst becomes a systemic, fast-multiplying problem once AI-assisted or fully autonomous workflows start acting on that same bad data without human review catching it first.

> "You can't act at scale on data you can't verify. It's true for your team, and for your AI agents." — Axonius, on the reasoning behind Verified Assets

This is structurally the same insight already captured elsewhere in this KB regarding Lumos's "upstream data quality" problem — governance and remediation automation is only as good as the data feeding it. Axonius is making the identical argument specifically for asset inventory data, at the moment AI agents start acting on it directly.

---

## Potential Cisco Acquisition Talks (January 2026)

Reported talks of Cisco pursuing a roughly $2B acquisition of Axonius surfaced in January 2026. Worth noting: $2B would sit *below* Axonius's existing $2.6B private valuation, which — if accurate — suggests either an early/lowball offer stage or reporting on a partial/structured deal rather than a full acquisition at a premium. No confirmed completed transaction as of this writing; treat as a developing story rather than settled fact.

---

## Competitive Landscape

| Competitor | Position vs. Axonius |
|---|---|
| **Tanium** | Real-time endpoint query at massive scale, strong on active remediation; Axonius is broader (agentless, covers SaaS/cloud/identity/OT-IoT, not just endpoint) and doesn't require agent deployment |
| **JupiterOne** | Prioritizes visualizing asset interdependencies, especially within cloud infrastructure and security configurations; Axonius emphasizes broader integrations and more robust automated policy enforcement |
| **Lansweeper** | Narrower, more traditional IT asset inventory tool |
| **Ordr** | Network-centric device visibility/management, narrower scope than Axonius's full CAASM platform |
| **Palo Alto Cortex Xpanse** | Outside-in External Attack Surface Management (EASM) — discovers internet-facing assets from an attacker's perspective; complementary rather than directly competing, since Axonius is primarily inside-out (integrating with existing tools) |
| **Spiceworks, Sitetracker** | Cited as competitors by market trackers but generally narrower/more specialized tools |

**Category creation note:** Axonius is credited as the creator of the CAASM (Cyber Asset Attack Surface Management) category itself — a genuinely defensible claim that shapes how analysts and competitors alike frame the space.

---

## ZTAI Layer Placement

**Primary layer: Endpoint Visibility** — alongside Tanium and Ivanti, in the same "state snapshots, inventory, query-based" category defined elsewhere in this KB. But Axonius's actual scope is broader than pure endpoint — it spans devices, SaaS applications, cloud resources, identities, and (as of 2026) OT/IoT, making it closer to a full **asset attack-surface visibility layer** than endpoint-specific tooling alone. See `ZTAI-ecosystem-map.md` for the full layer breakdown.

**What this layer still cannot do:** like Tanium and Ivanti, Axonius tells you *what exists and what's configured* — it does not explain *why* an agent or user did something, the way Origin's Hybrid Workforce Observability layer does. Axonius's new Verified Assets and Exposures products push toward better-trusted, better-owned findings, but the core job remains inventory and posture, not causal behavioral explanation.

---

## Key Takeaways

- **Axonius created the CAASM category** — Cyber Asset Attack Surface Management — and remains the most credentialed player in it, agentless by design, deployed in days rather than months
- **The leadership transition is recent and relevant** — Dean Sysman moved to Executive Chairman in February 2026; Joe Diamond became CEO in May 2026 as the company crossed $200M ARR
- **The 2026 Adapt expansion (Exposures, Cyber-Physical Assets, Verified Assets) is a coherent strategic push** — extending from pure asset visibility into AI-driven remediation, OT/IoT coverage, and data trust specifically for the agentic era
- **Verified Assets makes the same "garbage in, garbage out" argument already seen with Lumos** — asset inventory data quality directly determines whether AI-driven remediation and autonomous agents can be trusted to act on it
- **1,400+ integrations is the real architectural moat** — Axonius doesn't replace existing IT/security tools, it aggregates and correlates what they already know into one trustworthy system of record

---

## Official References

| Source | Link |
|---|---|
| Axonius | https://www.axonius.com |
| Axonius — Adapt 2026 AI-Powered Remediation Announcement | https://www.axonius.com/newsroom/press-release/axonius-delivers-ai-powered-remediation |
| Axonius Blog — Asset Cloud AI-Ready Data Foundation | https://www.axonius.com/blog/axonius-asset-cloud-is-enhanced-with-ai-ready-data-foundation |
| Help Net Security — Axonius Asset Cloud Expansion Coverage | https://www.helpnetsecurity.com/2026/04/15/axonius-expands-asset-cloud/ |
