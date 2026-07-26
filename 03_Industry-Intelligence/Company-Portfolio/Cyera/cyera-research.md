# Cyera — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  
**Official Reference:** https://www.cyera.com  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Category** | DSPM (Data Security Posture Management), expanding into AI data governance |
| **Total funding** | $2.3B across 8 rounds |
| **Latest valuation** | $12B (Series G, June 2026) |
| **Team size** | 1,518 employees (May 2026) |
| **IPO signal** | Appointed a President with 30+ years of tech IPO experience and a Global Legal/M&A/IPO specialist in 2026; stated target 2027 |
| **Website** | https://www.cyera.com |

---

## Founders

- **Yotam Segev (CEO)** — Age 32, born in Alon HaGalil, Israel. IDF Talpiot Leadership Academy, then Unit 8200 (Israel's elite cyber intelligence unit), where he led the Cyber Department and co-founded the unit's cloud security division. 15+ years in cybersecurity. Moved to New York to be close to customers. Vision: "Cyera is becoming the AI Trust layer."
- **Tamar Bar-Ilan (CTO)** — Age 32, from Haifa. Also IDF Talpiot → Unit 8200. Deep expertise in identity and data. Key framing that shaped the company: "Identity and data are two sides of the same coin. They are also the two fastest growing attack surfaces."
- **Yonatan Itay** — Third founding partner, manages development and Israel operations.

**Stated ambition:** "We want to be the Palo Alto Networks of data security." On AI's impact on the business: "Our business had legs before AI. But with AI, it's got wings."

---

## Origin Story

2021 — Segev and Bar-Ilan discharged from Unit 8200 at 27, both recognizing the same gap: enterprises couldn't answer the most fundamental question after a breach — "What data was impacted, and who had access to it?" The company was built to answer that question proactively, before a breach, rather than reactively after one.

**First investor:** Gili Raanan (Cyberstarts) — the same VC who made an early investment in Wiz. He introduced the founders to Doug Leone (Sequoia), who joined the board. The Unit 8200 alumni network is a real and recurring pattern across Israeli cybersecurity startups (also true of Wiz).

---

## Funding Timeline

| Round | Amount | Date | Led By | Valuation | Milestone |
|---|---|---|---|---|---|
| Seed | $4.5M | Dec 2020 | Cyberstarts | — | Early product development |
| Series A | $60M | Early 2022 | Sequoia + Accel | — | Emerged from stealth March 2022 |
| Series B | $100M | June 2023 | Accel | ~$500M | 300% customer growth |
| Series C/D | $300M | Nov 2024 | Multiple | $3B | Unicorn status |
| Series E | $540M | June 2025 | Multiple | $6B | $100M+ ARR milestone |
| Series F | $400M | Jan 2026 | Blackstone | $9B | FedRAMP High certification |
| Series G | $600M | June 2, 2026 | Evolution Equity + Temasek | $12B | Latest round |

**Notable investors:** Blackstone, Accel, Sequoia, Cyberstarts, Lightspeed, Georgian, Coatue, Greenoaks, Redpoint, Sapphire.

---

## Core Platform — DSPM

**The problem it solves:** enterprise data is scattered across thousands of cloud apps, SaaS platforms, databases, and on-prem systems. The average organization uses 100+ SaaS apps — 100+ places sensitive data can leak, with no unified visibility into where it all is or who can access it.

**Four steps:**

1. **Discover** — agentless connectors scan every data store (cloud, SaaS, on-prem) in minutes; no agents to install, no servers to provision, no multi-month deployment. Petabytes scanned in days, not months.
2. **Classify** — AI-native classification using FLAN T5 and Mistral foundation models identifies data type (PII, PHI, financial, IP, etc.) at up to 95% precision; context-aware, understanding how data is actually used rather than just pattern-matching what it looks like.
3. **Govern** — maps who has access to what; identifies excessive permissions, risky sharing, and policy violations.
4. **Protect** — DLP (Data Loss Prevention) capabilities enforce policy; alerts and remediates when sensitive data is exposed, overshared, or accessed outside policy.

**The agentless advantage:** deployment measured in days, not months. A public case study (Carmoola, a UK-based fintech car finance platform) documents a 3-day total implementation — 1 day configuration, 2 days scanning, with all data analyzed and classified by the end. Competitors like BigID and Varonis typically require agent installation and considerably longer setup.

**Additional cited metrics:** actionable insights within 48–72 hours (vs. weeks for legacy hardware-based solutions); classification discovers up to 40% more sensitive data than typical approaches while reducing false positives; feeds enriched data-risk signals directly into SIEM, CSPM, and SOAR tooling so analysts can focus on the alerts that matter most.

---

## AI Guardian — Securing the AI Layer

A specific module within the Cyera platform (not Cyera itself) launched as AI adoption created an entirely new attack surface. Extends the same discover/classify/govern/protect model specifically to AI workloads:

- **AI training datasets** — scanned before model training to ensure no PII, PHI, or sensitive IP is accidentally baked into a model (once embedded, difficult to remove)
- **Vector databases** (Pinecone, Weaviate, Postgres pgvector) — where AI systems store compressed "memories" (embeddings); sensitive data embedded here can potentially be retrieved via prompt injection
- **Model artifacts in cloud storage** — trained model files sitting in S3/Azure Blob Storage, often forgotten and over-permissioned
- **Inference logs** — every query against an AI model generates logs, which can contain customer data included in the original prompt

**The core stat driving this:** an estimated 34.8% of corporate data fed to AI is sensitive — most organizations have no visibility into what's actually going into their LLMs.

---

## Recent Product Launches (RSAC 2026)

- **Browser Shield** — prompt-level protection in public AI tools; prevents sensitive data from being pasted into ChatGPT, Claude, or other public AI tools, operating at the browser layer
- **Data Lineage** — tracks how files move across the organization, whether moved by humans or AI agents, with a full audit trail
- **Cyera MCP** — lets security teams build custom data security agents on top of Cyera's data visibility layer using Model Context Protocol

### Ryft Acquisition (April 2026)

Acquired to provide traceable data access specifically for AI agents — tracking what agents access and when, giving full observability into agentic AI workflows. Positions Cyera directly at the intersection of data security and AI agent governance.

---

## The Problem Cyera Solves

**Before Cyera, in the aftermath of a breach, a CISO typically couldn't answer:**
- What data was taken? (Unknown — data was everywhere)
- Who had access to it? (Unknown — no unified access map)
- Was it compliant? (Unknown — no classification)
- Did AI ingest it? (Unknown — no AI data lineage)

**Cyera's bet:** answer all four questions before a breach occurs, not after.

**The AI acceleration problem specifically:** AI adoption is outpacing security governance — employees feeding customer data into public AI tools (shadow AI), organizations training internal models on sensitive datasets, AI agents deployed with excessive permissions (NHI sprawl), and LLMs that can potentially surface training data via prompt injection. Cyera's positioning: the platform that answers "what data can your AI see, and should it?"

---

## Key Terminology

| Term | Definition |
|---|---|
| **PII** | Personally Identifiable Information — name, email, phone, address, SSN, DOB, passport number. Regulated under GDPR, PIPEDA (Canada), CCPA (California) |
| **PHI** | Protected Health Information — a healthcare-specific subset of PII, connecting a person to health status, medical records, treatment history, insurance, or payment for care. Regulated by HIPAA (US) and provincial health information acts (Canada) |
| **IP (in this context)** | Intellectual Property — source code, product roadmaps, trade secrets, proprietary algorithms, internal research, unreleased designs. The category with existential competitive stakes if exposed |
| **NHI** | Non-Human Identity — service accounts, API keys, AI agents |
| **Shadow AI** | Employees using unauthorized AI tools with company data |
| **Data Lineage** | Tracking how data moves across people, systems, and AI agents |
| **Prompt Injection** | Manipulating an AI system into revealing training data or unintended information |

---

## Competitive Landscape

| Competitor | Strength | Where Cyera Differentiates |
|---|---|---|
| **Varonis** | Deep behavioral analytics, strong on-prem file share coverage | Agent-heavy deployment, weeks to stand up vs. Cyera's 3-day agentless model; Cyera classification accuracy is comparatively higher |
| **BigID** | Broad data governance beyond DSPM, strong compliance tooling | More complex deployment, notably higher starting cost, more consultant-dependent |
| **Securiti** | Strong compliance and privacy automation | Narrower coverage, less AI-native |
| **Sentra** | Cloud-native DSPM | Smaller, less coverage breadth, newer entrant |
| **Microsoft Purview** | Built into M365, no additional licensing | Limited to Microsoft ecosystem, weaker multi-cloud coverage, not AI-native |
| **Wiz (AI-SPM)** | CNAPP leader expanding into AI security | Different problem entirely — cloud posture (CNAPP) vs. data posture (DSPM); Wiz doesn't own the data layer itself |

**Cyera's one-line differentiation:** fastest deployment, highest classification accuracy, and the only platform natively connecting data security and AI agent governance.

**Industry recognition:** named a Leader in Sensitive Data Discovery and Classification (Forrester, Q2 2026 Wave); listed in Gartner's DSPM Market Guide; CNBC Disruptor 50 — top cybersecurity company, ranked in the top 10 alongside Anthropic, OpenAI, and Databricks.

---

## ZTIA Layer Placement

**Layer: Discovery & Context — Data.** Cyera discovers and classifies sensitive data across environments — structurally the same category of problem as Dosu's knowledge-grounding work, just applied to data instead of codebase context. See `ztia-ecosystem-map.md` for the full layer breakdown.

---

## Key Takeaways

- **Cyera's core bet:** answer "what data exists, where does it live, who can access it, is it compliant" proactively, before a breach — not reactively after one
- **The agentless, days-not-months deployment model** is a genuine and repeatedly cited differentiator against legacy competitors
- **AI Guardian and the Ryft acquisition** extend the same discover/classify/govern/protect model specifically to AI training data, vector databases, model artifacts, and agent access — positioning Cyera directly in the agentic AI governance conversation, not just traditional data security
- **34.8% of corporate data fed into AI is estimated sensitive** — the core stat justifying the AI Guardian product line
- **Founders' Unit 8200 background** is a recurring, credibility-relevant pattern across Israeli cybersecurity startups (also true of Wiz)

---

## Official References

| Source | Link |
|---|---|
| Cyera | https://www.cyera.com |
| Cyera — Carmoola Case Study | https://www.cyera.com (on-prem comparison page) |
