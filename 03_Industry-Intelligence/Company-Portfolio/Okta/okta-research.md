# Okta — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  
**Official Reference:** https://okta.com  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Founded** | January 26, 2009 (originally incorporated as Saasure Inc., rebranded Okta in 2010) |
| **IPO** | April 7, 2017, NASDAQ: OKTA — opened at $17.00/share, raised $187M, ~$1.8B initial valuation |
| **Current scale** | 7,525 employees (May 2026); FY2026 revenue guidance $2.85–2.86B; 19,450+ customers, 4,705 generating $100K+ ACV (up 8% YoY) |
| **Category** | Identity and access management — workforce and customer identity, expanding into AI/machine identity governance |
| **Website** | https://okta.com |

---

## Founders

- **Todd McKinnon (CEO, Co-Founder)** — previously led engineering at Salesforce. Recognized the enterprise pain of IT losing control over user access as organizations adopted multiple cloud apps (Salesforce, Google Apps, Box). Wrote an internal memo to Marc Benioff titled "Proposal for a New Company," arguing for a cloud-based identity layer — that memo seeded Okta's mission and roadmap.
- **Frederic Kerrest (Co-Founder, EVP)** — worked in sales at Salesforce, met McKinnon there. Combined engineering and go-to-market instincts from the start.

---

## Origin & Funding

Launched with a ~$1.1M seed round led by Andreessen Horowitz. By 2012, Okta had ~100 employees and served 140+ customers, including Pandora and LinkedIn. The 2015 launch of Customer Identity and Access Management (CIAM) expanded Okta beyond internal workforce IAM into customer-facing identity — materially expanding total addressable market.

**Key acquisitions:**
- **Auth0** (mid-2022, all-stock deal) — significantly enhanced CIAM capabilities and developer-first identity tooling
- **Spera Security** (December 2023) — identity threat detection and posture management
- **Axiom Security** (August 2025) — Privileged Access Management (PAM); integrates into Okta Privileged Access to manage human and non-human identities (including AI agents) via Just-In-Time access, automated workflows, and compliance auditing across sensitive infrastructure like Kubernetes and databases

---

## The Core Platform

Okta positions itself as **"The World's Identity Company"** — a neutral, independent identity layer securing workforce, customer, and now AI/machine identity.

**Two core platforms:**

| Platform | Purpose |
|---|---|
| **Okta Platform (Workforce Identity)** | SSO, MFA, Universal Directory, Lifecycle Management (JML — Joiner/Mover/Leaver), Identity Governance (IGA), Privileged Access (PAM) — what internal employees use to access every app securely |
| **Auth0 Platform (Customer Identity/CIAM)** | Developer-first identity infrastructure for building login, authentication, and authorization directly into customer-facing applications — what companies embed into their own products |

### The Identity Security Fabric (ISF) — Current Strategic Positioning

Okta's core current thesis: identity and data are no longer separate problems — they're part of the same challenge and require the same solution. ISF is a unified framework providing consistent security posture, governance, and visibility for every identity, human or machine, across the entire ecosystem.

**Notable industry convergence:** this framing closely echoes Cyera's own "identity and data are two sides of the same coin" thesis — the broader identity security industry appears to be converging on this same core idea from multiple different angles simultaneously.

---

## AI Identity Security — Okta's Biggest Current Strategic Push

**The problem being solved:** AI agents are the fastest-growing identity category in the enterprise, and the least governed. 88% of organizations report suspected or confirmed AI agent security incidents, yet only 22% treat AI agents as independent, identity-bearing entities. Only 44% have any policy governing AI agents at all. Most agents today authenticate with static API keys, hardcoded secrets, and permanent access — with no central view of what agents exist, who owns them, or what they can do.

### Okta for AI Agents (GA April 30, 2026)

Answers three non-negotiable questions for the agentic era:

- **Where are my agents?** — discover known and unknown agents (including shadow AI created by employees), register them in a single directory, assign a human owner
- **What can they access?** — control connections to MCP servers, APIs, and other agents; reduce risky long-lived tokens in favor of short-lived, temporary credentials
- **What can they do?** — enforce least-privilege policies, automated governance workflows, and a kill switch to revoke access for a rogue agent with full audit trail

### Cross App Access (XAA)

An open protocol extending OAuth to secure agent-to-app and app-to-app communication. Traditional OAuth was built for human-to-app interaction (a human approves a permission screen); XAA moves authentication and authorization from ad hoc, point-to-point credentials to the identity layer itself — centrally regulated, policy-driven, auditable. Industry partners supporting XAA include AWS, Box, Google Cloud, Salesforce, and Grammarly.

**Major update — Agent SSO (GA August 24, 2026):** Okta shipped Agent SSO, bringing XAA into core Okta SSO as a first-class, no-additional-cost feature across all 20,000+ Okta SSO customers — not just an add-on or beta program. Agent SSO registers an AI agent as a first-class identity in Universal Directory and issues **short-lived, governed tokens in place of the static API keys agents normally carry**, with admins assigning and revoking agent access through the exact same workflows already used for employees.

**A genuinely significant industry milestone, distinct from Okta's own product news:** the same month, Cross App Access was adopted as the **official Enterprise-Managed Authorization extension for the Model Context Protocol (MCP) itself** — meaning XAA is no longer just an Okta protocol other vendors optionally support, it's becoming part of the actual MCP specification.

**Full governance still requires the paid tier:** Agent SSO (free, XAA-based) only covers agents that speak the XAA standard. Complete governance — including non-XAA agents, full lifecycle management, and behavioral monitoring — remains in the paid **Okta for AI Agents** tier described below.

**The sobering counterpoint, worth remembering precisely:** roughly two and a half weeks before Agent SSO's GA, security researchers demonstrated at Black Hat 2026 that simply opening a GitHub issue was enough to reach CI workflow secrets in Anthropic's and Google's own coding-agent repositories — real production systems from the two labs most invested in agent safety. One industry analysis framed it exactly right: *"The delegation protocol is close to settled, and the operational discipline around it is not close to anything."* A governed identity standard doesn't validate what a RAG pipeline retrieves, and a scoped token calling a tool that itself holds a broad token still has that broad token's effective permissions — delegation chains inherit the widest permission in the chain unless something actively narrows them.

**Also worth remembering — the ownership gap, stated plainly by industry analysts:** *"Nobody owns the agent."* Every functioning non-human identity program starts with an owner, an expiry, and a review cycle. Agents, by contrast, typically get created by a developer in the course of building something, inherit whatever credential was nearest at the time, and never appear on any formal access review — a structural gap that a protocol alone cannot close.

### Auth for GenAI

Developer-focused tooling embedding identity security directly into AI agent code — secure login for agents, agents calling APIs on behalf of users, explicit user approval for critical autonomous actions, and granular permissions for RAG document retrieval so an agent only accesses authorized content.

### Visibility vs. Observability — Where Okta Currently Sits

| Layer | Capability |
|---|---|
| **Visibility (Okta's ISF strength today)** | Discovery of every known and unknown agent; a single directory of registered agents and assigned human owners; mapping of what connections and resources each agent can reach |
| **Observability/Governance (the newer, less mature layer)** | Continuous monitoring of identity activity (human and non-human); behavioral analytics detecting abnormalities in agent behavior; automated response (revoke access, alert security, isolate an identity); full audit trail for compliance and post-incident review |

**Honest read:** Okta's stated focus is heavily weighted toward visibility and governance — discovery, ownership assignment, policy enforcement. The observability/behavioral-analytics layer exists but reads as less mature than the discovery layer. This mirrors a pattern across the broader identity industry, not something unique to Okta: visibility comes first, deep behavioral observability is the harder, later-maturing capability everywhere.

---

## Competitive Landscape

| Competitor | Position | Where Okta Differentiates |
|---|---|---|
| **Microsoft Entra ID** | Bundled with M365, dominant by default in Microsoft-centric shops | Okta is independent/neutral — no ecosystem lock-in; strongest fit for multi-cloud, heterogeneous environments |
| **CyberArk** | PAM heritage, strong on privileged access specifically | Okta has broader workforce + customer identity breadth; CyberArk is deeper but narrower |
| **SailPoint** | Deep IGA/entitlement management, ~$925M ARR, strong in regulated industries | Okta deploys faster, more developer-friendly via Auth0, stronger in born-in-cloud environments |
| **Ping Identity** | Strong access management, tied with Okta in some analyst rankings | Okta has stronger brand recognition and broader combined platform (workforce + CIAM + governance in one) |

**Gartner Magic Quadrant (Access Management):** Microsoft, Okta, and Ping Identity dominate. In the most recent evaluation, Microsoft edged ahead on execution, with Okta close behind; Okta and CyberArk tied for the highest strategy score.

**Market size:** Okta's total addressable market is estimated at $80B, with current penetration around only 3% — acknowledging significant room to grow, particularly into the fast-emerging AI/NHI governance space.

**Core differentiator to internalize:** independence and neutrality. Unlike Microsoft (which naturally favors its own ecosystem), Okta positions as the identity layer that works everywhere — any cloud, any app, any agent framework. This is the pitch to enterprise CIOs avoiding vendor lock-in.

---

## Core Values

Okta's four stated values:

1. **Love our customers** — earn their love back; listen and learn from customers, users, and champions; prioritize their priorities; deepen partnership through trust and integrity
2. **Always secure. Always on.** — build, educate, and advocate for a safer world with pride in a mission-critical role; ensure security and reliability every person, every moment; see around the corners; continuously raise the industry bar
3. **Build and own it** — solve hard problems together; own the outcome and the impact; empower each other to do the best work of our careers
4. **Drive what's next** — deliver the future of identity; innovate with courage and a learner mindset; live up to the leadership role; move with speed and rapid decisions

---

## NPI Overlay Function — Role Structure (General Reference)

A specialized, sprint-based function focused on New Product Introductions and at-risk accounts — closer in spirit to a Senior Solutions Engineer than a relationship-owning account manager.

**What it actually does:** ensures the TAM team responsible for an account has everything it needs technically to take that account through a launch successfully. Not the long-term relationship owner — the technical specialist deployed to assess readiness, unblock hard problems, and hand off cleanly so the TAM can carry the relationship forward.

**Go/No-Go, defined:** an internal readiness assessment delivered to the TAM team — is this account technically ready for the new product introduction? If it's a No-Go, what specifically needs to happen to convert it to a Go (configuration fix, platform limitation workaround, unready dependency). Diagnostic, cross-functional, enablement-focused work — not a customer-facing verdict or a sales approval.

**Key technical dimensions this function requires fluency in:**
- RPS limits (Requests Per Second) — API rate limiting
- RTO/RPO (Recovery Time Objective / Recovery Point Objective) — disaster recovery and infrastructure resilience
- Distinguishing platform defects from customer configuration gaps — the core diagnostic skill behind every Go/No-Go call
- SDLC fluency — how software gets built, tested, and shipped

---

## Technical Reference — RTO, RPO, RPS

**RTO (Recovery Time Objective):** the maximum acceptable time a system can be down before serious harm occurs. Answers "how fast do we need to be back online?" If RTO is one hour, whatever broke needs to be fully working within that hour or the target is breached.

**RPO (Recovery Point Objective):** the maximum acceptable data loss, measured backward in time from the failure. Answers "how much data can we afford to lose?" If RPO is four hours and a system crashes at 2pm, the most recent usable backup needs to be from no earlier than 10am — anything created after that and lost is a genuine gap.

**The clean distinction:** RTO is a race against downtime. RPO is a race against data freshness.

**RPS (Requests Per Second):** the maximum number of requests an API or authentication server can handle per second before throttling or failing. Every API, including Okta's, has rate limits — a ceiling on authentication/authorization calls processed per second for a given customer. A key diagnostic question this creates: is a slowdown a platform limitation (an RPS ceiling being hit) or a customer configuration issue (inefficient code making unnecessary repeated calls)?

---

## Key Takeaways

- **Okta's core strategic bet is the Identity Security Fabric** — treating identity and data governance as one unified problem, echoing the same thesis emerging independently across the identity security industry (Cyera included)
- **Okta for AI Agents (GA April 2026)** anchors on the same three questions used across this KB's ZTAI framework: where are my agents, what can they access, what can they do
- **XAA is a genuine technical innovation** — extending OAuth beyond human-to-app into agent-to-app and app-to-app, with real industry partner backing (AWS, Box, Google Cloud, Salesforce, Grammarly), and as of August 2026 adopted as MCP's own official Enterprise-Managed Authorization extension
- **Agent SSO (GA Aug 2026) productized XAA into a free, core feature** across all Okta SSO customers — but full agent governance, and coverage of non-XAA agents, still requires the paid Okta for AI Agents tier
- **The protocol is maturing faster than operational discipline** — real-world incidents (the Black Hat 2026 CI-secrets exposure in Anthropic's and Google's own repos) show that a governed identity standard alone doesn't close gaps like delegation-chain permission inheritance or unvalidated RAG retrieval
- **Visibility is ahead of observability** — Okta's discovery and governance layer is more mature than its behavioral analytics layer, a pattern true across the identity industry broadly
- **Independence is the core differentiator** — no ecosystem lock-in, unlike Microsoft's naturally Microsoft-favoring approach

---

## Official References

| Source | Link |
|---|---|
| Okta | https://okta.com |
| Okta for AI Agents | https://www.okta.com/blog/2026/04/okta-for-ai-agents/ |
| Okta — Agent SSO General Availability Announcement | https://www.okta.com/newsroom/press-releases/okta-brings-first-class-identity-to-ai-agents-with-agent-sso/ |
