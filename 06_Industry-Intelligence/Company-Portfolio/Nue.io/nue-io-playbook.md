# Nue.io — Playbook

**Document Type:** Personal Playbook / Knowledge Bridge Reference  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  

---

## What This Is

This pairs with `nue-io-research.md`. That file holds objective company and technical knowledge. This file holds personal bridges connecting AHS/Apple experience to Nue's specific context, plus reusable talking points.

---

## The Sharpest Analogy: Revenue Lifecycle as Visibility + Observability

"Nue is doing for revenue operations what identity lifecycle management does for IT — instead of managing each step separately, the entire lifecycle unifies into one system with one source of truth. A quote is the beginning of a relationship, not the end. Customer Success IS Customer Revenue — that's genuinely the platform's entire thesis. Nue brings visibility and observability to that revenue journey the same way identity governance brings visibility to who accesses what across an enterprise."

**The full version:** "Nue handles Revenue Lifecycle the way IT handles Customer Success — a quote is the beginning of the journey, not the end. Customer Success IS Customer Revenue. Nue brings visibility and observability to that entire journey, the same way identity governance brings visibility to who accesses what across the enterprise."

---

## The Empathy Bridge — Customer Diversity

"What's compelling about Nue's customer base is the diversity of complexity — from OpenAI's usage-based AI pricing to iCapital's regulated financial products, SonarSource's developer tool licensing to Obsidian's privacy-first subscription model. Every customer has a different revenue motion but the same underlying pain: fragmented systems that don't reflect how the business actually works. That's the same empathy-first problem-solving already applied in IT — understanding the human workflow before touching the technology."

---

## The Opening Framing — Why Nue's Problem Is Genuine

"Nue isn't reinventing Salesforce — it's solving a pain that's existed so long everyone decided to just live with it. Unlike a legacy VPN, where at least convenience gets traded for security, fragmented CPQ and billing systems offer nothing to trade. No convenience. Just consequences — slow implementations, revenue leaks, manual reconciliation, pricing changes that take weeks. Nue is showing what revenue operations should have always felt like."

---

## Identity & Access Bridges

**IAM at scale, direct transfer:** "The protocols are the same regardless of platform — SAML, OIDC, SCIM, RBAC. Operating at 160K-user scale means identity complexity at a 104-person, 9-country company is a scope handled confidently, not a stretch."

**Joiner/Mover/Leaver automation:** "SCIM provisioning, ABAC dynamic groups, and identity lifecycle automation were designed and built at AHS — access following the person, changes propagating automatically without manual intervention. That's built in the personal Entra IaC lab from scratch as well."

**Endpoint management, cross-platform:** "Workspace ONE, Intune, and Jamf-equivalent tooling all cover multi-OS fleet management at 160K-user scale — hardened baselines, patching, compliance policies, enrollment across Apple, Android, and Windows. The MDM discipline is identical regardless of which specific platform is in use, and an Apple background (ACMT certified) makes Mac-specific management second nature."

**Asset lifecycle management:** "Full asset lifecycle was managed at provincial scale using Ivanti AMC and ServiceNow — procurement tracking, auditable inventory, secure decommissioning. That's the exact audit trail a growth-stage company preparing for SOC 2 needs to build."

**Async-first documentation as a genuine differentiator:** a distributed team across 9 countries makes documentation survival, not a nice-to-have. Personal playbooks, runbooks, and a self-documenting IaC lab are direct proof of that discipline already being lived, not theoretical.

**SaaS management:** enterprise SaaS licensing and RBAC (Adobe CC, M365, broader enterprise SaaS) were directly managed at AHS — license optimization and entitlement governance are proven, not aspirational.

**Agentic AI workflow alignment:** a company building AI into its own product and wanting the same in its internal operations is a direct match for an existing human-in-the-loop AI workflow practice.

---

## Honest Tooling Gap Bridges

**Google Workspace vs. M365:** "Deep M365/Entra ID experience, but Google Workspace admin is the same underlying discipline — user lifecycle, group management, SSO integration, license governance. The concepts transfer directly; the GWS admin console is arguably simpler than the M365 equivalent."

**Okta vs. Entra ID:** "Entra ID is the primary IdP experience, but Okta speaks the same protocol language — SAML, OIDC, SCIM, lifecycle policies. The architecture is identical; only the UI differs."

**Jamf vs. Workspace ONE:** "Workspace ONE is the primary MDM background, but Jamf follows the same MDM philosophy applied to a Mac-first environment — enrollment, baselines, patching, compliance. A natural extension, not a new discipline."

**Linear vs. Jira/Asana:** modern, lightweight project management tooling popular with startups — comfortable adapting given broad exposure to Asana and Jira already.

**Workato/n8n (no direct experience):** "The automation mindset transfers directly from Bash scripts and Terraform automation already built for provisioning pipelines. Low-code platforms represent a fast learning curve for someone who already thinks natively in automation flows."

---

## SOC 2 — Personal Bridge Framing

**On PHIPA mapping to SOC 2 generally:** "AHS operated under PHIPA — Alberta's health privacy legislation, requiring mandatory audit trails, access reviews, data privacy controls, and zero-downtime change management. That's SOC 2 discipline, just applied to a different regulated industry. The framework vocabulary is new; the operational muscle is 7 years deep."

**On Type 1 specifically:** "When AHS rolled out Connect Care across 400+ sites, standardized readiness frameworks existed — documented, auditable, consistent, with every site meeting the same baseline before go-live. That's Type 1 thinking: proving the design is right before scaling it."

**On Type 2 specifically:** "Sustained 99.9% uptime for mission-critical clinical operations wasn't a one-day check — that's sustained operational evidence. Every incident was documented, every change tracked, every access review logged. That's Type 2 evidence collection happening daily, without ever calling it SOC 2."

**On Security TSC ownership specifically:** "Conditional Access policies were enforced for 160K clinical users — MFA, device compliance, location-based access — with every access change logged and privileged account reviews run regularly. That's Security TSC in practice at provincial scale. The personal Zero Trust lab is Security TSC in miniature — RBAC, Conditional Access, SCIM provisioning, SSH locked behind an identity-aware network, an audit-ready infrastructure-as-code codebase, every control documented and reproducible."

**On Availability TSC:** "99.9% uptime for mission-critical clinical operations — when the network went down, a clinician couldn't access patient records, a genuine patient safety issue. PIPR was built specifically to catch signals before they became outages — that's Availability criteria thinking in practice."

**On Confidentiality TSC:** "Patient data is among the most confidential data categories that exist. Every access to clinical records was identity-verified, logged, and auditable — the access control layer (SSO, Conditional Access, RBAC) protecting that data was owned directly. Revenue data instead of health data is the same confidentiality discipline, applied to a different domain. ABAC dynamic groups and least-privilege RBAC in the lab are Confidentiality controls in direct practice — access follows identity, identity follows attributes, automatically."

**A grounded, honest answer on direct SOC 2 audit experience:** "No direct ownership of a SOC 2 audit relationship specifically — equivalent controls existed at AHS but were owned by dedicated compliance and security teams, with IT operating the controls feeding into those frameworks: access reviews, audit trails, incident documentation, endpoint compliance. Owning the controls without owning the audit relationship directly is the honest distinction — and coming in at a build stage is often where the most value gets added, because what 'good' looks like at scale is already understood."

**On architecting for evidence generation, plainly stated:** "The right approach isn't building for the audit — it's building systems that generate evidence as a natural byproduct of daily operations. When the auditor arrives, the evidence already exists."

---

## Recognizing and Naming Scope Ambiguity in a Job Description

A generally useful, reusable interview skill: when a JD lists a broad combination of responsibilities (e.g., endpoint security, identity security, vulnerability management, incident response, and compliance ownership all in one posting), it's worth naming that pattern directly and asking how those responsibilities are currently structured — rather than assuming the title reflects the actual scope. A good version of this question: "The JD references several distinct functions — I want to understand how those responsibilities are currently owned, whether there's a dedicated function for each, or whether this role is expected to carry all of them end-to-end. That helps calibrate expectations on both sides." This demonstrates careful reading and systems thinking, and it invites an honest answer about actual scope rather than assuming good faith on title alone.

---

## Personal Pitch Framing

**Why a company at this specific stage:** "A company at Series A with 3x growth and expanding globally is exactly the stage where IT infrastructure matters most — the systems that work at 50 people break at 150. Years spent building the identity, device, and compliance infrastructure that keeps a 160,000-person organization running translate directly into building it right the first time at a fast-growing smaller company, rather than retrofitting it later."

**On empathy as a genuine throughline, not a buzzword:** "Customer empathy isn't just a stated value — it's where this career started. At Apple, every broken device represented a broken trust relationship. That same philosophy carried into healthcare IT, where a clinician without their tools means a patient without care. IT done right means people never have to think about it."

**On ownership specifically:** "IT isn't treated as a ticket queue — it's treated as a product. Systems were built from scratch at AHS: the PIPR incident framework, provisioning automation, identity architecture. That same builder mentality is the default operating mode, not an occasional mode."

**A grounded systems-thinking summary across domains:**
- **IT Architecture & Strategy:** identity architecture owned at 160K-user, 900-facility scale — RBAC, Conditional Access, SCIM lifecycle, built as patterns from scratch, not just operated
- **Endpoint & Asset Management:** 7 years of full device lifecycle — multi-platform MDM, asset tracking, hardened baselines, secure offboarding at provincial scale
- **Identity, Access & SaaS Governance:** SCIM, SAML, OIDC, RBAC, ABAC, and joiner/mover/leaver automation built and operated at scale — a new IdP is new UI over familiar protocols
- **Security, Compliance & Risk:** PHIPA-equivalent discipline for 7 years — mandatory audit trails, access reviews, data privacy controls, incident response with RCA documentation
- **IT Operations, Automation & Support:** PIPR reduced major incidents by 40%; Bash and Terraform automation in the personal lab; async-first runbooks designed for distributed teams across 400+ sites
- **Leadership & Mentorship:** informal mentoring on security-minded troubleshooting; Apple training background designing and delivering technical workshops; documentation authored so any engineer could pick it up independently
