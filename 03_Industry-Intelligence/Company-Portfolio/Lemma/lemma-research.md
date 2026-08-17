# Lemma — Company Research File

**Document Type:** Company Intelligence / Portfolio Research  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** August 2026  
**Official Reference:** https://www.uselemma.ai  

---

## Company Snapshot

| Field | Detail |
|---|---|
| **Founded** | 2025, San Francisco, CA — via Y Combinator Fall 2025 batch |
| **Stage** | Pre-Seed |
| **Total funding** | $2.3M (announced August 13, 2026) |
| **Investors** | Matrix, Y Combinator, Liquid 2 Ventures, Vermilion Cliffs Ventures, Irregular Expressions, Cervin Ventures, Comma Capital, Position Ventures, Eight Capital — plus operator angels from OpenAI and xAI |
| **Recognition** | Named by Forbes as one of the top startups to watch from YC's Fall 2025 batch |
| **Scale** | 1M+ agent traces processed per day as of the pre-seed announcement |
| **Category** | AI agent observability + automated remediation |
| **Website** | https://www.uselemma.ai |

---

## Founders

- **Jerry Zhang (Co-Founder & CEO)** — met Cole Gawin as freshmen in USC's startup incubator
- **Cole Gawin (Co-Founder)** — described as developing "the next generation of intelligent systems"

**The founding motivation, in Zhang's own words:** "Cole and I started Lemma because we experienced the pain of building AI agents firsthand... We kept running into the same problem: agents would [fail silently]."

---

## The Core Problem — "Silent Failures"

Lemma's central thesis, and the sharpest part of their positioning: **an AI agent failure often doesn't look like a failure at all.** Nothing crashes. No error throws. The agent completes its run and returns a plausible-looking response — while the user quietly gets the wrong outcome and walks away.

**Specific failure modes named:** agents stuck in loops, failed tool calls, misread user intent. None of these trip a traditional software monitoring alert, because from a systems perspective, the process executed successfully.

**Why this matters at scale, per the company's own framing:** as agents take on real work in healthcare, finance, and law, a single silent miss can cascade into lost customers and real product damage — and because nothing alerts on it, the team often doesn't find out until a customer complains, if they find out at all.

**A cited stat from their YC launch:** agent performance can degrade roughly 40% within a few weeks in production due to real-world input drift (new user behaviors, unseen edge cases) — meaning what passed evaluation in testing can quietly break in front of customers without anyone noticing the regression happening.

---

## How Lemma Actually Works

**Core mechanism: one trace per agent execution.** Engineering teams instrument their agent with the Lemma SDK; every run generates a single trace, with LLM calls and tool calls captured as child spans within that trace (not separate traces) — Lemma calls this its "trace contract," the one rule instrumentation has to follow for the analysis to work correctly.

**The pipeline, end to end:**

1. **Trace ingestion** — the SDK sends structured trace data for every agent execution
2. **Semantic failure detection** — Lemma analyzes the trace for silent failures dashboards miss (not just "did it error," but "did it actually accomplish the task")
3. **Root cause diagnosis** — pinpoints the exact step in the trace where things went wrong, across potentially thousands of traces
4. **Automated remediation** — generates a proposed fix (an optimized prompt candidate, a corrected tool-call pattern) and delivers it automatically, either via API or by **opening a pull request directly in the customer's codebase**

**The differentiator, stated plainly:** detection and resolution happen in one workflow. Most observability tooling stops at "here's what went wrong" and leaves the fix to an engineer. Lemma's stated goal is closing that loop — "Deploy 1x. Learn forever." — agents that continuously improve from real production outcomes instead of silently degrading until someone notices.

---

## Target Customer & Go-to-Market

**Target profile:** engineering teams from seed stage through Series B that are **already operating AI agents at significant production volume** — not teams still prototyping, but teams whose agents are doing real work with real users.

**Stated GTM motion (per YC/investor materials):**
- **First 10 customers:** high-touch pilots with YC network and inbound demo leads, Lemma's own team handling onboarding directly until measurable reductions in agent failures are demonstrated
- **First 50:** convert pilots into public case studies, targeted outbound to engineering/ML leads, self-serve trial emphasizing low-friction GitHub PR/API integration
- **First 100:** add enterprise controls (audit trails, approvals, RBAC) and formal SLAs, build integrations with adjacent LLM platforms, CI/CD, and observability tooling

**"Lemma Weekly"** — a public Friday newsletter/blog on AI agent observability and reliability, covering real incidents and engineering lessons across the industry (not just their own product) — a content-marketing play building credibility in the space ahead of broader GTM.

---

## Competitive Landscape

| Adjacent Player | Relationship to Lemma |
|---|---|
| **Origin** | Different object of observation entirely — Origin watches *employee* AI tool usage on endpoints (Claude, Cursor used internally). Lemma watches a company's *own shipped agent product* in live production. Not really competitors — different layer, different buyer |
| **Traditional APM (Datadog, New Relic)** | Built for deterministic software — crashes, latency, error rates. Silent semantic failures (agent ran fine, got the wrong answer) are structurally invisible to this category of tooling |
| **General LLM observability (LangSmith, Langfuse)** | Closer competitors — trace-based LLM/agent observability. Lemma's specific differentiation is the closed-loop automated remediation (PR-opening), not just detection and tracing |
| **Cortex.io** | Different layer — Cortex catalogs and scores software services/repos against engineering standards (visibility). Lemma reconstructs causal traces of live agent behavior to find and fix semantic failures (observability). See `cortex-research.md` for the full distinction |

---

## ZTIA Layer Placement

**New layer: Agentic Reliability — Observability sub-row.** Lemma answers "is my own shipped AI agent actually working correctly in production, and can the fix happen automatically." Distinct from Cortex (Visibility sub-row of the same layer) and from Origin's Hybrid Workforce Observability (which watches internal employee AI tool usage, not a company's own deployed agent product). See `ztia-ecosystem-map.md` for the full layer breakdown.

**What this layer cannot do:** Lemma doesn't govern access, doesn't vault credentials, doesn't discover shadow AI usage — it's scoped specifically to whether an already-deployed, already-governed agent is producing correct outcomes.

---

## Key Takeaways

- **The core insight is genuinely sharp:** most AI agent monitoring watches for crashes and errors; Lemma watches for outcomes that are silently wrong despite the process completing successfully
- **The closed-loop remediation is the real differentiator** — detection alone is common in this emerging category; automatically proposing and delivering a fix (via PR or API) in the same workflow is not
- **This is a different object of observation than Origin** — Lemma watches a company's own shipped agent product in production, not employee AI tool usage on endpoints. Complementary, not competing
- **Very early stage** — pre-seed, $2.3M, tiny team, genuinely unproven at scale beyond early pilots, though the 1M+ daily traces figure suggests real usage already exists
- **Worth watching, not yet a safe bet** — the problem framing (silent semantic failures) is one of the sharpest, most under-addressed pain points in the current AI agent tooling landscape, but the company itself is unproven

---

## Official References

| Source | Link |
|---|---|
| Lemma | https://www.uselemma.ai |
| Lemma Docs | https://docs.uselemma.ai |
| Lemma Weekly | https://www.uselemma.ai/weekly |
| Lemma — YC Company Profile | https://www.ycombinator.com/companies/uselemma |
| GlobeNewswire — $2.3M Pre-Seed Announcement | https://www.globenewswire.com/news-release/2026/08/13/3344773/0/en/2-3m-pre-seed-for-lemma-backed-by-matrix-yc-openai-xai-operators-to-fix-silent-ai-agent-failures.html |
