# Okta — Playbook

**Document Type:** Personal Playbook / Knowledge Bridge Reference  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  

---

## What This Is

This pairs with `okta-research.md`. That file holds objective company knowledge. This file holds personal bridges connecting AHS/lab experience to Okta specifically, plus an honest self-assessment of where real gaps exist.

---

## Weaving Core Values Into Personal Framing

Rather than reciting Okta's stated values verbatim, the spirit maps naturally onto existing experience:

- **"Own the outcome and the impact"** → maps directly to the DRI (Directly Responsible Individual) framing already used at AHS
- **"See around the corners"** → maps directly to PIPR (Proactive Incident Pattern Recognition)
- **"Always secure, always on"** → maps directly to sustaining uptime and zero-downtime change management at 160,000-user scale

---

## AHS and Lab Bridges

**Bridge 1 — Identity at Scale, Platform-Agnostic Concepts:** "I've operated enterprise identity at 160,000-user scale using Entra ID — SSO, Conditional Access, SCIM provisioning, RBAC/ABAC lifecycle. The concepts are directly portable to Okta. SAML, OIDC, OAuth 2.0 are industry standards, not vendor-specific. I've lived the operational reality of identity at scale, and that translates regardless of which IdP sits underneath."

**Bridge 2 — The "Own the Outcome" DRI Story:** "I served as the technical DRI for identity, endpoint, and IT service delivery across 160,000 users and 900+ facilities. When something broke, I owned it end to end, not just the piece in my lane. That's the same ownership mindset Okta describes in 'own the outcome and the impact.'"

**Bridge 3 — PIPR as "See Around the Corners":** "I built PIPR, Proactive Incident Pattern Recognition, specifically because I learned that by the time an issue escalates, you've already lost the opportunity to prevent it. PIPR was, in effect, a continuous readiness assessment — is this system, this workflow, this environment actually ready to handle what's coming, or is there a gap to close first. That's the exact instinct behind a Go/No-Go call."

**Bridge 4 — Zero Trust Lab as Technical Credibility:** "I built a production-grade Zero Trust identity environment using Terraform and Entra ID — JML lifecycle automation, RBAC/ABAC governance, SSO and SCIM across enterprise SaaS apps. It's hands-on proof of building identity architecture, not just discussing it."

**Bridge 5 — Agentic AI and NHI Awareness:** "I've been actively studying the convergence of identity and agentic AI across the industry — how Okta, Lumos, Cyera, and Tailscale are all attacking the same fundamental problem from different layers. Okta's Cross App Access and the 'agents as first-class identities' framing is exactly where the industry has to go, and I want to be part of building that at the company leading it."

---

## RTO/RPO — Healthcare Framing (Real Stakes, No Analogy Needed)

In healthcare, RTO and RPO don't require an analogy — hospital system downtime and patient data loss are the direct, real stakes. If a clinical system like Connect Care goes down, RTO determines how fast it needs to be restored before patient care is compromised. RPO determines how much charting, orders, or clinical data can be lost before it creates a patient safety gap, not just an inconvenience.

---

## RPS — Real AHS Example (Identity-Driven WiFi Auto-Connect Incident)

**Why RPS matters for Okta specifically:** if a customer's integration suddenly floods Okta with login requests (a bad script, a traffic spike), Okta's API might throttle or reject requests once the RPS limit is hit. Part of a technical readiness role's job is diagnosing whether a slowdown is a platform limitation (an RPS ceiling being hit) or a customer configuration issue (inefficient code making unnecessary repeated calls).

**A direct, real example:** the Identity-Driven WiFi Auto-Connect project at AHS experienced a major incident where enrolled devices suddenly couldn't connect to the AHS restricted network. It initially looked like a client-side connectivity failure, but the root cause was the authentication server (RADIUS, standard for 802.1X certificate-based WiFi) being overwhelmed by a spike in simultaneous authentication requests — an RPS ceiling being hit, not a broken WiFi profile.

This is a strong, real example of distinguishing a platform/infrastructure capacity issue from a configuration issue — exactly the diagnostic instinct a readiness-focused technical role calls for.

---

## The Two-Project Readiness Story

Connect Care and Remote-Hybrid Workforce Enablement together represent two dimensions of "readiness" that map directly onto a Go/No-Go evaluation framework.

"Two projects capture this well. The first is Connect Care, a 9-phase EPIC rollout across 900+ facilities and 160,000 users. My job was assessing readiness at every phase — not just whether the technology worked, but whether clinical staff and the IT team were actually prepared to support it on go-live day. That's readiness at the human and operational level. The second is the Remote-Hybrid Workforce Enablement project, evaluating and migrating 100,000+ employees off legacy Fortinet VPN onto a cloud-native, identity-driven access model. That was readiness at the enterprise infrastructure and technology-decision level — evaluating options, documenting trade-offs, making the call on what was actually ready to replace what existed. Both were built on the same identity foundation — secure, identity-driven connectivity, which is also the thread running through the SCEP-based WiFi auto-connect work. Different scale, same instinct: don't declare something ready until you've actually verified it is."

---

## Honest Gap Assessment

Worth being direct about, rather than overclaiming: a technical readiness-focused Okta role expects someone who has lived inside identity platforms at a technical implementation level — SAML, WS-Federation, OAuth, OIDC at an architect level of fluency, not just conceptual understanding. Entra ID depth bridges reasonably well since the underlying protocols are the same industry standards, but Okta-specific protocol implementation experience is genuinely thinner than what a native Okta background would bring. Best framed honestly rather than glossed over — conceptual and architectural fluency transfers directly, but hands-on Okta-specific tooling is a real, acknowledged growth area.

---

## Sample Narrative Framing

**Opening framing, leading with genuine interest rather than a resume walk:** "Rather than walk through my whole resume, I'd rather share what's actually drawn me to Okta right now. I've been following the shift toward Identity Security Fabric and Okta for AI Agents closely — the idea that agents need to be first-class, governed identities rather than static API keys with permanent access. That's the exact problem I've been building toward in my own Zero Trust lab using Terraform and Entra ID. The value brought isn't just identity experience — it's having operated at real enterprise scale under strict compliance, paired with genuine conviction about where this industry is heading."

**On "why Okta" specifically:** "Three reasons. First, Okta is the independent identity company — not tied to one cloud ecosystem, which matters enormously to enterprises avoiding vendor lock-in. Second, the timing — Okta for AI Agents just went GA, and the identity industry is converging on the idea that agents need to be first-class, governed identities. That's exactly the space being built toward with my own lab. Third, a technical readiness-focused role is fundamentally about making sure a team has everything it needs before a launch goes forward — that readiness-assessment instinct is exactly what PIPR and the Connect Care rollout at AHS practiced."

**On technical background, bridging honestly:** "The deepest technical experience is in Microsoft Entra ID at enterprise scale — SSO, Conditional Access, Zero Trust transition from legacy VPN, SCIM provisioning. The underlying protocols — SAML, OIDC, OAuth — are the same standards Okta is built on. There's also hands-on Terraform experience for identity infrastructure as code. Not pretending to have Okta-specific implementation depth on day one, but the conceptual and architectural fluency transfers directly, and learning fast in production environments is a proven pattern."
