# Zero Trust & Network Security: Network as Gate, Not Sensor

**Document Type:** Knowledge Article  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** May 2026  

---

## The "Network Is Dead" Myth

A common but flawed take in security circles is that the network no longer matters. The reality is more precise:

> "Saying 'Network is dead' is just plain dumb. What's dead is network as a sensor. Network as a gate is more important than ever."

| What Changed | What Didn't |
|---|---|
| ~95% of web traffic is encrypted HTTPS | Networks still control what can talk to what |
| East-west cloud traffic encrypted by default | Network segmentation still enforces access boundaries |
| Deep packet inspection is largely obsolete | Zero Trust still requires network-layer enforcement |
| Identity, endpoint, and app are better sensors | Network is still a critical gate — just not a passive sensor |

---

## What Zero Trust Actually Means at the Network Layer

Zero Trust is not a product. It's an architectural principle: **never trust, always verify** — at every layer.

At the network layer, this means:

- **No implicit trust based on IP or location** — being on the corporate network grants nothing by default
- **Identity-aware access** — every connection is tied to a verified identity (human or machine)
- **Least-privilege connectivity** — devices and services can only reach what they're explicitly permitted to
- **Encryption everywhere** — traffic is encrypted in transit regardless of network segment

---

## Tailscale as a Zero Trust Network Example

Tailscale implements Zero Trust networking via a WireGuard-based mesh VPN:

| Concept | Tailscale Implementation |
|---|---|
| Identity-based access | Every node authenticated via identity provider (Google, Okta, Entra ID) |
| Least-privilege connectivity | ACLs define exactly which nodes can reach which services |
| Encrypted by default | WireGuard encryption on all traffic, no exceptions |
| No implicit trust | Subnet routers and exit nodes require explicit policy approval |
| Tailscale SSH | SSH access gated by Tailscale identity, not exposed to public internet |

**Tailscale ROI insight (Forrester TEI 2026):**  
Payback on Tailscale infrastructure investment documented at **under 6 months** — driven by faster onboarding, fewer support tickets, and tighter security with less friction.

> Connectivity isn't a feature. It's the layer everything depends on: access, security, remote work, and now AI and LLM usage.

---

## Infrastructure + Security Convergence

A structural shift underway: **CISOs increasingly owning infrastructure**, not just security policy.

Historically, security teams were accountable for risk without direct control over the systems generating it. That divide is closing.

| Old Model | Emerging Model |
|---|---|
| Security team sets policy; infra team owns systems | Security and infra under shared or unified ownership |
| Reactive: audit after the fact | Proactive: security built into infra from day one |
| Separate tooling and teams | Tightly aligned tooling, shared accountability |

> "The future of security (and security products) sits at the intersection of infra and security — not in silos."

---

## Real-World Architecture: Tailscale + tsnet for Secure Agent Access

Cleric (automated SRE platform) uses Tailscale's `tsnet` library to give AI agents **scoped, secure access** to customer environments:

```
Cleric VPC                         Customer VPC
┌──────────────┐                  ┌──────────────────────────────┐
│ Cleric Agent │──100.64.0.1:443─▶│ Cleric Connector             │
│              │──100.64.0.2:443─▶│   → Kubernetes API (10.0.0.1)│
│              │──100.64.0.3:443─▶│   → Grafana (10.0.0.2)       │
└──────────────┘                  │   → Prometheus (10.0.0.3)    │
                                  └──────────────────────────────┘
```

Each connection = a distinct Tailscale device. No broad VPN access. Least-privilege by design.

---

## OAuth Tokens & the Limits of Network-Layer Offboarding

A common misunderstanding: deprovisioning a user from Tailscale is not the same as revoking all their access.

**What Tailscale does on offboarding:**
- User deprovisioned from IdP → Tailscale node loses authentication on next key expiry
- With key expiry enabled and device authorization required, network access is revoked cleanly within the configured window

**What Tailscale cannot do:**
- OAuth tokens issued directly between a user's browser and a SaaS app (Notion, Slack, GitHub, Google Workspace) **bypass the network layer entirely**
- Tailscale never issued those tokens, never saw them, and cannot revoke them
- From the SaaS app's perspective, the token is still valid — the user is still "in"

> "Tailscale closes the network access door on offboarding — but OAuth tokens issued directly to SaaS apps bypass the network layer entirely. That's an IdP governance and SaaS management problem, not a connectivity problem."

This is the **ghost account problem** — users deprovisioned at the directory level with live credentials still floating in connected applications.

| Offboarding Layer | Tailscale's Role | Who Owns It |
|---|---|---|
| Network access revocation | ✅ Handles via key expiry + IdP deactivation | Tailscale + IdP |
| SSO session termination | 🟡 Depends on IdP propagating revocation | Okta / Entra ID |
| OAuth token revocation (SaaS apps) | ❌ Outside network layer scope | Okta Lifecycle Management, CASB tools |
| Behavioral detection of ghost accounts | ❌ Outside network layer scope | Artemis, CASB |

**Practical implication:** Key expiry should always be configured in production Tailnets. And OAuth governance (token discovery, lifetime enforcement, revocation) needs a dedicated layer above the network — typically the IdP or a CASB tool.

---

## Key Takeaways

- **Network as sensor is diminishing** — encryption has made payload inspection largely obsolete
- **Network as gate is growing** — what talks to what is more critical than ever in Zero Trust architectures
- **Tailscale's ROI is fast** — sub-6-month payback because connectivity touches every layer of the stack
- **Infrastructure and security are converging** — the clean separation between the two teams is disappearing
- **tsnet / subnet routers** let AI agents access customer environments with least-privilege scoping — no hardcoded credentials, no standing access
- **OAuth tokens outlive network revocation** — Tailscale closes the network door; SaaS token governance requires IdP lifecycle management or CASB tooling

---

## Official References

| Source | Link |
|---|---|
| The Core Strength Network — Network Is Dead debate | LinkedIn post |
| Tailscale Forrester TEI Report 2026 | https://tailscale.com/resources/reports/forrester-tei-report-2026 |
| Cleric + Tailscale tsnet blog | https://tailscale.com/blog/cleric-tsnet-automate-software-operations |
| Ross Haleliuk — CISOs Owning Infrastructure | https://substack.com/@ventureinsecurity/p-195780508 |
| 1Password — OAuth Ghost Accounts & Supply Chain Risk | https://1password.com/blog/protect-against-oauth-supply-chain-breaches |
