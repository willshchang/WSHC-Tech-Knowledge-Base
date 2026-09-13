# WorkOS — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** September 2026  
**Official Reference:** https://workos.com  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Founded** | 2019, San Francisco — public launch on Hacker News, March 2020 |
| **Stage** | Series C |
| **Total funding** | ~$198M+ across 3 disclosed rounds |
| **Latest valuation** | $2B (Series C, March 2026 — up from a $525M Series B valuation in 2022) |
| **Team size** | ~134 employees |
| **Notable customers** | OpenAI, Anthropic, xAI, Cursor, Perplexity, Sierra, Baseten, Replit, Vercel, Webflow, Synthesia, Temporal, Gamma, Clay, Exa — 1,000+ paying customers total |
| **Category** | Enterprise-readiness infrastructure (SSO, SCIM, authorization) — increasingly extending into agentic identity and authorization |
| **Website** | https://workos.com |

---

## Founder

**Michael Grinich (Founder & CEO)** — wrote his first lines of code in a dorm room at MIT, later dropping out. Worked as an engineer at Dropbox (2011) before co-founding **Nylas** (2013–2017), an email/calendar API infrastructure company he ran for several years before departing. Founded WorkOS in 2019.

**The founding insight — "the enterprise chasm":** individual developers and small teams could build genuinely great software quickly, but the distance between "a product individual users love" and "a product an enterprise buyer will actually approve" was enormous — SSO, directory sync, audit logs, and compliance requirements that most early-stage products simply didn't have, and that took months to bolt on later. WorkOS positions itself explicitly as **"the Stripe of enterprise features"** — a set of APIs any developer can drop in to make an application enterprise-ready in minutes rather than months.

---

## Funding Timeline

| Round | Amount | Valuation | Date | Notes |
|---|---|---|---|---|
| Series B | $80M | $525M | June 2022 | Alongside the acquisition of **Modulz**, a Dublin-based design tooling startup |
| Series C | $100M | $2B | March 2, 2026 | Led by Meritech Capital Partners and Sapphire Ventures, with Audacious, Craft, Abstract, and Greenoaks also participating |

**Grinich's own framing of the Series C's purpose:** *"This new funding allows us to accelerate the next phase: building what's needed to make agentic software secure and reliable by default."*

---

## Core Product Suite

**AuthKit** — the flagship authentication product. Free up to **1M monthly active users**, a genuinely generous free tier that positions WorkOS as a credible Auth0 alternative specifically for B2B SaaS companies (not consumer/B2C use cases, where WorkOS is deliberately weaker — see Honest Limitations below). Covers SSO, social login, MFA, session management, and full SDK coverage across major frameworks (Next.js, Astro, TanStack Start, iOS via a native Swift SDK using PKCE-based public-client authentication).

**Directory Sync (SCIM)** — automated user provisioning/deprovisioning synced from a customer's own identity provider.

**Fine-Grained Authorization (FGA)** — shipped 2024, a Zanzibar-style authorization model (the same relationship-based access control approach Google originally published and popularized) — competitive with Auth0's own FGA offering for modern B2B SaaS authorization needs.

**Audit Logs, User Management, Widgets API** (a session-aware GraphQL API for building UI directly from WorkOS data), and a growing **Management MCP server** exposing hundreds of WorkOS operations directly to AI agents/tools.

**Vault** — credential and secrets handling with local cryptographic operations (referenced in the iOS SDK material), and a capability to **"call third-party APIs on behalf of your users without handling their access tokens"** directly.

---

## Auth.md — Open Protocol for Agent Registration (Launched June 2026)

An open, published protocol (not a proprietary WorkOS-only feature) giving AI agents a standardized way to **discover services, register with verifiable identities, obtain scoped credentials, and connect their accounts to a person or organization** — introduced on stage at WorkOS's own "MCP Night: Agent Night" keynote. AuthKit has native, out-of-the-box support for the protocol.

**In plain terms:** before Auth.md, there was no standard way for an AI agent to "log into" a third-party application the way a human does via OAuth — Auth.md is WorkOS's attempt to establish that standard, openly, rather than keeping it proprietary.

---

## Airlock — Intent-Based Access Control for Agents (Launched August 2026)

The most technically sophisticated and important recent product, introduced at WorkOS's own "Agent Night" event. This deserves real depth, since it's a genuinely novel approach relative to everything else in this KB's Secrets & Credentials / Identity & Access layers.

**The core problem Airlock addresses, stated precisely by WorkOS itself:** traditional least-privilege access control requires hard-coding permissions in advance — but an agent's actual job is often unknown until runtime. Teams are left choosing between two bad extremes: `--dangerously-skip-permissions` (no meaningful access control at all) or constant manual approval prompts (so much friction the agent becomes useless).

**A genuinely sharp illustration WorkOS uses to make the stakes concrete — the "blast radius" asymmetry:** coding agent permission systems were built to protect a developer's laptop filesystem. Ask a coding agent to run `rm -rf` and it stops to ask first. Ask that same category of agent to "clean up the stale opportunities in your CRM pipeline" and it can silently close 214 records without a single permission prompt — because no mainstream agent permission system has any concept of what an API call actually *means* to a business, only what a shell command could do to a filesystem. Both are single tool calls; only one triggers a safeguard, and it's not the one that's actually irreversible.

**How Airlock actually works — intent-based, not role-based:**

1. A task is defined as an **intent**, not a role or scope — e.g., *"Send an email to Jo with the latest financial forecast"* or *"Find last month's duplicate charges and refund them"*
2. The intent compiles into a specific **action** — the connectors involved and the concrete action definition expanded from the original request
3. As the agent works and calls tools/integrations, **every single call is judged at runtime** against both the original intent and the organization's written policies
4. The verdict is one of four outcomes: **allow, deny, escalate to a human, or request more context** — that third outcome (escalation) is explicitly framed as the missing piece most systems lack: *"The honest answer to 'can this agent do this' is often 'it depends, ask someone.'"*

**Two policy layers:** static policies (constrain method, arguments, and request body — always in effect) and runtime checks (judged per call, handling nuance no static rule can express — e.g., whether a message body contains financial data, or whether a distribution list has ever included external recipients).

**A real architectural concern Airlock's own team names honestly:** *"If an agent evaluates the policies, who checks the checker? A model sitting in the enforcement path can be worked on by the same input it is supposed to judge."* This is a genuine, unsolved tension in any LLM-adjudicated authorization system, and worth remembering as a live open question rather than something Airlock claims to have fully solved.

**Where it runs — deliberately not tied to one surface:** inside coding harnesses (Claude Code, Codex, OpenCode), behind any MCP gateway already deployed, and inside AI teammates like **Atlas** (WorkOS's own AI coworker product, launched August 2026, that works in Slack). Approvals are explicitly routed through Slack rather than an IDE, because — in WorkOS's own words — *"for most people at a company, Slack is the app, and a permission model that only exists in an IDE excludes them from governing their own agents."*

**Every verdict is logged, with rationale attached** — the stated reasoning: the question security eventually asks is never "what could the agent do," it's "what did it do," and that question requires one durable record per action.

---

## Honest Limitations (Per Independent Third-Party Review)

Worth including for balance rather than only repeating WorkOS's own marketing framing. A recent, credentialed independent CIAM review (guptadeepak.com's CIAM Compass, last verified August 19, 2026) offers a genuinely even-handed assessment:

- **Strongest specifically in B2B, by deliberate scope choice** — every product surface assumes the buyer is selling to enterprise IT, not building for consumer/B2C use cases
- **Weaker B2C-grade features** — no progressive profiling, no native bot detection
- **Adaptive/risk-based MFA is rudimentary** compared to specialized competitors like Descope or Auth0
- **Narrower compliance breadth** than Auth0 — no FedRAMP, no direct PCI DSS attestation
- **The reviewer's most important calibration point, worth remembering precisely:** as of this review, *"MCP/agentic identity is partial, no first-class agent token model... the company is documenting MCP step-up patterns for agents; that is still a tutorial surface, not a packaged agent-identity product like Auth0 for AI Agents."*

**Why this last point matters:** Airlock and Auth.md are real, genuinely sophisticated, and publicly launched — but an independent, credentialed reviewer's assessment (as of August 2026) is that WorkOS's agentic-identity offering is still earlier-stage and less fully packaged than Okta's comparable Agent SSO product (see `okta-research.md`). Worth holding both facts at once: WorkOS's *architecture* for agent authorization (Airlock's intent-based model) is arguably more novel and interesting than anything else in this KB's Identity & Access layer, while its packaging and maturity as a turnkey enterprise product may still be behind Okta's more established offering.

---

## Competitive Landscape

| Competitor | Position vs. WorkOS |
|---|---|
| **Auth0 (Okta)** | The most direct, most-cited competitor — WorkOS's own free-tier generosity (1M MAU) and B2B-first focus position it as "a credible Auth0 alternative for B2B SaaS," per independent review. Okta's Agent SSO (see `okta-research.md`) is currently viewed as more mature/packaged for agentic identity specifically |
| **Descope** | Stronger adaptive/risk-based MFA specifically |
| **Frontegg, Stytch** | Other developer-first, B2B-focused identity infrastructure competitors |
| **C1 (Agentic Vault / Agent Runtime Governance)** | Genuine conceptual overlap with Airlock — both govern what an agent can do at runtime, though via different mechanisms (C1's gateway-based tool-call scoring vs. Airlock's intent-compiled, policy-evaluated model) |

---

## ZTAI Layer Placement

**Primary layer: Identity & Access** — same core layer as Okta, C1, and Lumos, specifically the B2B-SaaS-developer-infrastructure sub-niche.

**Airlock pushes WorkOS meaningfully into Agent Runtime Governance territory** — the same conceptual space C1's Agent Runtime Governance occupies, worth a direct comparison once the ZTAI map gets its full update pass:

| | WorkOS Airlock | C1 Agent Runtime Governance |
|---|---|---|
| **Core mechanism** | Intent compiled into action, evaluated per call against policy | Every tool call scored against the "lethal trifecta" risk model |
| **Verdict options** | Allow, deny, escalate to human, request more context | Block, hold for approval, redact |
| **Where it runs** | Coding harnesses, MCP gateways, AI teammates (Atlas), approvals via Slack | Identity-aware gateway, requires agent traffic routed through it |
| **Philosophy** | Intent-based — not pre-defined roles/scopes | Real-time enforcement on defined tool scope |

See `ZTAI-ecosystem-map.md` for the full layer breakdown.

---

## Key Takeaways

- **WorkOS's core thesis — "the enterprise chasm" — is genuinely well-observed:** the distance between a product individuals love and a product an enterprise buyer will approve is a real, specific, expensive gap, and WorkOS built an entire company closing exactly that gap
- **The customer list is a strong signal of category leadership among AI-native companies specifically** — OpenAI, Anthropic, xAI, Cursor, Perplexity, and Replit all run enterprise identity on WorkOS infrastructure
- **Airlock's intent-based model is one of the more genuinely novel approaches to agent authorization in this entire KB** — moving from pre-defined roles/scopes to runtime intent evaluation directly addresses the "asymmetric blast radius" problem most agent permission systems don't even recognize exists
- **Airlock names its own hardest unsolved problem honestly** — "who checks the checker" when an LLM sits in the enforcement path is a real, live tension, not something to pretend is fully solved
- **Independent, credentialed review calibrates the hype appropriately** — Airlock and Auth.md are real and sophisticated, but WorkOS's agentic identity offering is assessed as less mature/packaged than Okta's Agent SSO as of mid-2026
- **Auth.md is a genuine attempt at an open, cross-vendor standard**, not a proprietary lock-in feature — the same instinct behind Okta's own Cross App Access becoming part of MCP's official spec

---

## Official References

| Source | Link |
|---|---|
| WorkOS | https://workos.com |
| WorkOS — Series C Announcement | https://workos.com/blog/series-c |
| WorkOS — Airlock Product Page | https://workos.com/airlock |
| WorkOS — Agent Night Recap: Airlock and Intent-Based Access Control | https://workos.com/blog/agent-night-recap-airlock-intent-based-access-control |
| WorkOS — Your Agent's Permission Model Stops at Your Home Folder | https://workos.com/blog/agent-permissions-blast-radius |
| Daring Fireball — WorkOS Launches Auth.md | https://daringfireball.net/linked/2026/06/15/workos-authmd |
| CIAM Compass — WorkOS Independent Review | https://guptadeepak.com/ciam-compass/vendors/workos/ |
