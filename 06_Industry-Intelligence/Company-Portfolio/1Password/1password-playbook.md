# 1Password — Playbook

**Document Type:** Personal Playbook / Knowledge Bridge Reference  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  

---

## What This Is

This pairs with `1password-research.md`. That file holds objective company and product knowledge. This file holds the personal bridges, positioning language, and talking points connecting AHS/Apple experience to 1Password's specific technical and GTM context.

**Note on figures:** source material for this playbook uses a 113,000-user AHS scale rather than the 160,000 figure used elsewhere in this KB. Worth reconciling before using this material live.

---

## Positioning as a Senior TAM Candidate

Three things to emphasize to establish "Senior" level, not just competent TAM:

1. **Proactive vs. Reactive** — don't wait for tickets; analyze usage data to spot under-utilization and intervene before renewal becomes a conversation
2. **The Feedback Loop** — translate technical friction observed with customers into concrete product requirements for engineering, not just complaints passed along
3. **Revenue Alignment** — understand NRR (Net Revenue Retention) even while staying technical; the job is making the customer so successful they couldn't imagine leaving

**Framing device:** in a senior role, think of the position as the "Technical Quarterback" — others move the ball down the field, the job is ensuring the play executes flawlessly and the team stays in the game long-term.

---

## Senior-Level Contribution Framing

| Contribution | What It Looks Like | Success Metric |
|---|---|---|
| **Trusted Advisor Status** | Moving from "the person who fixes 1Password" to "the person we ask about our security posture" | Customer includes you in their own internal planning meetings |
| **Strategic Friction Reduction** | Spotting patterns across a portfolio (e.g., three clients hitting the same Okta integration issue) and fixing the pattern once — documentation + product advocacy — rather than solving it repeatedly | Reduction in Time-to-Value for new enterprise features across the account list |
| **Revenue Safeguarding (Churn Mitigation)** | Spotting "Silent Churn" — a customer who's stopped opening tickets and stopped using the product isn't healthy, they're disengaged. Identifying this up to 6 months before renewal and building a proactive save plan with the AE | High Gross Retention Rate (GRR); identifying leads for Net Retention Rate (NRR) growth |
| **Technical Advocacy & Feedback Loop** | Acting as Voice of the Customer to the Product team — translating raw frustration into actionable technical requirements | Features shipped based on documented business cases from real enterprise accounts |

---

## Handling a Difficult Account — The Senior TAM Answer

"I start by mapping the stakeholders. I identify if the friction is coming from the Technical Lead (a product issue) or the Executive Sponsor (a value-perception issue). Once I know who the stakeholder is and what their specific pain is, I can tailor my technical solution to meet their business goal."

---

## Talking Points — Agentic Governance

**The core "agentic" line:** "We're moving past the era where a TAM just manages vaults for people. In a world of agentic security, my role is to ensure that as 1Password customers deploy AI, those agents are governed by the same rigorous, encrypted access policies as their human counterparts — preventing credential leakage or an identity crisis at scale."

**On the AWS partnership:** "I'm excited about the AWS Strategic Collaboration Agreement. It allows a TAM to solve the 'last mile' problem of secrets management — getting a secret from a secure vault into a production AWS container without manual intervention."

**On Cursor/Browserbase hooks (showing currency):** "With the rise of agentic AI, the Cursor Hook is a genuine shift. It ensures that when an AI writes code, it's using a reference to a secret, not the secret itself. It makes security invisible for the developer."

**The "punchy" one-liner for "Why 1Password?" or "What is a TAM?":** "I see the TAM role as the bridge that eases the tension between speed and security. With tools like Cursor Hooks and AWS Secrets Sync, we enable developers to move at the speed of AI while ensuring every credential given is intentional and human-verified."

---

## Sample Response: Handling a CISO's Agentic Concern

**Scenario framing:** a CISO says: "We love 1Password for our employees, but my engineers are building agentic AI workflows. These agents need access to our production databases. How do I govern these AI identities without creating a massive security hole?"

**Response structure — three parts:**

**1. Identity Separation:** "The first step in modern governance is recognizing that an AI agent is not just a service account — it's a dynamic identity. I'd recommend moving away from shared developer keys toward 1Password Service Accounts specifically scoped for AI. This ensures that if an agent is compromised via a prompt-injection attack, the blast radius is limited strictly to what that agent needs."

**2. Secrets Automation via Connect API:** "We'd deploy the 1Password Connect API within your infrastructure — Kubernetes or Docker. This lets AI agents fetch credentials programmatically. The governance benefit: the agent never actually knows the password, it holds a temporary, revocable permission to use it." Senior-level add-on: IP whitelisting and automated token rotation, so a leaked token becomes useless within minutes.

**3. Real-Time Governance & Visibility:** "We'd integrate the Events API with your SIEM. If an agent starts requesting credentials it's never accessed before, or requests them at unusually high frequency, that triggers an automated alert — a kill-switch for AI behavior that deviates from the norm."

---

## AHS Bridge: API Fluency

**Likely question:** "How technical are you with APIs?"

**Response:** "In my role at AHS, I deal with API-driven workflows every day through Microsoft Entra and Workspace ONE. When we moved to role-based access for Adobe Creative Cloud, we weren't just clicking buttons — we were ensuring the SCIM API was correctly syncing user attributes from our directory to the service provider. As a Senior TAM at 1Password, I see the API as the key to easing the tension between speed and security. I speak the language of developers who want to use the Connect API for CI/CD pipelines, and the language of a CISO who wants the Events API to ensure every secret access is audited and intentional."

**Why this framing works:** it doesn't stop at "I can use Postman" — it links the API directly to business value (audit trails, developer speed, identity sync) and grounds it in a real, specific example (Adobe CC/Entra) rather than a generic claim.

---

## Deep-Dive References Worth Reviewing Before Live Use

- 1Password's Extended Access Management (XAM) — positioning on total SaaS/identity sprawl visibility
- Public talks/demos on Securing AI with 1Password — useful for staying current on how the company itself frames the agentic trend externally
