# Cyera — Playbook

**Document Type:** Personal Playbook / Knowledge Bridge Reference  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  

---

## What This Is

This pairs with `cyera-research.md`. That file holds objective company knowledge. This file holds personal bridges connecting AHS/healthcare experience to Cyera's specific data security problem space, plus reusable talking points.

**Customer Success framework:** see `07_4S-Customer-Success-Framework/4s-customer-success-framework.md` for the full 4S model — apply it directly rather than re-deriving it here.

---

## The Core Framing: Identity Governance vs. Data Governance

At AHS, identity governance answered **who** had access to data. Cyera answers **what** data exists and **where** it lives — before anyone even asks who has access to it. It's the layer below identity: identity governance says "this person has access to this system." Cyera says "but do you know what's actually in that system, and whether it should be there?"

**The analogy:** "Cyera is essentially an X-ray machine for your entire data estate — you finally see what's there before something goes wrong."

---

## The Central Bridge: Living the Customer's Problem

"I come from one of the most complex hybrid on-prem environments in existence — provincial healthcare with legacy Active Directory, on-prem LDAP, and a hybrid Entra Connect Sync pipeline feeding into cloud Entra ID. An environment where nobody could tell you with confidence what sensitive data lived where, who had accessed it last, or whether a departing employee's access had been fully revoked across every system. That's exactly the visibility gap Cyera solves. When talking to a healthcare CSO or a financial services CISO about why they need Cyera, this isn't reading from a case study — it's having lived on the customer side of that exact problem."

**A related observation worth using conversationally:** AHS itself would be a genuinely strong Cyera customer — a real, credible signal that the fit between background and product isn't coincidental.

---

## AHS Bridges

**Bridge 1 — PHI Data Governance = DSPM in Production:** "At AHS, I enforced PHI data governance across 160,000 users in a provincially regulated environment where a data access failure is a patient safety event, not a compliance finding. DSPM is the same discipline — discovering, classifying, and governing sensitive data — that I applied at scale every day. The difference is Cyera automates at cloud scale what we were doing manually at provincial scale."

**Bridge 2 — Identity Journey Maps to Data Access Governance:** AHS identity journey: HR ADP → IDM middleware → on-prem AD (LDAP) → Entra Connect → Entra ID → SSO. "At AHS I operated one of the most complex hybrid identity architectures in existence. Every access decision started with identity. Cyera's own framing — 'identity and data are two sides of the same coin' — is a truth lived at 160k-user scale. Cyera brings them together, which is exactly the intersection worth operating at next."

**Bridge 3 — PIPR Framework = Proactive Customer Health Monitoring:** "PIPR — Proactive Incident Pattern Recognition — was built at AHS because escalation, by definition, means the moment to prevent something has already passed. The same philosophy applies to customer success: customers who churn aren't the ones whose platform broke, they're the ones whose value gap was never caught early enough. PIPR reduced major incident volume by 40%. The same early-warning instinct applies directly to customer health monitoring."

**Bridge 4 — Connect Care Rollout = Enterprise Platform Adoption at Scale:** "Technical lead for a 9-phase platform rollout across 900+ facilities and 160,000 users. The hardest part wasn't the technology — it was adoption. Clinicians didn't care about the feature set; they cared about whether the change made their day harder or easier. That's the same muscle a data security CSE team needs — driving adoption through empathy and clear value framing, not feature lists."

---

## PHI Stakes — Why the Urgency Is Real, Not Performative

"PHI isn't abstract — it's what's been protected at 160,000-user scale for over seven years. In healthcare, a data classification failure isn't a compliance finding remediated next quarter. It's a patient safety event answered for immediately. That's the urgency brought to how data security gets approached — and it's exactly the stakes Cyera's healthcare customers operate under."

---

## On Non-Human Identity and Agentic AI

"What Cyera is building with AI Guardian and the Ryft acquisition is exactly the direction being built toward independently — the identity and observability layer for AI agents. Non-human identity isn't just service accounts anymore. Every AI agent needs its own identity, audit trail, and access governance."

---

## Sample Response Framing

**"Tell me about yourself" — opening structure:** Lead with the North Star (identity security + AI workflow + empathy-first), state AHS scale in one sentence, use the lab as hands-on proof, then pivot into genuine interest in Cyera specifically.

*Draft:* "Senior IT Operations Engineer at Alberta Health Services, spending 7+ years as the technical DRI for identity governance and Zero Trust enforcement across 160,000 clinical and administrative staff at 900+ facilities. In a healthcare environment, data governance isn't a compliance exercise — a gap means a patient safety event. Also building hands-on in the agentic AI and non-human identity space through a personal Zero Trust IaC lab. What draws me to Cyera specifically is Tamar Bar-Ilan's framing — 'identity and data are two sides of the same coin.' That intersection has already been operated at provincial scale; the goal now is doing it at Fortune 1000 scale with the platform leading the category."

**"Why Cyera?"** Three reasons worth structuring an answer around: (1) the mission is personal — coming from healthcare where data exposure is a patient safety risk, and Cyera is the platform giving enterprises the visibility to prevent that; (2) the timing — Series G at $12B, AI Guardian, the Ryft acquisition all signal an inflection point where the hardest part shifts from building the platform to helping strategic customers realize its full value; (3) the technical team — cloud-native security depth, Unit 8200 heritage, a team building the right thing the right way.

**"What do you know about DSPM?"** "DSPM answers the question every CISO couldn't answer after a breach: what data was impacted, and who had access to it? Cyera turns that into a proactive question, before the breach — discovering sensitive data agentlessly across cloud, SaaS, and on-prem, classifying it with AI at 95%+ precision, mapping access, enforcing policy. The AI Guardian extension addresses the next frontier — what happens when AI agents become the ones accessing and processing that data. For healthcare specifically, that maps directly to PHI data governance at scale."

**"Tell me about a time you drove adoption with a difficult customer"** — use the Connect Care rollout: 9 phases, 900+ facilities, 160,000 users. The hardest part wasn't the technology, it was clinicians who didn't understand why the change was happening and resisted it. The solution: a standardized readiness framework meeting each site where it was, building in a feedback loop, translating technical requirements into clinical workflow language. Result: zero-downtime go-lives across every phase.

**"How do you handle a customer who's not seeing value?"** Lead with the 4S framework's Stabilize/Adaptation stage specifically. Customers rarely churn because the product broke — they churn because they never fully adapted, so they never felt the value. The signal is usually early: low login frequency, shallow feature adoption, no stakeholder engagement in reviews. "Building early warning systems around these signals is the same instinct applied at AHS with PIPR. By the time it's a QBR conversation, it shouldn't be a surprise."

**"What's your experience with cloud security / DSPM tools?"** Honest framing, no overclaiming: "Haven't administered a DSPM platform commercially, but have operated the clinical equivalent at provincial scale — PHI data governance, Conditional Access enforcement, SCIM provisioning, identity-driven access control across a hybrid environment. The Zero Trust IaC lab demonstrates the technical concepts directly — ABAC governance, least privilege scoping, shadow AI exposure controls. Learning fast through building is the pattern, and Cyera's problem space is one already being prepared for."

**"Where do you see the data security space going?"** "Non-human identity is the next frontier. Identity governance today is built around humans — users, groups, roles. But AI agents now act autonomously, access data, spawn child agents, make decisions. 'Who accessed this data and why' is increasingly not a question about a human at all. Cyera's Ryft acquisition and AI Guardian module are exactly the right bets — traceable data access for AI agents, and visibility into what AI models see during training and inference. The companies that can answer 'what did my AI agent do with customer data last Tuesday' will win the next decade of enterprise security."

---

## Prep Checklist (Reusable Pattern for Future Companies)

- Re-read the company's own website — especially Platform, AI Security, and Resources-type pages
- Watch any available product demo videos
- Practice the "Tell me about yourself" opener out loud — 90 seconds max
- Review the lab GitHub repo — be ready to walk through it if asked
- Know the core product mechanics cold (for Cyera: Discover, Classify, Govern, Protect)
- Have two or three specific customer outcome stories ready from AHS
- Prepare two thoughtful questions for whoever is on the other side of the conversation
