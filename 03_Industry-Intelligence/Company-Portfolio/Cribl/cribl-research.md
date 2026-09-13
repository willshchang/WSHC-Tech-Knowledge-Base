# Cribl — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  
**Official Reference:** https://cribl.io  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Founded** | 2018 (some sources cite 2017 incorporation), San Francisco, CA |
| **Stage** | Series E |
| **Total funding** | $600M–$725M across 6-7 rounds (sources vary slightly) |
| **Latest valuation** | $3.5B (August 2024) |
| **Revenue** | ~$200-305M ARR (2025), 163% CAGR over four years |
| **Team size** | ~1,100+ employees worldwide |
| **Notable customers** | 43 Fortune 100 companies, Sophos among named references |
| **Recognition** | Forbes Cloud 100 — #37 (2025), America's Best Startup Employers 2025 |
| **Category** | Observability pipeline / data engine for IT and Security |
| **Website** | https://cribl.io |

---

## Founders

- **Clint Sharp (Co-Founder & CEO)** — two decades leading product management and IT operations at Splunk and Cricket Communications before founding Cribl. Company nickname for him: "the man who built the Switzerland of data pipelines."
- **Ledion Bitincka (Co-Founder & CTO)**
- **Dritan Bitincka (Co-Founder)**

**The founding insight, in Sharp's own words:** "As practitioners who worked in this space for years, my co-founders and I know firsthand the challenges facing IT and Security as data grows exponentially. What worked over the last ten years simply cannot keep up with the needs of businesses today."

---

## What Cribl Actually Does

**The core problem:** telemetry data (logs, metrics, traces) is growing roughly 29% per year according to IDC — data volumes double about every 18 months while budgets stay flat. IT and Security teams face redundant agents, capacity anxiety, and blind spots from data they never collected in the first place.

**Cribl's positioning: "The Data Engine for IT and Security."** Cribl sits *between* your data sources and your destinations — it doesn't store or visualize data itself, it routes, transforms, and reduces it in flight.

```
Sources (logs, metrics, traces)
        ↓
   Cribl Stream (routing, filtering, enrichment, volume reduction)
        ↓
Destinations (Splunk, Datadog, S3, Grafana, SIEM tools, cold storage)
```

**Six core attributes that make the pipeline model work:** schema-agnostic processing, universal schema adaptation, broad protocol support, easy verification, responsive configurability, and reliable delivery.

**Practical outcomes cited:** customers routinely cut data volumes by 30-50%, reuse existing agents to feed multiple destination tools simultaneously, and can trial new platforms without ripping out existing infrastructure. A real example pattern: a security team collects logs from every system, filters out noise, routes critical security events to their SIEM in real time, while sending the complete raw data to cheaper cold storage for compliance retention — all from one pipeline, one collection pass.

**The nickname that stuck:** "the Switzerland of data pipelines" — vendor-neutral by design, works with Kafka, Kinesis, Splunk, Grafana, and effectively any source or destination rather than locking customers into one ecosystem.

---

## Product Lineup

- **Cribl Stream** — the flagship observability pipeline (routing, filtering, transformation, reduction)
- **Cribl Edge** — lightweight collection at the edge/endpoint level
- **Cribl Search** — federated search across data without needing to move or re-index it first
- **Cribl Lake** — cloud-native storage layer, positioned as a lower-cost destination for retained data

**Partnership worth noting:** Cribl and Imply (creators of the Imply Lumi observability data layer, built by the original creators of Apache Druid) announced a joint solution in January 2026 — Cribl handles ingest/routing, Imply Lumi handles fast query/storage, giving customers end-to-end control from pipeline to query without disrupting existing tools.

---

## Cribl on Agentic AI — "Agentic AI Needs a Data Rethink"

In May 2026, Clint Sharp appeared on CNBC's *Fortt Knox* specifically to discuss agentic AI's implications for data infrastructure. His take was measured, not evangelical: customers know they need a strategy, but legal and security teams broadly aren't ready yet.

**Cribl's stated infrastructure answer:** cloud-native lakehouses and elastic compute that scales CPU/GPU capacity 1:1 with agent rollout — the same underlying thesis as the rest of Cribl's product: as AI agents proliferate and generate their own telemetry (queries, tool calls, outputs), that data needs the same routing, reduction, and governance discipline as any other observability data, just at a much higher and more unpredictable volume.

---

## The Industry Signal — EDR Vendors Are Acquiring the Pipeline Layer

This is a genuinely important structural trend, not just a Cribl-specific detail: major EDR/security platform vendors have started **acquiring pipeline tooling directly** rather than staying dependent on a neutral third party like Cribl.

**Recent Q4 2025 acquisitions cited industry-wide:** Onum, Observe AI, and Chronosphere — all acquired by leading EDR platforms specifically to build direct ingestion lines into their own products (CrowdStrike, Palo Alto Networks, SentinelOne).

**Why this matters strategically:** a vendor-owned pipeline is structurally incentivized to route the most data into that vendor's own platform, since the pipeline vendor and the destination vendor share commercial interest. A neutral pipeline like Cribl has no such incentive — its business model depends on staying agnostic about where data ultimately lands. This is the same "own the connective layer vs. stay neutral" tension seen elsewhere in this KB (Tailscale as neutral network layer vs. platform-native alternatives; C1's Agentic Vault vs. platform-locked credential models).

**The honest read on what this means for Cribl specifically:** the very companies that could be Cribl's customers (via SIEM/EDR integration) are simultaneously the companies best positioned to build competing in-house pipeline capability. Cribl's defense is genuine multi-destination neutrality and deep protocol/format breadth — a single-platform pipeline (built by CrowdStrike, for example) will always be optimized primarily for CrowdStrike's own ingestion needs, not for routing data to five different destinations equally well.

---

## Competitive Landscape

| Competitor | Position vs. Cribl |
|---|---|
| **Splunk Edge Processor** | Native to Splunk shops, tightly integrated but not vendor-neutral |
| **Datadog Observability Pipelines** | The managed/integrated-suite option — good if already committed to Datadog end-to-end |
| **Vector** | Open-source, flexible, but requires more hands-on operational management |
| **Edge Delta** | Closest direct observability-pipeline peer/competitor |
| **Expanso** | Positions as a broader data control plane — not just observability telemetry, also IoT, application, and event data, with governance (masking, redaction) built in from the start |
| **Onum, Observe AI, Chronosphere** | Now owned by CrowdStrike, Palo Alto, and SentinelOne respectively — platform-native pipeline options, optimized for their own ecosystem rather than staying neutral |

**Cost model note (a real point of friction cited by analysts):** Cribl uses credit-based consumption pricing, which some enterprises find harder to forecast above the 1 TB/day free tier — one of the more commonly cited reasons teams evaluate alternatives.

---

## ZTAI Layer Placement

**New layer: Data Pipeline & Routing** — distinct from Telemetry Visualization & Aggregation (Grafana). Grafana is a *destination* where telemetry gets visualized and correlated. Cribl is the *pipe* — the routing and volume-reduction layer that decides what data reaches which destination, in what shape, before it ever arrives. See `ZTAI-ecosystem-map.md` for the full layer breakdown.

**What this layer cannot do:** Cribl doesn't detect threats, visualize dashboards, or store data long-term itself (aside from Cribl Lake as an optional cheap destination) — it's infrastructure that every other layer depends on to actually receive usable data, not a destination in its own right.

---

## Key Takeaways

- **Cribl is "the Data Engine for IT and Security"** — a vendor-neutral pipeline sitting between data sources and every destination tool, not a visualization or storage product itself
- **The core value proposition is volume reduction plus flexibility** — 30-50% data volume cuts, reuse existing agents across multiple destinations, trial new platforms without infrastructure rip-and-replace
- **The EDR-vendor pipeline acquisition trend is a real structural signal** — CrowdStrike, Palo Alto, and SentinelOne all acquired competing pipeline tooling (Onum, Observe AI, Chronosphere) in Q4 2025, creating genuine tension between platform-native and neutral pipeline models
- **Cribl explicitly frames agentic AI as a data infrastructure problem** — Clint Sharp's CNBC appearance positioned AI agent telemetry as needing the same routing/reduction discipline as any observability data, just at much higher volume
- **This deserves its own ZTAI layer, distinct from Grafana** — Data Pipeline & Routing (the pipe) vs. Telemetry Visualization & Aggregation (the destination)

---

## Official References

| Source | Link |
|---|---|
| Cribl | https://cribl.io |
| Cribl — What is an Observability Pipeline | https://cribl.io/blog/the-observability-pipeline/ |
| Cribl — Series E Announcement | https://cribl.io/news/cribl-announces-319m-series-e/ |
| Imply + Cribl Joint Solution Announcement | https://imply.io/news-and-press/imply-and-cribl-deliver-modern-data-architecture-for-observability/ |
