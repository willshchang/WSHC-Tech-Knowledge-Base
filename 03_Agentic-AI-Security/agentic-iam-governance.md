# Agentic AI Security: Governing Agents Like Identities

**Document Type:** Knowledge Article  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** May 2026  

---

## Why Traditional IAM Assumptions Break in the Agentic Era

Traditional IAM was built for human users:
- One identity per person
- Predictable access patterns
- Sessions with defined start and end
- Humans can be held accountable

AI agents break all of these assumptions:

| IAM Assumption | Why It Breaks with Agents |
|---|---|
| Identity = human | Agents are non-human identities that act autonomously |
| Access is request-driven | Agents act continuously, often without explicit per-action approval |
| Sessions are bounded | Agents may run indefinitely across multiple systems |
| Accountability is clear | Agent actions may be opaque without explicit audit logging |

> "Traditional IAM assumptions no longer hold in the era of agents."

---

## The Three Defining Questions (Okta Framework)

Okta's **Blueprint for the Secure Agentic Enterprise** (2026) anchors governance on three questions:

### 1. Where are my agents?
Visibility into agent presence across the environment:

- Agent integrations catalogued
- Browser-based protection active
- Endpoint and network detection enabled
- Gateway detection in place
- AI agent risk detection running

### 2. What can they connect to?
Control over agent connectivity:

- MCP servers (Model Context Protocol)
- SaaS services
- Agent-to-agent connections
- Service accounts
- Vaulted credentials (no hardcoded secrets)

### 3. What can they do?
Governance over agent actions and lifecycle:

- Kill switch (instant access revocation)
- Runtime enforcement
- Agent lifecycle management
- Human-in-the-loop (HITL) controls
- Audit logs and telemetry

---

## Okta for AI Agents — Key Capabilities (GA 2026)

Okta extended its IAM platform to give agents **first-class identities**:

| Capability | Description |
|---|---|
| Discovery & onboarding | Any agent framework, cloud, or SaaS — all inventoried in one place |
| Least-privilege access | Scoped access to auth servers, secrets, service accounts, MCP servers |
| No hardcoded credentials | Credential vaulting via Okta Privileged Access |
| Token exchange | Brokered via Okta's MCP Bridge |
| Lifecycle management | Automated access reviews + instant kill switch |
| Audit trails | Full telemetry on agent actions |

Builds on existing Okta platform: **ISPM** (shadow AI), **Okta Privileged Access**, **Okta Identity Governance**.

---

## What Agentic IAM Does NOT Solve Yet

Agentic AI and Claude-powered tools (Claude Code, Claude Security) handle **code-level** security well. But large categories of security work remain unsolved:

- Managing identity sprawl and privilege risk
- Detecting active exploitation in real time
- Enforcing network segmentation and egress controls
- Preventing cloud misconfigurations (CSPM domain)
- Protecting secrets and machine credentials (NHI domain)
- Maintaining infrastructure integrity against configuration drift
- Monitoring third-party and supply chain access
- Cross-environment incident response and containment
- Cyber resilience: rollback, data recovery, service re-deployment

> "Security is about much more than finding vulnerabilities in code."

These domains all need governance — and none of them are solved by code scanning alone.

---

## Artemis Security — Agentic Security in Practice

Artemis (Series A) builds their entire platform with AI agents writing every line of code. Human engineers set constraints and review outputs — Claude implements.

Design thesis: **humans should bar-raise and direct, not make every individual security decision.**

> "You can't bolt intelligence onto static infrastructure. We started over."

Anthropic published a case study on how Artemis uses Claude as a core engineering collaborator.

---

## Key Takeaways

- **Agents are identities** — they need the same governance as human users: discovery, least privilege, lifecycle management, audit trails
- **Three questions anchor agentic IAM:** Where are my agents? What can they connect to? What can they do?
- **Kill switches and HITL controls** are non-negotiable — autonomous agents need human override capability
- **Agentic AI doesn't replace security** — code scanning is one slice; identity, network, cloud, and incident response still need humans and dedicated tooling
- **Okta's approach** treats agents as a natural extension of IAM — same platform, new identity type

---

## Official References

| Source | Link |
|---|---|
| Okta for AI Agents (GA announcement) | LinkedIn post — Ely Kahn |
| Resilient Cyber — Agentic IAM deep dive | https://www.resilientcyber.io/p/the-identity-layer-underneath-the |
| CSO Online — Identity in the Agentic Era | https://www.csoonline.com/article/4163365/what-cisos-need-to-get-right-as-identity-enters-the-agentic-era.html |
| Anthropic × Artemis Case Study | https://claude.com/customers/artemis |
| The Core Strength Network — AI won't kill cyber | LinkedIn post |
