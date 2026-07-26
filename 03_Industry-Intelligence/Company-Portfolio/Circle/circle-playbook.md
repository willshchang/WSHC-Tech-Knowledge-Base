# Circle — Playbook

**Document Type:** Personal Playbook / Knowledge Bridge Reference  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  

---

## What This Is

This pairs with `circle-research.md`. That file holds objective company and technical knowledge. This file holds personal bridges connecting AHS/Apple experience to Circle's specific regulated-fintech IT context.

---

## The Core Framing: Why Circle's IT Stakes Map to Healthcare

"Understanding that Circle is B2B infrastructure changes how IT service delivery gets approached. Users here aren't just knowledge workers — they're building financial infrastructure for institutions managing billions of dollars. The bar for reliability, security, and discretion is fundamentally higher. That maps directly onto healthcare IT experience, where downtime has patient safety consequences."

**Same philosophy, different stakes:**
- Healthcare: a clinician without tools = a patient without care
- Circle: an engineer without tools = financial infrastructure at risk

---

## Regulated Environment Bridge

"Circle operates in one of the most regulated fintech environments in the world — NYSE listed, licensed across 46 states, MiCA compliant in Europe. Healthcare IT experience means 7 years operating under regulation demanding the same discipline: mandatory audit trails, access reviews, zero-downtime change management, data privacy controls. The stakes and standards are equivalent — just different industries."

**On PHIPA specifically:** "AHS operates under PHIPA — Alberta's health privacy legislation, equivalent discipline to SOC 2 and financial regulation. Patient data is among the most sensitive data categories in existence. Mandatory audit trails, access reviews, zero-downtime change management, compliance evidence generation have been the operating standard for 7 years. Circle's regulated fintech environment maps directly onto that same discipline."

---

## The Five Values, Bridged

**High Integrity:** Apple's 3A framework was built on this — never overpromise, stay honest even when the news is hard to deliver. At AHS, integrity meant a clinician could trust their tools would work when a patient's life depended on it.

**Future Forward (Adopt + Adapt):** Not waiting for trends — building toward them. Agentic AI Workflow is the current operating model; the Zero Trust IaC lab was built before anyone asked for it. This KB itself is being built in parallel with the job search. That instinct is Future Forward in practice, not performance.

**Multistakeholder:** every IT decision at AHS touched multiple stakeholders simultaneously — clinicians needing their tools, patients whose safety depended on uptime, administrators managing compliance, and the public whose tax dollars funded the system. Never had the luxury of optimizing for a single stakeholder — exactly the muscle this value describes.

**Mindful:** this is the Apple empathy-first framework restated in different language. Listen first, acknowledge, then respond — built from de-escalating frustrated Apple customers to supporting C-suite executives during high-pressure clinical incidents. Not a soft skill; a technical competency in human systems.

**Driven by Excellence:** PIPR was built because reactive incident management wasn't good enough. The Zero Trust IaC lab was built from scratch, not because anyone asked, but to prove the concept properly. "It works" isn't the bar when "it works AND it's documented AND it scales AND it's auditable" is achievable.

---

## Scale & Regulated-Environment Bridge

"IT infrastructure experience spans 160,000 users across 900 facilities. Circle's current scale is smaller in headcount, but the complexity of a regulated fintech company more than compensates — high-stakes environments where IT failures have real-world consequences are the norm, not the exception, in this background."

**On ServiceNow specifically:** "ServiceNow has been a core strength — not just using it, but building on it. Workflow development, RCA frameworks, and platform administration were owned directly. PIPR — a proactive incident pattern recognition system — reduced major incidents by 40%. That's the operational discipline a regulated environment like Circle's needs."

---

## JD Requirement Translations

**"7+ years supporting enterprise SaaS and IT systems in a global remote environment":** "14 years. AHS is one of Canada's largest distributed organizations — 900+ facilities across Alberta, fully remote-capable infrastructure, supporting 160K users across urban hospitals and rural clinics simultaneously. Global remote is the default operating model already lived."

**"Deep expertise managing macOS fleets at scale":** "Apple ACMT certified, 7 years as an Apple Genius. Managed a mixed macOS/Windows/iOS/Android fleet via Workspace ONE and Intune. Jamf-style tooling is a growth area, but the underlying MDM philosophy is identical — a fast ramp given the Apple background."

**"Hands-on experience with ServiceNow ITSM, including workflow development and platform administration":** "ServiceNow was the primary ITSM platform — workflows, RCA frameworks, incident management, asset management, and analytics all owned directly. PIPR (Proactive Incident Pattern Recognition) was built on top of it, reducing major incident volume by 40%. Workflow development and platform administration are core strengths, not gaps."

**"Strong experience with MDM":** "Workspace ONE was the primary MDM — 7+ years, 160K-user scale, full lifecycle from enrollment to secure offboarding. Newer Apple-first MDM platforms are unfamiliar territory specifically, but the same discipline applies — hardened baselines, patch management, compliance policies, device posture. The concepts transfer directly."

**"Experience in highly secure, regulated environments":** "PHIPA-equivalent discipline to SOC 2 and financial regulation, operated for 7 years. Patient data is among the most sensitive data categories in existence. Mandatory audit trails, access reviews, zero-downtime change management, compliance evidence generation — this maps directly onto a regulated fintech environment."

**"Executive-level white glove IT support":** "Direct technical DRI for C-suite, executive directors, and board members — managing onboarding, endpoint lifecycle, and escalation for the most senior stakeholders in a large health system. Discretion, responsiveness, and zero-failure standards are non-negotiable at that level, and that standard is already internalized."

**"Automation — Workato, n8n, or similar":** "No direct experience with those specific tools, but the automation mindset is identical — identify repetitive manual work, eliminate it with code. Bash automation for provisioning pipelines, Terraform IaC for entire infrastructure layers, certificate-based WiFi enrollment eliminating manual authentication for 160K users are all direct evidence of the same instinct. Low-code platforms are a fast ramp for someone who already thinks in automation."

**"AI tools or AI-assisted workflows":** "Agentic AI Workflow is a core part of how work already gets done — using AI as a technical collaborator, not just for answers but for accelerating implementation, documentation, and problem-solving. A full Zero Trust IaC lab was built in 7 days using AI as a collaborator alongside Terraform. AI-assisted IT operations isn't a future state — it's the current workflow."

---

## Gap Bridges — Honest and Confident Framing

**ServiceNow (power user, not workflow builder):** "Seven years as a power user — filters, favorites, dashboards, reporting — but workflow and service catalog development was ITSM-team territory, not a personal responsibility. What that means practically: deep familiarity with where friction lives, where tickets get stuck, where SLA bleeds, without having previously had the permission or scope to fix it directly. That's the actual appeal of a role with that scope — finally being able to build what's been mentally designed for years."

**Automation platforms (Workato/n8n, no direct experience):** "The underlying logic transfers directly from Terraform and Bash automation already built in the lab — an event or condition triggers a state change across multiple systems. A low-code automation platform is the same thinking with a visual interface instead of code. Production-ready workflows should come quickly given that existing automation-first thinking."

**Apple-first MDM platforms (no direct experience, Workspace ONE background):** "Workspace ONE is one of the more complex MDM platforms on the market — multi-OS, deep compliance policies, certificate management, complex enrollment flows. A more streamlined, Apple-first MDM platform is a matter of learning a new interface, not new concepts, given deep familiarity with the underlying enrollment protocols (ABM, ADE, SCEP certificates, zero-touch provisioning)."

**Non-Microsoft identity providers (Entra ID background, not the specific provider in use):** "Identity is identity — SAML, OIDC, SCIM, Conditional Access, lifecycle management are the protocols operated at 160,000-user scale in Entra ID. A different identity provider speaks the same language with a different interface; the underlying security architecture is already familiar at a considerably larger scale."

**GRC/compliance platforms (PHIPA background, not the specific tool):** "PHIPA compliance at AHS required the same discipline a dedicated GRC platform formalizes — mandatory audit trails and evidence collection. The specific tool is new, the underlying discipline isn't."

**CMDB (Ivanti background, not ServiceNow CMDB specifically):** "Asset lifecycle was managed in Ivanti AMC — every device tracked from procurement to secure decommission, auditable at any point. ServiceNow's CMDB applies the same principle at the ITSM layer, with the added dimension of capturing relationships between assets — which user owns which device, which device runs which software, which software carries which vulnerabilities. That relationship map is what makes automated remediation possible, and a CMDB health audit would be a natural early priority in any new role."

---

## Differentiators Worth Naming Directly

**The Zero Trust Lab:** most candidates in this space talk about automation — this is proof of having built it. Terraform managing entire identity infrastructure, SAML/OIDC/SCIM SSO across multiple SaaS apps, RBAC + ABAC self-healing dynamic groups, a production-grade documentation suite, and an architecture designed to scale from 89 to 8,900 users without changing code.

**Scale nobody else brings:** 160,000 users, 900+ facilities, a pandemic transition, zero downtime. Most candidates for equivalent roles come from considerably smaller organizations; this background operated at provincial-scale regulatory pressure that exceeds what most fintech environments actually require.

**The empathy foundation:** technical skills can be taught. Years of empathy-first support — managing executive expectations under pressure, recovering broken trust relationships, translating complexity into human outcomes — is a foundation that doesn't come from a course.

---

## Ivanti-to-Modern-Stack Translation

| Legacy Tool | Purpose | Modern Equivalent |
|---|---|---|
| Ivanti Landesk/EPM | Windows endpoint management | Apple-first MDM (Mac) + Intune (Windows) |
| Ivanti AMC | Asset lifecycle tracking | ServiceNow CMDB |
| Intune | MDM compliance + device posture | Apple-first MDM (Mac side) |
| ServiceNow | ITSM + CMDB | Same tool, same concept |

**The honest realization worth stating directly:** existing experience isn't a gap to bridge — it's effectively the enterprise, multi-OS version of what a simpler modern stack accomplishes. A modern Mac-first MDM is the streamlined version of a more complex stack already operated at scale.

---

## Talking Points on Systems Thinking (Architecture Over Button-Pushing)

**How a new-hire event flows through the stack:** an HRIS event fires a webhook or API call into the ITSM platform, which creates an onboarding ticket, triggers an integration layer to call the identity provider's SCIM API, provisions the account and pushes group memberships, and those groups trigger device enrollment and SaaS license assignment — the ticket closes automatically once all downstream provisioning confirms complete.

**How platform data surfaces security risk proactively:** the CMDB defines what's owned; the MDM tool reports the compliance posture of each device. Feeding both into vulnerability management means any device out of compliance, missing patches, or running unlicensed software surfaces as an automated risk ticket — a GRC platform pulls that data for the audit trail. The system surfaces risk proactively rather than an auditor finding it reactively.

**How CMDB structure enables real-time device answers:** each device record needs live data feeds — from the MDM tool for compliance/patch status, the identity provider for assigned user/status, and an EDR tool for security health. When those feeds are automated rather than manual, CMDB becomes a live dashboard rather than a stale spreadsheet.

---

## SLA Philosophy Bridge

"SLA enforcement in a union environment is fundamentally a political conversation — hard to act on patterns without it feeling personal. The better system is one where data surfaces the pattern, not a manager. Automation flags risk early, the team self-corrects, and SLA compliance becomes a cultural pride point rather than a performance conversation."

---

## Network Layer Bridge — Where Zero Trust Fits

A company like Circle would benefit substantially from an identity-aware, Zero Trust network model — identity-driven access to cloud resources, policy controlling exactly who reaches what, full audit trail for compliance. The alternative, a traditional VPN, creates a classic perimeter problem: once inside the VPN, broad reachability follows by default. An identity-first mesh network model eliminates that structural risk.

---

## Vision Talking Points

**The self-healing ITSM vision:** "The ideal build is a self-healing workflow — when an incident comes in, AI analyzes it, references the knowledge base, and surfaces troubleshooting steps to the user before a human ever touches it. This absorbs routine noise automatically, reserving human capacity for genuine escalations and white-glove executive support. SLA compliance improves without adding headcount."

**The zero-touch onboarding vision:** "The first automation worth building is zero-touch onboarding — an HRIS hire event triggers identity provisioning, which triggers device enrollment, with the device shipping pre-enrolled so a new hire logs in on Day 1 with everything ready. No tickets, no manual steps, no IT bottleneck."

**The closing framing:** "What's most exciting isn't just the tools or the tech stack — it's the opportunity to build IT that scales intelligently. Self-healing workflows, zero-touch onboarding, AI-assisted ITSM aren't future concepts — they're problems already being mentally designed for, waiting for an environment with the freedom to actually build them."
