# IAM: Visibility, Governance & What the Team Actually Does

**Document Type:** Knowledge Article  
**Author:** Will Chang  
**Audience:** Personal Portfolio / Interview Reference  
**Last Updated:** May 2026  

---

## The Core Problem: It's Not an Access Problem, It's a Visibility Problem

Most organizations believe they have an access problem. They actually have a visibility problem.

> "You cannot secure what you cannot see."

No single team — IT, security, or compliance — has a complete picture of who has access to what. The root causes:

| Root Cause | What It Looks Like |
|---|---|
| Disconnected systems | Directory, cloud, and SaaS apps each hold partial access data — nobody has the full picture |
| Provisioning outpaces deprovisioning | Access granted in hours; stale access sits for weeks or months after offboarding |
| Machine identities ignored | Service accounts, API tokens, bots — identities with no owners, no expiry, no governance |
| Access reviews are checkbox exercises | Managers rubber-stamp 200 names in 4 minutes; audit passes, risk stays |

---

## What Mature IAM Visibility Actually Looks Like

| Capability | Description |
|---|---|
| Unified identity store | Single source of truth aggregating access across all systems |
| Automated correlation | Every entitlement tied to a real, active identity — no orphan accounts |
| Continuous access reviews | Triggered by role changes, not just calendar dates |
| Machine identity inventory | Documented owners, explicit expiry dates for all non-human identities |
| Real-time dashboards | Answer on demand: *Who has access to what right now?* |

> **IAM Program Success Formula:**  
> Secure IAM = Visibility of All Access × Automated Governance × User & Machine Accountability + Real-Time Dashboards

---

## The IAM Visibility Blueprint: 3 Phases

**Phase 1 — Unify Identity Silos**  
Directory, cloud, and SaaS must speak one language. No more fragmented views.

**Phase 2 — Accelerate Deprovisioning**  
Revocation urgency must match provisioning urgency. Stale access = open attack surface.

**Phase 3 — Govern Machine Identities**  
Inventory all service accounts, API tokens, and workload identities — with owners and expiration.

---

## What IAM Teams Actually Do (vs. What the Business Thinks)

The business assumes: provision access, reset passwords.

The reality — IAM teams operate across many functions:

- Identity engineer & policy architect
- Federation troubleshooter (SAML, OIDC, OAuth)
- Token translator & legacy system negotiator
- SaaS firefighter & audit evidence generator
- Privileged access manager & secrets rotation engineer
- "Why is this 403?" detective at 2 AM
- Break-glass operator
- Human & non-human identity wrangler
- Risk translator to the business

> "An IAM team doesn't just give people access. They operate the most critical control layer in the modern enterprise."

**The job in one sentence:** Make the organization's attack surface smaller than yesterday, and the user experience smoother than before.

---

## OAuth & Ghost Accounts: A Hidden Risk

Deprovisioning a user from an application is good practice — but if they authenticated via "Sign in with Google/Microsoft," the **OAuth token may still be active**.

This creates **ghost accounts**: deprovisioned users with live credentials floating in connected apps.

| Risk Factor | Detail |
|---|---|
| Token not revoked on offboarding | OAuth connection persists even after directory removal |
| Attacker path | Compromise third-party service → use valid token → walk straight in |
| Detection difficulty | Most security systems see nothing wrong — token is technically valid |

**Mitigation shifts that matter:**
- Treat credential discovery as ongoing, not periodic
- Shorten credential lifetimes
- Separate dev and production environments
- Centralize credential storage; move toward just-in-time access
- Monitor how access is used, not just how it's granted

---

## Key Takeaways

- IAM is a **visibility problem before it's an access problem** — you can't govern what you can't see
- **Deprovisioning is as urgent as provisioning** — the gap between them is where breaches live
- **Machine identities are identities** — service accounts and tokens need owners, expiry, and governance
- **OAuth ghost accounts** are a real supply chain risk that survives standard offboarding
- IAM teams are the **control plane of the modern enterprise** — not a helpdesk function

---

## Official References

| Source | Link |
|---|---|
| IAM Visibility Gap (Sunny Kumar Kamani) | LinkedIn post — infographic |
| IAM "What We Actually Do" | LinkedIn post — pie chart |
| 1Password — OAuth Ghost Accounts | https://1password.com/blog/protect-against-oauth-supply-chain-breaches |
| CSO Online — Identity in the Agentic Era | https://www.csoonline.com/article/4163365/what-cisos-need-to-get-right-as-identity-enters-the-agentic-era.html |
