# Agentic vs. Human Identity: Why Governance Needs to Evolve

**Document Type:** Personal POV / Opinion Piece  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** September 2026  

---

## The Framing Problem Nobody Is Fixing

When people talk about AI agent risk, the conversation usually lands on "the agent acting on its own." That framing makes it sound like the agent has intent — like it woke up and decided to do something.

It didn't.

And I think that misframing is exactly why governance frameworks keep missing the point.

---

## Agents Don't Decide. They Execute.

Here's what I actually believe after spending time in both enterprise IT operations and identity security:

**AI agents don't think. They don't make decisions. They meet conditions.**

Every action an agent takes traces back to a condition, a prompt, or a policy written by a human — or defined by another agent's code. The agent has no stake in the outcome. It has no judgment. It has no sense of consequence.

What it does have is:
- Speed — machine execution speed
- Scale — no fatigue, no context switching
- Scope — access to whatever it was granted, used fully and without hesitation

That combination — fast, tireless, and exactly as privileged as you made it — is where the real risk lives.

> "The security risk in agentic AI isn't rogue intelligence. It's unchecked execution of human-defined conditions without enough visibility to know when those conditions are wrong."

---

## Why This Is Different From Human Identity

I've spent years governing human identities at enterprise scale. Here's the fundamental difference:

| Dimension | Human Identity | Agentic Identity |
|---|---|---|
| **Decision making** | Humans choose — they can deviate, escalate, use judgment | Agents execute — conditions trigger actions, no judgment applied |
| **Context awareness** | Humans recognize when something feels wrong | Agents only see what they were given access to see |
| **Access usage** | Humans use a fraction of their granted access on any given day | Agents use all relevant access every time a condition fires |
| **Accountability** | Humans are accountable by nature — there's a person behind the action | Agent accountability requires explicit audit design — it doesn't exist by default |
| **Speed** | Human-speed decisions, human-speed actions | Machine-speed execution — lateral movement in seconds, not minutes |
| **Failure mode** | Human makes a bad call — contained, recoverable | Agent executes a bad condition at scale — fast, broad, hard to reverse |

The most dangerous thing about an AI agent isn't that it will go rogue. It's that it will do exactly what you told it to do — perfectly, repeatedly, at scale — even when what you told it to do was wrong.

---

## The Condition Design Problem

Traditional IAM assumed that access governance was the hard part. Grant the right access, review it periodically, revoke it on offboarding. Done.

Agentic IAM has a layer above that: **condition design governance.**

Because the question isn't just "does this agent have the right access?" It's "are the conditions driving this agent's actions correct, safe, and scoped appropriately?"

A poorly scoped condition + broad permissions = an agent doing exactly what it was told, at machine speed, across your entire environment, with no judgment to stop it.

This is why I think **human-in-the-loop isn't about distrusting AI.** It's about acknowledging that condition design is imperfect — and humans need checkpoints to catch the gaps before the agent runs away with them.

---

## What Governance Actually Needs to Cover

For human identities, governance asks:
- Who has access to what?
- Is that access still appropriate?
- Did anything change?

For agentic identities, governance needs to ask more than that — what conditions is an agent operating under, who defined those conditions, what can it trigger autonomously versus what requires human approval, and what did it actually do. The industry's own answer to this (Okta's "where are my agents / what can they connect to / what can they do" framework, and the broader agentic IAM landscape) is covered in full in `agentic-identity-governance.md` — this piece is about the philosophy underneath that framework, not a restatement of it.

> Visibility and observability aren't optional in agentic systems. They are the governance. Without them, you have no way of knowing when a condition is wrong until the damage is already done.

---

## The Network Layer Angle: Identity-Aware Networking as a Safety Layer

This is where my background in identity security intersects directly with the **Network layer** of the ZTAI stack.

An identity-aware network — Tailscale is the clearest example — ties every connection to a verified identity, human or machine. ACLs define exactly what each identity can reach. Nothing connects that isn't explicitly permitted.

For agentic workloads, this matters more than most people realize:

- An agent's network access can be **scoped at the policy layer** — it can only reach the systems its conditions actually require
- If an agent is compromised or a condition misfires, **network segmentation limits the blast radius** — the agent can't reach what it was never permitted to reach
- Network-layer audit logs capture **what connected to what** — one layer of the observability picture, not the whole picture

This layer doesn't govern the conditions themselves. It doesn't inspect what an agent does after it connects — that's the job of Detection and Hybrid Workforce Observability layers. But it controls **what the agent can reach** — and in a world where agents execute at machine speed, constraining the reachable surface is one of the most important safety controls available.

> Network-layer least privilege is agentic safety infrastructure. Not sufficient on its own — but foundational, and it's just one layer of a much larger ZTAI stack. See `ZTAI-ecosystem-map.md` for how this connects to Identity & Access, Detection, and Hybrid Workforce Observability.

---

## Where This Is Headed

The Mythos incident — where AI conducted 80–90% of a state-sponsored cyber espionage campaign autonomously — is not a future warning. It already happened.

The agents executing those attacks weren't thinking. They were meeting conditions — at machine speed, across 30 organizations, with minimal human supervision.

The defenders who win in this environment will be the ones who:
1. Govern the conditions agents operate under, not just the access they have
2. Build observability into every layer — network, identity, application, behavior
3. Maintain human-in-the-loop checkpoints at every decision point that matters
4. Treat the kill switch as a first-class feature, not an afterthought

Identity security was always the control plane of the enterprise. In the agentic era, it becomes the control plane of the agents too.

---

## Key Takeaways

- **Agents don't decide — they execute conditions defined by humans.** The risk is unchecked execution, not rogue intelligence
- **The failure mode is scale and speed** — a bad condition executes perfectly, repeatedly, across your entire environment
- **Condition design governance** is the new layer above traditional access governance that most frameworks haven't caught up to
- **HITL is about imperfect conditions**, not distrust of AI — humans need checkpoints to catch what condition design gets wrong
- **Identity-aware networking** (Tailscale being the clearest example) scopes what agents can reach — network-layer least privilege as one foundational piece of agentic safety infrastructure, not the whole answer
- **The Mythos incident proved this isn't theoretical** — autonomous AI-driven attacks are already happening at scale

---

## References & Further Reading

| Source | Link |
|---|---|
| Anthropic — Mythos Preview (Frontier Red Team) | https://red.anthropic.com/2026/mythos-preview/ |
| Anthropic — Project Glasswing | https://www.anthropic.com/glasswing |

*For sourcing on Okta's agentic framework and the broader agentic IAM landscape, see `agentic-identity-governance.md`.*
