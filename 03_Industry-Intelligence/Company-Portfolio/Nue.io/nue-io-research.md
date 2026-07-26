# Nue.io — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  
**Official Reference:** https://nue.io  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Founded** | 2019, San Mateo, CA (formerly Ruby IO) |
| **Name origin** | "Nue" derives from "Revenue" |
| **Total funding** | $35M across 3 rounds |
| **Latest round** | $20M Series A (Jan 2025), led by Inovia Capital |
| **Team size** | ~104 employees, distributed across 9 countries, 5 regions |
| **Growth** | 3x year-over-year sales growth in 2024 |
| **Category** | Revenue Lifecycle Management (CPQ + billing + renewals unified) |
| **Website** | https://nue.io |

---

## Founders & Origin

- **Mark Walker (CEO)** — serial entrepreneur, 20+ years in SaaS/CRM/ERP; former CEO of Strongpoint (acquired by Netwrix), COO at ScribbleLive (acquired by Rock Content)
- **Tina Kung (CTO)** — 20+ years in CPQ and billing; former engineering leadership at Salesforce CPQ, Zuora, and Oracle CPQ. Notably, she built the systems Nue is now disrupting — meaning she has direct, first-hand knowledge of exactly where they break
- **Kate McCullough** — Co-founder, go-to-market focus

**Founding story:** Tina, having sat inside Salesforce CPQ and Zuora, watched customers suffer through fragmented, complex, expensive implementations repeatedly — and asked why B2B software couldn't feel as simple as Amazon's consumer experience. Nue was built by insiders who understood exactly what was broken in the category.

---

## Funding Timeline

| Round | Amount | Year | Led By |
|---|---|---|---|
| Seed | $6M | 2022 | Information Venture Partners |
| Seed Extension | $9M | 2023 | Bluefish Capital + NJP Ventures |
| Series A | $20M | Jan 2025 | Inovia Capital |

---

## The Problem Being Solved

**CPQ (Configure, Price, Quote):** the process of creating accurate sales quotes for complex products and pricing structures. A SaaS company with dozens of pricing tiers, usage-based add-ons, annual/monthly options, enterprise discounts, and renewal terms creates real complexity. Legacy tools (Salesforce CPQ) typically require months of expensive consultant-led implementation, complex custom code for every pricing change, disconnected billing systems, and manual finance reconciliation — the practical result being inaccurate quotes, slowed deals, revenue leakage, and inaccurate books.

**What Nue actually solves — Revenue Lifecycle Management:** unifying the entire quote-to-revenue journey (Quote → Order → Contract → Billing → Revenue Recognition → Analytics) in one platform, natively built on Salesforce rather than bolted onto it.

**Key differentiators:**
- No-code interface — RevOps teams change pricing without engineering involvement
- Deep, native Salesforce integration
- Lifecycle Manager — automated customer upgrades, renewals, expansions
- "Everything Billing" — handles subscription, usage-based, and hybrid revenue models
- Real-time analytics — revenue visibility without manual reporting
- **Nue AI** (launched October 2025) — AI-powered revenue operations

**Why "Revenue Lifecycle" rather than just "CPQ":** traditional CPQ tools stop at the quote. Nue extends through new business, expansions, renewals, graceful cancellation/retention workflows, and automated revenue recognition — giving finance accurate, compliant numbers without manual reconciliation.

---

## Market & Customers

**Target market:** B2B SaaS companies, typically 50–2,000 employees, in growth mode — too complex for spreadsheets, too nimble for legacy enterprise tooling. Deep Salesforce integration is a core selling point for this segment specifically.

**Market size:** the CPQ and billing category is roughly a $4B global market, currently dominated by Salesforce CPQ and Zuora (both complex, expensive, consultant-heavy) with smaller players (DealHub, Chargebee, Maxio) splitting the remainder. Nue's Series A was explicitly raised to fund capturing a meaningful share of that market over 3-4 years.

**Notable customers:**

| Customer | Why They're Relevant |
|---|---|
| **OpenAI** | Headline customer — validates the platform handles genuine enterprise complexity (usage-based API billing, enterprise contracts, research tiers) at extreme scale and growth speed |
| **Glean** | $4.6B-valued AI enterprise search company — represents Nue's ideal customer profile: fast-growing AI company with complex enterprise pricing |
| **iCapital** | Alternative investment platform, $880B in platform volume — demonstrates Nue can handle regulated, compliance-heavy financial services billing |
| **SonarSource** | Code quality/security platform — demonstrates handling of developer-tool pricing complexity (per-line-of-code, seats, enterprise mixed models) |
| **Obsidian** | Privacy-first, developer-beloved note-taking tool — demonstrates fit for technical, privacy-conscious customer bases, not just traditional enterprise sales orgs |
| **Procurify, Iodine, Mews, i3 Verticals** | Additional named customers spanning RevOps tooling, healthcare AI, hospitality tech, and government technology |

---

## Competitive Landscape

| Competitor | What They Do | Nue's Positioning |
|---|---|---|
| **Salesforce CPQ** | Dominant, complex, built into Salesforce | Simpler, cheaper, faster to implement — avoids extensive consulting engagements |
| **Zuora** | Subscription billing specialist | Nue unifies CPQ + billing natively; Zuora typically requires separate integration work |
| **DealHub.io** | CPQ + subscription billing | Similar category; Nue claims stronger native Salesforce integration |
| **Chargebee** | Billing-focused | Chargebee is billing-first; Nue covers the full revenue lifecycle |
| **Maxio** | SaaS billing and analytics | Nue offers broader CPQ + lifecycle management scope |
| **PandaDoc** | Document/proposal-focused | A document tool rather than a full revenue platform |

**CEO's explicit positioning:** "the go-to alternative to Salesforce CPQ and Zuora."

**Honest limitations (for credibility, not talking points against them):** newer entrant with less brand recognition than Salesforce/Zuora; advanced features like complex channel management still maturing; smaller integration ecosystem than established players; best fit currently for companies with relatively straightforward sales structures.

---

## Culture & Values

**Stated core philosophy — Empathy + Excellence:**
- **Customer Empathy** — "We stay close to our customers, listen deeply, and build a platform that reflects their evolving needs"
- **Team Empathy** — "We treat each other as people first, teammates second"
- **Brilliantly Nue** — "Curious, thoughtful people who think big, work smart, care deeply. No room for ego here"

**Work style:** remote-first and global (9 countries, 5 regions), high-trust/high-ownership, async-first by necessity given the distributed team, fast-paced startup energy reflecting the 3x 2024 growth rate.

---

## The IT Function at This Stage

At ~104 people across 9 countries, the IT function is realistically 1–2 people total — a build function, not a maintenance function.

**Likely existing stack (based on company size/stage and typical patterns):** an IdP for SSO (Okta or similar), Google Workspace, Jamf for Mac management, Slack, Atlassian tooling, GitHub, and Salesforce as the internal platform (since it's also the product itself).

**What needs to be built at this stage, typically:**
- Proper joiner/mover/leaver automation (often still manual pre-Series-A)
- RBAC and least-privilege access review processes
- SOC 2 controls (a genuine requirement given enterprise customers like OpenAI and iCapital)
- Endpoint hardening — baseline configs, patching, MDM policy
- SaaS governance — license optimization, vendor review
- Documentation and runbooks — frequently nonexistent at this stage

---

## What CPQ Means for an Internal IT Function Specifically

Most IT roles support users on generic productivity tools. At a company like Nue, internal users are the RevOps, Sales, and Finance teams living inside Salesforce all day — meaning IT support requires real fluency in Salesforce SSO, permissions, and integrations. Additionally, the people building the product use the same platform customers buy — an internal outage is simultaneously an IT issue and a product credibility issue. Every new customer integration (Stripe, NetSuite, HubSpot, etc.) adds another SaaS surface touching identity and access governance.

---

## SOC 2 — Comprehensive Technical Reference

### What SOC 2 Is and Why It Exists

SOC 2 (System and Organization Controls 2) is a security compliance framework created by the AICPA specifically for technology and cloud service companies. When enterprises buy SaaS software, they need independent proof the vendor handles their data securely — SOC 2 is that proof, issued after an independent auditor reviews the vendor's controls.

**Why a company like Nue needs it specifically:** handling revenue data (pricing, contracts, billing) for enterprise customers whose own security teams require SOC 2 before signing — without it, enterprise deals simply don't close.

### SOC 2 Type 1 vs. Type 2

| | Type 1 | Type 2 |
|---|---|---|
| **What it proves** | Controls are *designed* correctly, at a point in time | Controls *operated effectively* over a period (typically 6-12 months) |
| **Analogy** | A building inspector reviewing architectural plans before construction | The inspector returning after 6 months to verify the building was actually maintained properly |
| **Timeline** | 2-4 months to prepare and complete | 6-12 month audit period plus reporting time |
| **When companies pursue it** | Early stage — "we have security controls" | Growth stage — "our controls work consistently"; enterprise customers generally prefer this |

### The Five Trust Service Criteria (TSC)

| Criterion | What It Requires | Typical IT/Endpoint Ownership |
|---|---|---|
| **Security** (the mandatory one) | MFA enforced, SSO with no orphaned accounts, regular access reviews, managed/patched/encrypted endpoints, documented incident response | Very high — this is frequently the core of an IT/security-adjacent role |
| **Availability** | Uptime monitoring, incident response/recovery procedures, redundancy planning, SLA commitments met | Partial — supporting internal tool availability; primary ownership often sits with engineering for the actual product |
| **Processing Integrity** | Data processing is complete, accurate, and authorized | Low for IT specifically — more an engineering/product concern |
| **Confidentiality** | Data classification, least-privilege access to confidential data, encryption at rest/in transit, documented handling procedures | High — this is fundamentally identity and access governance work |
| **Privacy** | Personal information collected/used/retained/disclosed appropriately, GDPR/CCPA alignment | Low for IT specifically — primarily legal and product territory |

### Architecting for SOC 2 — Four Pillars

**Pillar 1: Identity is the Perimeter.** Every Security control starts with identity. A single IdP as the source of truth, SSO for every SaaS app (no app with its own username/password), universally enforced MFA, SCIM provisioning (access follows the person automatically), and Conditional Access (right access, right device, right context).

**Pillar 2: Evidence by Default.** Type 2 requires proof controls operated consistently — the right architecture generates that evidence automatically rather than requiring a scramble when the auditor arrives: every access change logged automatically, an ITSM platform recording every change/incident/request, infrastructure-as-code with Git history functioning as the change log, scheduled (not ad hoc) access reviews, and regularly exported (not on-demand) compliance reports.

**Pillar 3: Least Privilege by Design.** Auditors specifically look for over-provisioned access. The architecture should make least privilege the default: defined role profiles per function, no default admin access, time-limited elevated access for specific tasks, regular (minimum quarterly) access reviews, and same-day offboarding automation.

**Pillar 4: Endpoint Trust.** An unmanaged personal device accessing company systems is itself a SOC 2 finding. Required: MDM enrollment for all corporate devices, hardened baseline configurations (disk encryption, screen lock, auto-update), Conditional Access blocking non-compliant devices, full asset inventory, and EDR (Endpoint Detection & Response) at the device level.

### What Auditors Actually Ask For

| Control Area | Evidence Requested | How It Gets Built |
|---|---|---|
| Access Management | Provisioning/deprovisioning logs, access review records | SCIM logs, quarterly access review tickets |
| MFA Enforcement | Enrollment reports, policy configuration | IdP MFA reports, Conditional Access policy exports |
| Endpoint Management | Device inventory, compliance reports, encryption status | MDM device and compliance reports |
| Change Management | Change tickets, approvals, rollback procedures | ITSM change requests, infrastructure-as-code Git history |
| Incident Response | Incident records, RCA documents, resolution timelines | ITSM incident tickets, post-mortems |
| Vendor Management | Security reviews, contract records | SaaS vendor inventory, risk assessments |
| Background Checks | HR confirmation | HR records (supported by IT, owned by HR) |

### A Realistic SOC 2 Roadmap at Series A Scale

- **Months 1–2:** discovery and gap assessment — map current controls to Security criteria, identify what's missing/manual/undocumented, prioritize by risk
- **Months 3–4:** control implementation — enforce MFA, deploy SSO across critical SaaS apps, build MDM hardened baselines, build JML automation, document runbooks
- **Months 5–6:** evidence collection and Type 1 — first access reviews run, compliance reports exported, Type 1 assessment engaged, findings addressed
- **Months 7–18:** operate for Type 2 — consistent evidence generation, quarterly access reviews, regular vendor reviews, incident documentation, auditor collects evidence across the period

---

## EDR (Endpoint Detection & Response) — Common Tools

| Tool | Positioning |
|---|---|
| **CrowdStrike Falcon** | Market leader, agent-based, AI-driven threat detection |
| **SentinelOne** | Strong competitor, autonomous response capability |
| **Microsoft Defender for Endpoint** | Built into M365, strong fit for Microsoft-heavy stacks |
| **Jamf Protect** | Mac-specific EDR, pairs naturally with Jamf MDM |

---

## Recognizing Scope Creep in Early-Stage Job Descriptions

A useful general pattern, illustrated well by this specific role's JD: language like "primary IT owner for endpoint security, identity security, SaaS hardening," "vulnerability management remediation," "incident response for account compromise/suspicious activity/vendor breaches," and "customer security questionnaires" collectively describes a full SecOps/GRC function, not a standard IT Engineer role — often signaling a small team trying to have one hire quietly absorb an entire security function without formally titling or compensating it as such.

**A reasonable minimum viable structure for a ~100-person Series A SaaS company facing real enterprise customers and an active SOC 2 push** typically includes 2-3 IT engineers, at least one dedicated security engineer, and either a GRC analyst or a fractional/virtual CISO. Wearing many hats is normal at 20-30 person scale; at 100+ person scale with major enterprise clients and an active compliance push, the absence of dedicated security ownership is a genuine structural gap — and a useful thing to identify and ask about directly in any conversation about a role like this.

---

## Quick Reference

| Term | Plain English |
|---|---|
| CPQ | Configure, Price, Quote — creating accurate sales quotes |
| Revenue Lifecycle Management | The full journey from quote to cash to renewal |
| RevOps | Revenue Operations — the team managing sales/finance systems |
| Quote-to-cash | From creating a quote to collecting payment |
| Usage-based billing | Charging based on actual customer usage |
| SOC 2 | Security compliance framework for SaaS companies |
| Type 1 / Type 2 | Point-in-time design check vs. sustained operational proof |
| Trust Service Criteria | The 5 categories SOC 2 evaluates |
| SCIM | Automated provisioning — access follows identity automatically |
| Conditional Access | If/then policy — right device + right identity = access granted |
| EDR | Endpoint Detection & Response — device-level threat detection |
| Linear | Modern, lightweight project management tool popular with startups |
| Workato/n8n | Low-code automation platforms for connecting SaaS apps |

---

## Official References

| Source | Link |
|---|---|
| Nue.io | https://nue.io |
