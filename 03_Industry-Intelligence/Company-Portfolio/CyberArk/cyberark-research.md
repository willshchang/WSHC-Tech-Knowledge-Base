# CyberArk — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** September 2026  
**Official Reference:** https://www.cyberark.com  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Founded** | 1999, Petah Tikva, Israel |
| **IPO** | 2014, NASDAQ: CYBR |
| **Current status** | Now a subsidiary of Palo Alto Networks (acquired February 2026 — see `palo-alto-networks-research.md`) |
| **Pre-acquisition revenue** | ~$1.0B (2024); Q3 2025 alone: $342.8M |
| **Pre-acquisition market cap** | ~$24.6B (November 2025) — notably close to the eventual $25B acquisition price, suggesting Palo Alto paid close to fair market value rather than a steep premium |
| **Scale** | Secured over 50% of the Fortune 500 prior to acquisition |
| **Team size** | ~3,000–3,800 employees pre-acquisition |
| **Category** | Privileged Access Management (PAM) — the category's originator and, until its acquisition, the #1 player, directly ahead of BeyondTrust |
| **Website** | https://www.cyberark.com |

---

## Founders & Origin Story

**Udi Mokady** and **Alon N. Cohen** founded CyberArk in 1999, both veterans of elite Israeli technology/intelligence units — the same broad "Israeli military-tech alumni" pattern already noted elsewhere in this KB (Cyera, Wiz). Mokady later became CEO, then Executive Chairman.

**The founding insight, genuinely ahead of its time for 1999:** privileged credentials — not the network perimeter — were the actual weakest point in enterprise security. Most security spending at the time went toward firewalls and perimeter defense; CyberArk's founders bet that the real risk was **unprotected "keys to the kingdom"** — administrative and privileged accounts that, once compromised, granted an attacker unrestricted access regardless of how strong the perimeter was.

**The first product: the Digital Vault** — a hardened, isolated server providing granular access controls and an immutable audit trail for privileged credentials. This single product effectively seeded the entire Privileged Access Management category. Early funding included Jerusalem Venture Partners; the company stayed lean in its early years before scaling into the global identity security platform it became.

---

## Platform Evolution — From Vault to Full Identity Security Platform

CyberArk's growth was defined by consistent, focused expansion outward from that original vaulting core:

| Capability | What It Added |
|---|---|
| **Core PAM** | Protecting high-privilege IT and database accounts — the original Digital Vault discipline |
| **Endpoint Privilege Security** | Managing local administrator rights directly on endpoints |
| **Secrets Management** | Securing credentials used in CI/CD pipelines and microservices |
| **Secure Cloud Access** | Protecting identities and access across multi-cloud and hybrid environments |
| **Identity Lifecycle Management** | Automating onboarding, role transfers, and offboarding access changes |
| **Machine Identity Management** | TLS/SSL certificates, SSH keys, and broader machine identity — expanded substantially through the **Venafi acquisition (2024)** |

**Two acquisitions that mattered most in the final years before Palo Alto's own acquisition:**

- **Venafi (2024)** — brought certificate and cryptographic key management at scale, extending CyberArk's reach from human privileged access into full machine-to-machine trust (bots, containers, cloud services)
- **Zilla Security (2025)** — added identity governance capability, closing the loop between "who has privileged access" (CyberArk's core) and "is that access appropriate and reviewed" (traditional IGA territory, the same layer Lumos and C1 occupy)

**Technical moat:** 100+ patents across vaulting techniques, encryption, and behavioral analytics for detecting credential misuse — a genuinely deep, defensible technical position built over two and a half decades, not a recent AI-era pivot.

**Recognition:** consistently named a Leader in Gartner's Magic Quadrant for PAM across consecutive years through 2025 — the position BeyondTrust sits directly behind (see `beyondtrust-research.md`).

---

## The Palo Alto Acquisition — What Actually Happened

Full deal mechanics and Palo Alto's own strategic rationale are covered in `palo-alto-networks-research.md`. This section focuses on what happened **to CyberArk specifically**, from the acquired company's side of the story.

**Timeline:** Announced July 30, 2025. Closed February 11, 2026. All-stock-plus-cash deal (~$25B total), CyberArk shareholders received $45 cash + 2.2005 Palo Alto shares per CyberArk share held.

**A real, worth-noting tension:** in December 2025, ahead of the deal closing, CEO Nikesh Arora personally visited CyberArk's Israeli employees and stated directly: *"The good news is that we currently have no products in identity management, the area CyberArk specializes in, so there's no reason to cut there... Our intention is to invest in both teams."* **After the deal closed in February 2026, Palo Alto laid off more than 10% of CyberArk's workforce**, including staff in Israel and globally. Worth stating plainly rather than glossing over — this is a documented gap between stated pre-close intent and actual post-close outcome, a pattern not unique to this deal but worth being aware of in any acquisition conversation.

**Current leadership within Palo Alto:** Udi Mokady (Executive Chairman), Matthew Cohen (CEO of the CyberArk business unit specifically).

---

## Idira — Palo Alto's New Identity Platform, Built on CyberArk

**Launched May 12, 2026** — roughly three months after the acquisition closed. **Idira is Palo Alto's next-generation identity security platform**, consolidating and upgrading CyberArk's existing capabilities into a single platform explicitly designed to manage **human, machine, and AI-agent identities and permissions together.**

**Stated capabilities:** AI-driven risk discovery, **zero standing privileges** (a meaningfully stronger posture than traditional just-in-time access — the default state is no standing access at all, not merely time-limited access), and automated governance.

**Why this matters for the broader ZTAI thesis:** Idira represents the fastest, clearest evidence yet of "platformization" (see the forthcoming Platformization section in `ZTAI-ecosystem-map.md`) actually happening in real time — a 27-year-old, deeply specialized, patent-rich PAM company absorbed and re-platformed into a much larger company's identity offering within roughly 100 days of the deal closing.

**Palo Alto's own framing of the shift, worth remembering:** *"Integrating CyberArk's identity security capabilities into Palo Alto Networks' platform marks a fundamental shift from 'protect the network' to 'protect the identity.'"*

---

## Secure AI Agents — CyberArk's Own Pre-Acquisition Agentic Bet

Before the acquisition closed, CyberArk had already launched its own **Secure AI Agents Solution** — an early, independent bet on the same agentic-identity thesis every other company in this KB's Secrets & Credentials layer is now racing toward (1Password, C1's Agentic Vault, BeyondTrust's Machine PAM, Tailscale's PAM via Border0). This solution is now presumably being absorbed into or superseded by Idira, though the two products' exact current relationship isn't fully clear from available sources as of this writing.

---

## Competitive Landscape (Pre-Acquisition Positioning, Still Relevant Historically)

| Competitor | Position vs. CyberArk |
|---|---|
| **BeyondTrust** | The clear #2 in the PAM category, directly behind CyberArk for years — see `beyondtrust-research.md` for the full comparison |
| **StrongDM, Teleport** | Newer, more developer-first alternative approaches to privileged access — narrower scope, more infrastructure-access-specific than CyberArk's full enterprise platform breadth |
| **1Password, C1 (Agentic Vault)** | Faster-deploying, more cloud/SaaS-native credential security plays — see the broader Secrets & Credentials layer comparison in `ZTAI-ecosystem-map.md` |
| **Okta, Microsoft** | Broader identity/access management incumbents CyberArk's expansion into identity governance (via Zilla) increasingly overlapped with |

---

## ZTAI Layer Placement

**Primary layer: Secrets & Credentials (PAM)** — the category's originator and, until acquisition, its clear #1 player. Now folded into Palo Alto's broader platform (see `palo-alto-networks-research.md`), specifically feeding the new Idira identity platform.

**Secondary presence:** Identity & Access Governance (via the Zilla Security acquisition) — the same territory occupied by Lumos and C1.

See `ZTAI-ecosystem-map.md` for the full layer breakdown.

---

## Key Takeaways

- **CyberArk pioneered the entire PAM category in 1999** — a genuinely prescient bet, decades ahead of most enterprise security spending priorities at the time, that privileged credentials (not the network perimeter) were the real weak point
- **The company built a genuine, deep technical moat** — 100+ patents in vaulting, encryption, and behavioral analytics, accumulated over 25+ years, not a recent AI-era feature sprint
- **Venafi and Zilla Security were the two acquisitions that mattered most** heading into its own acquisition — extending from human privileged access into full machine identity (Venafi) and identity governance (Zilla), rounding out the platform Palo Alto ultimately paid $25B for
- **There's a real, documented gap between stated pre-close intent and actual post-close outcome** — Arora's public "no reason to cut" promise to CyberArk staff was followed by a 10%+ workforce reduction after the deal closed
- **Idira (launched May 2026) is the fastest, clearest real-time evidence of platformization in this entire KB** — a fully independent, patent-rich, category-defining company absorbed and re-platformed within roughly 100 days of acquisition close
- **CyberArk already had its own pre-acquisition agentic AI security bet** (Secure AI Agents Solution) — meaning even before Palo Alto's involvement, CyberArk was independently racing toward the same agentic-identity thesis as every other Secrets & Credentials player in this KB

---

## Official References

| Source | Link |
|---|---|
| CyberArk | https://www.cyberark.com |
| PR Newswire — Palo Alto Networks Completes Acquisition of CyberArk | (see `palo-alto-networks-research.md` for full deal coverage and links) |
| SiliconAngle — Palo Alto Networks Launches Idira | https://siliconangle.com (May 12, 2026 coverage) |
| JumpServer — What Is CyberArk: A Beginner's Guide | https://www.jumpserver.com/blog/what-is-cyberark |
