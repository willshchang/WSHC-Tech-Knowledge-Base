# Agentic Reliability

**Document Type:** Personal POV / Cross-Cutting Thesis  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** September 2026  

---

## What This Is

This doc holds two related but distinct pieces of thinking, both pulled out of `ztia-ecosystem-map.md` because they're genuinely cross-cutting analysis, not pure layer-mapping content — and both are likely to keep growing as this KB grows.

**Section 1** covers the Agentic Reliability layer itself — the specific, concrete, currently-active battleground for what "reliable AI workforce" actually means in production.

**Section 2** is the broader thesis this layer is arguably the sharpest current proof of: that none of this is a new problem, just an old one wearing a new workforce's clothes.

---

## Section 1: Agentic Reliability

A genuinely new layer in the ZTAI ecosystem, distinct from Hybrid Workforce Observability (Origin) despite the surface-level similarity — both watch "agent behavior," but the *object* being watched is different. Origin watches internal employee tool use on their own endpoints. Agentic Reliability watches whether a company's **own shipped AI product**, built and deployed to its own customers, is actually working correctly.

This is also the layer most directly answering the question the whole ecosystem keeps circling back to: as AI takes on more of the actual work, how do you know it's doing that work *well* — not just that it ran, but that it produced something correct, safe, and worth the cost.

### The Two Sub-Layers: Visibility vs. Observability

Split using the same distinction already established elsewhere in this ecosystem:

**Visibility — [Cortex](../03_Industry-Intelligence/Company-Portfolio/Cortex/cortex-research.md):** catalogs services, APIs, and ML models, scores them against defined engineering standards (code coverage, vulnerability SLAs, package freshness), and drives guided remediation (scaffolding, org-wide initiatives). Aggregates signals already produced by other tools (Datadog, Snyk, PagerDuty) rather than reconstructing causal chains itself — structurally the same function Tanium/Ivanti perform for devices, applied to software services instead.

**Observability — [Lemma](../03_Industry-Intelligence/Company-Portfolio/Lemma/lemma-research.md):** one trace per agent execution, reconstructing the causal sequence of a live production run to catch **silent semantic failures** — an agent that completes without crashing but got the task wrong (loop, bad tool call, misread intent). The differentiator: automated remediation closes the loop in the same workflow, proposing a fix and opening a PR directly, not just flagging the failure.

**Why these two don't compete with each other, or with Origin:** Cortex answers "do we even have visibility into what exists and whether it meets our bar" — an earlier-stage question. Lemma answers "why did this specific live run fail, and can it self-correct" — a later-stage, causal question. Origin answers a structurally different question again — what is my *workforce* (human + internal agents) doing, not what is my *product* doing. Three genuinely different buyers inside the same company: IT/Security (Origin), Engineering leadership (Cortex), and the team that built and owns the shipped agent (Lemma).

### The Full Three-Way Comparison: Origin vs. Cortex vs. Lemma

| | Origin (Hybrid Workforce Observability) | Cortex (Agentic Reliability — Visibility) | Lemma (Agentic Reliability — Observability) |
|---|---|---|---|
| **What it watches** | Internal employees + agents on their own endpoints | Software services, APIs, ML models in the engineering catalog | A company's own shipped AI agent product, live in production |
| **Visibility vs. Observability** | Observability — causal chain (prompt → reasoning → action → outcome) | Visibility — state snapshot scored against a standard | Observability — causal trace of a live execution |
| **Does it close the loop automatically?** | No — surfaces findings for a human (or another system via query/MCP) to act on | No — guided remediation (scaffolding, initiatives), still human-driven | **Yes** — detects root cause and delivers a fix directly (PR or API), no human step required |
| **The buyer inside the company** | IT / Security | Engineering leadership | The team that owns the shipped agent product |
| **The core question answered** | "What is my workforce actually doing?" | "Do we have an accurate, standards-scored inventory of our services?" | "Is my own AI product actually working, and can it self-correct?" |

**The key insight this table makes explicit:** "Observability" alone doesn't imply automated remediation — Origin and Lemma are both genuinely Observability-layer (deep, causal), but only Lemma closes the loop with automated action. This is a second, independent axis from the visibility/observability split, worth tracking separately as this space evolves — a company can be deep on causal reconstruction and still leave the fix entirely to a human, or vice versa.

**Why Origin doesn't move to Agentic Reliability even though it clearly does causal observability of agents:** the object being watched is the primary axis this layer split is built on, not the mechanism. Origin watches internal employee/workforce tool use; Agentic Reliability watches whether a company's own shipped product works. Even if Origin eventually adds automated remediation, it would still belong in Hybrid Workforce Observability — because it's watching a different *thing*, not because it lacks automation.

### Why This Layer Will Keep Growing

Rootly's acquisition of ThinkHive (July 2026, see `rootly-research.md`) is a direct, real-time example of a third company entering this exact space — not by building from scratch like Lemma, but by acquiring the capability and bolting it onto an existing, mature incident-management platform. As more companies race to prove their AI products are reliable in production, expect this layer to keep adding entrants faster than most others in the ecosystem — it's arguably the most immediately monetizable pain in the whole map right now, since "is the AI product I shipped actually working" is a direct revenue and trust question, not a background security concern.

---

## Section 2: The Old Problem, New Workforce

None of this is a new problem. Every layer in the ZTAI map — however novel the vocabulary sounds — is solving the same legacy organizational question every company has always had to answer: **who should be doing what, and how do you keep the information they're working with clean enough that it doesn't bleed into the next person's (or model's) work.**

Trace the last few years of AI engineering vocabulary and the pattern is obvious in hindsight: **prompt engineering** (get the wording right) → **context engineering** (get the right information into the window) → **harness engineering** (build the scaffolding of tools, memory, and middleware around the model) → **loop engineering** (structure the repeated cycles of plan-act-observe) → **graph engineering** (model the relationships between tasks, agents, and data explicitly). Each wave looks like a new discipline. Each one is actually the same underlying problem restated at a different level of abstraction: **role and task definition, and data hygiene, done for a non-human workforce instead of a human one.**

This reframes the whole ecosystem cleanly:

- **Cribl's entire thesis** is keeping the data stream clean so it doesn't bleed into the wrong destination or blow the budget getting there
- **Dosu's entire thesis** is keeping an agent's *context* clean so it doesn't hallucinate on bad or missing grounding
- **Origin and Lemma's entire theses** are catching the moment context or intent already bled into the wrong outcome, after the fact
- **RBAC/ABAC, restated for agents**, is exactly "who should be doing what" — the oldest access-control question there is, now applied to a workforce that doesn't sleep

The tools are new. The discipline they're all reaching for — clear roles, clean data, contained blast radius — is not. This is the connective thread running underneath every layer in the ZTAI map, whether or not a given company would describe itself that way.

**Why Agentic Reliability (Section 1) is arguably the sharpest current proof of this thesis:** it's the layer where "is the new workforce doing quality work without going rogue" gets asked most directly and most urgently — every company entering this space (Lemma from scratch, Rootly via acquisition, Cortex by extension of an existing catalog) is independently arriving at the same conclusion: the old discipline of "verify the work, catch the mistake, fix it before it compounds" doesn't disappear just because the worker is now an agent. It just needs new tooling to do the same job.

---

## Related

- See `ztia-ecosystem-map.md` for the Agentic Reliability layer's placement in the full ecosystem table
- See `origin-research.md`, `cortex-research.md`, and `lemma-research.md` for each company's individual deep dive
- See `rootly-research.md` for the ThinkHive acquisition as a live example of this layer's growth
- See `practical-observability.md` and `agentic-vs-human-identity-governance.md` for the other two standalone POV pieces in this KB
