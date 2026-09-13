# Lumos — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  
**Official Reference:** https://www.lumos.com  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Founded** | 2020, San Francisco, CA |
| **Stage** | Series B |
| **Total funding** | $65M+ across 4 rounds |
| **Latest round** | $35M Series B (May 2024), led by Scale Venture Partners, with Andreessen Horowitz, Harpoon Ventures, Neo participating |
| **Team size** | ~160 employees (2026) |
| **Category** | Autonomous Identity Platform — IGA (Identity Governance and Administration) rebuilt for the agentic AI era |
| **Notable customers** | Pinterest, GitHub, Anduril, MongoDB, Major League Baseball, Roku, Deel, Drata, ChargePoint |
| **Recognition** | Forbes America's Best Startup Employers 2026 |
| **Website** | https://www.lumos.com |

---

## Founders & Origin

**Andrej Safundzic (CEO), Alan Flores Lopez, and Leo Mehr** — met in a Stanford class focused on ethics, public policy, and technological change. The founding insight: few people, particularly in the corporate sector, have real control over their own digital identities.

**Founding thesis:** authorization decisions were identified as one of the first enterprise workflows ripe for full end-to-end automation — straightforward in principle, but extremely high-frequency with real business impact when done wrong.

**Growth trajectory:** revenue grew 9x between the company's stealth exit and the Series B round; large enterprise customers Lumos serves use an average of 650 applications, with IT and Security teams historically managing that sprawl in separate silos.

---

## The 2026 Strategic Pivot

Lumos explicitly repositioned from "SaaS management and access reviews" into an **"Autonomous Identity Platform for the agentic era."** This is a meaningful strategic bet: that AI agents become first-class identities requiring the same governance rigor as human users.

**Company framing:** "Traditional IGA tools just move the spreadsheet into a web app. We didn't just build a tool, we built an analyst."

---

## The Four Core Pillars

### 1. JML Lifecycle Automation (Joiner, Mover, Leaver)

Lifecycle events flow directly from the HRIS. Joiners get exactly what they need on day one, movers don't accumulate excess access over time, and leavers are fully offboarded with licenses automatically reclaimed — operating at scale across 300+ SaaS applications.

### 2. Agentic User Access Reviews (UARs) — Powered by Albus

The flagship AI capability. Albus analyzes dozens of data points per identity — role, department, access sensitivity, last activity, peer group alignment, Segregation of Duties (SoD) conflicts — separating low-risk access from genuine anomalies. Instead of a manager rubber-stamping 400 line items in a spreadsheet, Albus does the first pass and surfaces only the handful that actually need human judgment.

**Results cited:** access reviews accelerated by up to 70%, up to 6x faster completion overall.

### 3. NHI Governance (Non-Human Identity)

Discovers every machine identity — service accounts, API keys, AI agent credentials — assigns owners, decommissions dormant accounts, right-sizes over-scoped access. Notable context: service accounts and bots now outnumber human users by roughly 20 to 1 in many organizations, yet historically carry no documented ownership.

### 4. Just-in-Time Access

Both humans and AI agents request access through Slack, an IT portal, or MCP. Access is granted just in time, checked against policy, and revoked on schedule — no standing privileges, no manual off-hours access requests.

---

## Albus — The AI Identity Agent

Albus operates continuously as the observability layer sitting on top of Lumos's visibility layer:

- Scopes access reviews — certifies the obvious, investigates the ambiguous
- Monitors for risk signals (e.g., a dormant service account suddenly accessing customer data)
- Proposes living RBAC/ABAC roles based on real, observed access patterns rather than job titles
- Generates audit-ready evidence automatically
- Handles access requests that clearly match existing policy without human intervention

**Product naming note:** Albus is a deliberate nod to Harry Potter's Albus Dumbledore — the wisest advisor figure who guides others toward the right decision while letting them retain the final judgment call. The parallel to the product's design (surface the obvious, escalate only the genuinely ambiguous to a human) appears intentional given the framing throughout Lumos's own materials.

---

## Visibility vs. Observability — The Clean Distinction

| Visibility (static, what Lumos shows) | Observability (continuous, what Albus does) |
|---|---|
| Every identity — human, NHI, AI agent — and every application they access | Real-time monitoring of access patterns, not just quarterly audit cycles |
| Permission levels and entitlements across 300+ SaaS integrations | Anomaly detection — flags behavior deviating from peer group norms |
| Shadow IT discovery — unauthorized apps outside governance | Risk signal surfacing — issues flagged before they escalate to incidents |
| Unused and orphaned accounts | Continuous entitlement drift detection — access appropriate 6 months ago that isn't now |
| License waste — spend on access nobody needs | Autonomous remediation — Albus acts on findings without waiting for a human to initiate every fix |

---

## The Honest Competitive Picture

### What Lumos Does Better Than Most

- Fastest deployment in the IGA category — days, not months
- Slack-native workflows — meets users where they already work
- Agentic UARs are genuinely first-of-kind — no direct competitor has an equivalent to Albus
- Consistently stronger UX/ease of use vs. legacy IGA (SailPoint, Saviynt)
- 300+ integrations — among the broadest SaaS coverage in the category

### Where Lumos Has a Genuine Ceiling

**1. Depth below the IdP.** Lumos sees what the identity provider knows — group memberships, last login, app assignments. It doesn't go below that into fine-grained entitlements inside applications. It knows a user has access to Salesforce; it doesn't know which specific records, fields, or actions that access permits.

**2. Hybrid and on-premises coverage.** Built for SaaS-native environments. Complex hybrid environments — legacy Active Directory, on-prem LDAP, systems that don't support modern identity federation protocols — are harder for Lumos to govern well.

**3. The data visibility gap.** Lumos tells you who has access to which apps. It does not do DSPM — it doesn't tell you what data is inside those apps or whether it's exposed. Complementary to a platform like Cyera, not competing with it; a CISO wanting a complete risk picture needs both.

**4. The enterprise regulated market.** Current logos (Pinterest, GitHub, Roku) are impressive but tech-native SaaS companies. Regulated enterprises — healthcare, financial services, government — require deeper compliance controls, on-prem coverage, and audit frameworks Lumos is still building toward. This is the stated growth frontier.

---

## Competitive Landscape

| Competitor | Position vs. Lumos |
|---|---|
| **SailPoint, Saviynt (legacy IGA)** | Lumos: ~7x faster deployment, ~80% lower cost of ownership, modern UX, AI-native. Legacy players go deeper into entitlements/role mining/SoD detection at a granular level, but take months to deploy at significant cost |
| **C1** (formerly ConductorOne) | Closest direct competitor — similar AI-native, fast-deploying positioning. C1's July 2026 Launch Week (Shadow AI Discovery, Agentic Vault, Runtime Governance, Agentic Security & Intelligence) expanded it well beyond core IGA — see `c1-research.md` for the full head-to-head, which concludes neither has a clean structural advantage in the core Identity & Access layer |
| **Okta IGA** | Okta is the identity provider itself; Lumos positions as identity-provider agnostic — a neutral governance layer on top of any IdP |
| **Zluri** | Lumos has deeper governance depth; Zluri has broader shadow IT discovery |
| **Linx Security (emerging)** | Goes deeper on fine-grained entitlements directly from connected apps; newer and smaller, gaining traction as a "modern SailPoint" |
| **CyberArk** | Different buyer — PAM specifically, governs privileged/admin-level accounts at the entitlement level |
| **Veza** | Distinct thesis — an authorization graph mapping who can do what to which data across every system; very deep entitlement visibility |

**The honest summary:** deep entitlement visibility below the IdP is traditionally the domain of legacy IGA (SailPoint, Saviynt) or emerging specialists (Linx, Veza). Lumos chose speed and ease of use over that depth — a different tradeoff serving a different buyer, not a strictly worse approach.

---

## The Upstream Data Insight

A sharp analytical point about how identity governance actually fails: **the answer to automating identity is better-quality upstream data.** Identity governance is only as good as the data feeding access decisions — if the HRIS has wrong department codes, wrong job titles, wrong manager relationships, RBAC policies built on top of that data will be wrong regardless of how good the governance platform itself is. Garbage in, garbage out.

**Where this connects to Cyera:** Cyera doesn't fix the upstream identity data problem (that's an HRIS/IdP problem), but the two platforms are complementary. Lumos answers "who has access to what." Cyera answers "what's actually inside what they have access to, and is it exposed." Example: Lumos flags "this contractor has access to 14 applications." Cyera adds "three of those applications contain customer PII, one contains source code, two haven't been accessed in 90 days." Together, that's the complete risk picture neither platform provides alone.

**The prevention vs. cure framing:** the legacy IGA approach discovers what access exists after the fact, then governs it reactively — necessary because access sprawl already happened without governance from the start. Lumos's bet is the opposite: get the upstream right (clean HRIS attributes, ABAC policies defined early, JIT access so standing privileges never accumulate) and the deep-entitlement-scanning problem never gets bad enough to need solving in the first place.

**The honest counterpoint:** Lumos's growth market is overwhelmingly greenfield Series A–D SaaS companies without 15 years of accumulated entitlement debt — they need prevention, not cure. That's a coherent bet even if it concedes the SailPoint-replacement market (with its legacy entitlement debt) to others.

---

## RBAC vs. ABAC — Technical Reference

- **RBAC (Role-Based Access Control)** — role-based: "everyone in Engineering gets access to GitHub." Clean and simple; breaks down at scale as roles multiply and people accumulate access across internal moves.
- **ABAC (Attribute-Based Access Control)** — attribute-based: "anyone whose department is Engineering AND whose level is Senior AND whose project is X gets access to Y." More precise, but harder to manage without real automation.

Albus is specifically designed to bridge the two — analyzing real access patterns (what people actually use, not what their role nominally implies) and proposing living RBAC/ABAC roles that reflect operational reality rather than org-chart theory.

---

## The Five Layers of Agentic Identity Security

A useful cross-company framework describing where different identity security players sit relative to each other:

| Layer | Representative Company | What They Govern |
|---|---|---|
| **Identity Provider** | Okta | Authentication and authorization for agents |
| **Network** | Tailscale (via Aperture, ACL tags) | What agents can reach |
| **Credentials and Secrets** | 1Password (Unified Access) | What credentials agents hold |
| **Governance** | Lumos | Whether agents have the right access, and whether it's being reviewed |
| **Data** | Cyera | What agents are actually touching, and whether they should be |

**Simplified:** IdP answers "who you are." IGA (Lumos) answers "whether your access is appropriate." An identity-aware network answers "what you can reach." This maps closely onto the broader ZTAI layer framework already built out elsewhere in this KB — see `ZTAI-ecosystem-map.md`.

---

## Key Metrics

- Access reviews accelerated by up to 70%
- Standing access reduced by 80%
- One customer case: time to access dropped from 79 hours to 45 minutes
- One fintech customer saved $3.5M in unused licenses
- 7x faster deployment than legacy IGA
- 80% lower cost of ownership vs. SailPoint/Saviynt
- 300+ SaaS integrations
- 96% of organizations experienced an identity-related incident in the past year (Lumos 2026 research)

---

## Key Product Names

- **Albus** — the AI identity agent; does the analytical work, surfaces judgment calls to a human
- **Identity Agent Force** — a broader team of agents launched March 2026
- **Agentic UARs** — first-of-kind autonomous access reviews
- **Identity Intelligence** — the visibility and risk analysis layer

---

## ZTAI Layer Placement

**Layer: Identity & Access (Governance specifically)** — Lumos answers whether an identity's access is appropriate and whether it's actively reviewed, distinct from Okta/Entra ID which answer whether the identity itself is authenticated. See `ZTAI-ecosystem-map.md` for the full layer breakdown.

---

## Key Takeaways

- **Lumos's 2026 pivot** — from SaaS/access management into a full Autonomous Identity Platform — bets that AI agents become first-class governed identities, not just service accounts
- **Albus is a genuine first-of-kind capability** — no direct competitor currently offers an equivalent agentic UAR analyst
- **The real architectural ceiling is depth below the IdP** — Lumos knows access exists, not what that access permits inside an application; SailPoint, Saviynt, Linx, and Veza occupy that deeper layer instead
- **The upstream data insight is the sharpest structural point** — governance automation is only as good as the HRIS/IdP data feeding it; prevention (clean data + JIT access) is a different bet than cure (deep entitlement scanning after sprawl already happened)
- **Lumos and Cyera are complementary, not competing** — one answers who has access, the other answers what's actually exposed
- **The Five Layers framework** is a clean way to place Lumos relative to Okta, Tailscale, 1Password, and Cyera simultaneously

---

## Official References

| Source | Link |
|---|---|
| Lumos | https://www.lumos.com |
| Lumos Series B Announcement | https://www.lumos.com/blog/lumos-secures-series-b-to-launch-the-unified-access-platform |
| TechCrunch — Lumos Series B Coverage | https://techcrunch.com/2024/05/23/lumos-helps-companies-manage-their-employees-identities-and-access/ |
| Tracxn — Lumos Company Profile | https://tracxn.com/d/companies/lumos |
