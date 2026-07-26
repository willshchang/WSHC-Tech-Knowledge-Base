# Grafana Labs — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  
**Official Reference:** https://grafana.com  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Founded** | Started December 2013 as a hobby project by Torkel Ödegaard; incorporated as Grafana Labs in October 2014 |
| **HQ** | New York City |
| **Total funding** | ~$908M across 7 rounds |
| **Latest valuation** | ~$6B (Series D extension, August 2024) |
| **Revenue** | ~$270M ARR as of mid-2024 (+69% YoY) |
| **Scale** | 20M+ users globally, 5,000+ paying customers, 25M+ users cited in more recent coverage |
| **Category** | Open-source observability and monitoring — metrics, logs, traces, visualization |
| **Website** | https://grafana.com |

---

## Founders & Origin

- **Torkel Ödegaard** — Swedish developer who started Grafana as a personal hobby project (originally called "Raintank") in December 2013, publicly released as open source in January 2014
- **Raj Dutt (CEO)** and **Anthony Woods** — commercialized the project into Grafana Labs alongside Ödegaard

**The origin is a genuinely organic, community-first story** — Grafana wasn't built as a startup pitch, it emerged from one developer's personal need for better dashboards, then grew into an open-source movement before a company formed around it.

---

## Product Evolution — The LGTM Stack

Grafana Labs expanded from a pure visualization tool into a full observability stack, commonly referred to as **LGTM**:

| Component | Function | Launched |
|---|---|---|
| **L**oki | Log aggregation | December 2018 |
| **G**rafana | Visualization/dashboarding (the original product) | 2014 |
| **T**empo | Distributed tracing | August 2020 |
| **M**imir | Metrics storage (Prometheus-compatible at scale) | March 2022 |

**The killer feature across the stack:** correlated navigation — clicking a spike in a Grafana metrics panel can jump directly to the relevant Loki log lines, then to the Tempo trace that produced the offending span, all within one UI. This kind of cross-signal correlation was historically a commercial-only capability; Grafana's stack made it standard in the open-source world.

**Licensing note:** Grafana shifted its license to AGPLv3 in April 2021 — a significant move in the broader open-source licensing debate playing out across the industry at the time (many open-source infra companies were changing licenses to prevent cloud providers from repackaging their software without contributing back).

---

## Funding Timeline (Key Rounds)

| Round | Amount | Date | Notes |
|---|---|---|---|
| Series C | $220M | Aug 2021 | Co-led by Sequoia Capital and Coatue; valued the company at $3B |
| Series D extension | $270M | Aug 2024 | Led by Lightspeed Venture Partners, new investor CapitalG (Alphabet's growth fund); valued at $6B |

**Notable board members:** Carl Eschenbach (Sequoia partner, former President/COO at VMware), David Schneider (Coatue general partner, former President at ServiceNow) — both joined following the Series C.

---

## Recent Product Direction (2026)

- **Grafana 13**, launched at GrafanaCON 2026 (April 2026) — positioned around making open observability easier to run at scale
- **AI-focused observability tools** announced at the same event, explicitly targeting what the company calls the "AI blind spot" — visibility gaps specific to AI/agent workloads
- **Grafana Cloud Proactive Assistant** — generative AI layered on top of telemetry, letting engineers query and remediate issues using natural language, aimed at improving mean time to resolution (MTTR)
- **Adaptive Metrics** — uses machine learning to detect unused or low-value time series, with reported customer cost savings of up to ~40% on observability bills
- Early-2026 expansion of the "All-in-One" observability suite to include more advanced SOC/security analytics capability — a notable move toward the security/detection space, not just infrastructure monitoring
- Active global expansion — ObservabilityCON events held in Toronto, Sydney, and an AI-powered observability push into Latin America (Santiago) during 2026

---

## Recent Security Incident — GitHub Breach (May 2026)

**What happened:** on May 16, 2026, Grafana Labs disclosed that an unauthorized party obtained a token granting access to its GitHub environment, allowing the attacker to download the company's codebase.

**Root cause:** a "Pwn Request" vulnerability — a misconfigured GitHub Action triggered on `pull_request_target` events, which granted external contributors access to production secrets during CI runs.

**How it was caught:** one of Grafana's own deployed canary tokens (a type of digital tripwire) was triggered, immediately alerting the security team — notably, the company had to rely on internal tripwires rather than catching the intrusion through the compromised pipeline itself.

**Scope, per the company's own findings:** limited to the GitHub environment — both public and private source code, plus internal repositories some teams use for operational collaboration and business information. Grafana stated no customer data, personal information, or customer production systems were affected.

**The extortion attempt:** a group calling itself "CoinbaseCartel" listed Grafana Labs on a dark web leak site on May 15, 2026 (a day before Grafana's own disclosure) and demanded a ransom to prevent the codebase's release. Grafana explicitly declined to pay, citing the FBI's stated position that paying doesn't guarantee data return and incentivizes further attacks.

**Later development (May 21, 2026):** the compromise was traced back to the broader TanStack npm supply chain attack — situating this incident within a wider wave of software supply chain compromises affecting the open-source ecosystem around the same period.

**Why this is a genuinely relevant case study:** this is a real, recent, well-documented example of a CI/CD pipeline misconfiguration (the "Pwn Request" pattern) leading to a significant credential compromise at a company whose own product is used for security/observability — a notable irony, and a clean, current illustration of supply chain and CI/CD security risk that connects directly to broader ZTIA governance themes.

---

## Competitive Landscape

| Competitor | Position vs. Grafana |
|---|---|
| **Datadog** | The most comprehensive commercial platform — single product covering metrics, logs, traces, APM, RUM, synthetics, security monitoring. Considerably more expensive at scale; strong correlation UX out of the box |
| **New Relic** | Closest like-for-like SaaS alternative to Datadog — unified experience, usage-based pricing many teams find more predictable |
| **Dynatrace** | Markets itself as AI-first, built around its proprietary "Davis" AI engine for automatic topology discovery — strong for large enterprises willing to pay a premium for reduced operational overhead |
| **Elastic Observability** | Extends the ELK stack (Elasticsearch, Logstash, Kibana); particularly strong for log analytics and compliance-driven retention |
| **OpenObserve** | Newer, cost-focused entrant explicitly positioning as a unified replacement for the entire Grafana/Prometheus/Loki/Tempo/Jaeger combination at lower operational overhead |
| **Honeycomb** | Purpose-built for distributed tracing and high-cardinality debugging specifically |

**Grafana's core positioning:** best-in-class dashboards and visualization flexibility, genuinely composable (pick and choose components rather than an all-or-nothing platform), strong fit for organizations already invested in the CNCF/OpenTelemetry ecosystem wanting full control over every layer of their observability stack. The tradeoff cited by market analysts: enterprise licensing complexity (fixed commits plus per-user/per-feature pricing can make total cost less predictable than some SaaS competitors), and storage at scale (particularly Loki and Tempo) requiring genuine backend planning expertise.

**Industry-wide context worth noting:** the observability market broadly consolidated around OpenTelemetry as the instrumentation standard by 2026 — vendors increasingly compete on storage architecture, query performance, correlation depth, and pricing model rather than on instrumentation SDK lock-in, since OTel effectively won that particular battle across the industry.

---

## ZTIA Relevance

Grafana isn't an identity security company — it's a general observability/monitoring platform. Its relevance to the broader ZTIA ecosystem thinking is more structural than direct: Grafana is a strong candidate for the **visualization/telemetry aggregation layer** that other tools in the stack (Detection platforms, Endpoint tools, even Identity & Access logs) can feed into for unified dashboarding. The 2026 move toward "advanced SOC/security analytics" inside the All-in-One suite suggests Grafana itself may be edging toward overlap with the Detection layer over time, rather than staying purely infrastructure-focused. See `ztia-ecosystem-map.md` for how this fits alongside the rest of the stack.

---

## Key Takeaways

- **Grafana's origin is genuinely organic** — a solo developer's hobby project that became a $6B company through open-source adoption, not a top-down startup pitch
- **The LGTM stack's correlated-navigation feature** (metric → log → trace, one click each) was historically commercial-only and is now table stakes in open source, largely because of Grafana's own work
- **The May 2026 GitHub breach is a strong, current, real-world CI/CD security case study** — a misconfigured GitHub Action ("Pwn Request" pattern) led to credential compromise, caught only via an internal canary token, with the intrusion later tied to the broader TanStack npm supply chain attack
- **2026 product direction is leaning toward AI-native observability and even security analytics** — Adaptive Metrics (cost optimization via ML), the Proactive Assistant (natural-language telemetry queries), and expanding SOC-adjacent capability all signal ambition beyond pure infrastructure dashboards
- **The competitive landscape has consolidated around OpenTelemetry** — differentiation now happens on storage architecture, correlation depth, and pricing model rather than instrumentation lock-in

---

## Official References

| Source | Link |
|---|---|
| Grafana Labs | https://grafana.com |
| Grafana Labs GitHub Breach Disclosure Coverage | https://www.securityweek.com/grafana-confirms-breach-after-hackers-claim-they-stole-data/ |
| The Hacker News — TanStack Supply Chain Connection | https://thehackernews.com/2026/05/grafana-github-breach-exposes-source.html |
| Grafana Labs Series D Extension Announcement | https://markets.financialcontent.com (BusinessWire, Aug 2024) |
