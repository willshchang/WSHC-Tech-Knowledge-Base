# Origin Blog Digest

**Document Type:** Living Content Digest  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  

---

## What This Is

A running, dated digest of Origin's own blog content — their thinking on endpoint AI observability, told in their own voice, over time. Kept separate from `origin-research.md` intentionally: the research doc holds stable, evergreen facts about the company and product; this doc holds their evolving public thinking, post by post, newest at the top.

Worth reading in full occasionally rather than skimming — several of these posts build directly on each other, and a few (the Kálmán observability origin story, the PowerShell/AMSI historical parallel, the Security-vs-Safety framework) are genuinely strong enough to use directly in conversation.

---

## Prelude is now Origin: the endpoint AI observability company

**Author:** Spencer Thompson (CEO) | **Date:** 2026-07-27

Not a soft rebrand — a **full company refocus**. Prelude Security is being wound down entirely; existing customers honored through their current contracts, with hope to migrate many to Origin. The company's full attention moves to Origin exclusively.

**How they got there:** Prelude's offensive testing work kept showing endpoint techniques succeeding, not from one missing signature but from structural limitations in how endpoint defenses were designed. Three conclusions became Origin's architecture: (1) endpoint tech should run in user mode, not depend on kernel drivers, (2) signature-based detection will keep losing ground to AI's novel, variable behavior, (3) the next generation has to be trace-driven observability.

**Worth remembering:** the team wrote the definitive published book on EDR evasion (No Starch Press, *"Evading EDR"*) — the observability-first bet is grounded in genuine published expertise on exactly how traditional defenses fail.

See full blog post: https://www.originhq.com/blog/prelude-is-now-origin

---

## Observability is the next generation of endpoint security. SACR just mapped the market.

**Author:** Nick Fitzsimmons | **Date:** 2026-07-22

Independent analyst firm Software Analyst Cyber Research (SACR) published a 5-zone Endpoint Control and Prevention market map on July 22. Origin placed in **Zone 3: "agent runtime observability."** Genuine third-party category validation, not self-description.

Frames the historical arc cleanly: file-based malware → antivirus (signatures) → fileless attacks → EDR (process behavior) → now agents, a third, non-deterministic vector nothing built for the first two can characterize.

**Worth remembering:** a separate LinkedIn post (Brightmind Partners) quoting the SACR report directly called Origin **"the most technically differentiated Zone 3 vendor in the market"** — citing patented CPU-level telemetry, a local graph database on every endpoint, no kernel driver, no cloud round trips.

See full blog post: https://www.originhq.com/blog/sacr-maps-endpoint-observability

---

## I Killed Our Standup: How I Use Origin as an Engineering Leader

**Author:** Keith Robertson (Engineering Lead) | **Date:** 2026-07-15

A real internal use case, not a product pitch. Keith replaced his team's daily standup with an automated morning report — an agent queries the last 24 hours of team AI activity and delivers a summary at 7am. The exact prompt is published: *"Use Origin to summarize what everyone on my team has been working on in the last 24 hours. Deliver this as a report to me every morning at 7 am."*

**The core thesis:** most engineering process (standups, status reports, syncs) exists to move knowledge around — "context transfer." Origin collects that context as a byproduct of people doing their actual work, so the process overhead disappears without losing the visibility it was providing.

**Worth remembering:** he addresses the "surveillance" question directly and honestly — team reaction was closer to "this is just permanent pair programming" than "micromanagement," and the visibility lets him stay *out* of the way rather than hover, stepping in early off a trace instead of late in a PR review. AI usage is also exposed through Origin's own **MCP server**, so other agents in the environment can query the aggregated activity directly, not just a human dashboard.

See full blog post: https://www.originhq.com/blog/i-killed-our-standup

---

## Observability Requires Proximity

**Author:** Chris Singlemann | **Date:** 2026-05-26

A genuine architecture argument for why endpoint-native beats every alternative layer, walked through honestly rather than dismissively:

- **CASB / network monitoring** — sees traffic crossing a network boundary, but local agent processes (Claude Code, Cursor) often communicate via IPC/WebSocket to a local CLI before anything hits the wire — nothing to inspect
- **API-side telemetry** — Anthropic's own OpenTelemetry schema for Claude Code redacts prompt content and raw file contents by default; even unredacted, API telemetry only shows what the model received/returned, not what the agent did locally afterward
- **Traditional EDR** — closer architecturally (runs on-device) but built for known-bad signatures; agents inherit user credentials and perform legitimate-looking actions, so "is this authorized and in line with intent" isn't a security question EDR is built to answer, it's closer to a *safety* question

**Worth remembering:** cites real external sources throughout (OpenTelemetry's own definition of observability, IBM's observability pillars, Anthropic's actual Claude Code monitoring docs, Harmonic Security's research on Claude/Cowork blind spots) — well-grounded, not just assertion.

See full blog post: https://www.originhq.com/blog/observability-requies-proximity

---

## AI Adoption and the Distribution of Intelligence Problem

**Author:** Chris Singlemann | **Date:** 2026-05-21

Core reframe: **AI spend is a resource allocation decision, not a software line item.** Vendor dashboards show token consumption by user but never whether that consumption maps to work worth investing in.

Two concrete problems raised: (1) frontier models get used by default for work a cheaper model could handle identically, with no visibility into which is which; (2) "adoption is not the same as proficiency" — some employees have genuinely figured out how to get far more value from the same AI tools, and there's currently no mechanism for that skill to spread across a team, because the best workflows live invisibly inside individual sessions.

**Worth remembering:** the marketing-team example — one person loads brand context and campaign history upfront, the other opens a blank chat window — is a clean, relatable illustration of the adoption-vs-proficiency gap.

See full blog post: https://www.originhq.com/blog/distribution-of-intelligence

---

## Your CISO is Becoming a Safety Architect (Whether They Know It or Not)

**Author:** Spencer Thompson (CEO) | **Date:** 2026-05-19 (also syndicated to SC Media, June 25, 2026)

The sharpest conceptual piece in the whole set. Core argument: the CISO role is shifting from **Security** (protecting against actors who intend harm) to **Safety** (ensuring complex systems behave reliably even when nobody intends harm) — the chemical-plant/nuclear-reactor framing, where the greatest risk isn't sabotage but a cascading failure nobody anticipated.

Cites real external research: Anthropic's own alignment work on agent "incoherence" failures (an agent tasked with managing a nuclear plant gets distracted reading French poetry and causes a meltdown — illustrative, not literal), Dario Amodei's "adolescence of technology" essay, GitHub Copilot's 90% Fortune 100 adoption, Claude Code's 29M daily installs.

**The closing line, genuinely quotable:** *"The agents are already inside the house. The question is whether you can see what they're doing."*

See full blog post: https://www.originhq.com/blog/your-ciso-is-becoming-a-safety-architect
Also syndicated to SC Media: https://www.scworld.com/perspective/your-ciso-is-becoming-a-safety-architect-whether-they-know-it-or-not

---

## Exploring the Broken Audit Trail for Artificial Intelligence

**Author:** Chris Singlemann | **Date:** 2026-05-19

Introduces **agent trajectory** as the core object that needs to be captured — the complete ordered record of a run: instruction, every reasoning step, every tool call, every file touched, in sequence. Argues this can't be reconstructed after the fact from API logs or network traces; it has to be observed live, at the endpoint.

**Real regulatory hook, worth remembering precisely:** the **EU AI Act reaches full enforcement in August 2026**, requiring automatic, structured, auditable logging for high-risk AI systems — fines up to **€35 million or 7% of global turnover** for non-compliance. NIST's AI Risk Management Framework cited as the equivalent US standard for federal contractors and regulated industries.

**A concrete illustration:** two employees using Claude Code on the same task — one takes 8 steps, the other 80, touching dozens of extra files — can produce comparable outputs at wildly different cost, and without trajectory visibility, you cannot see or optimize that difference.

See full blog post: https://www.originhq.com/blog/exploring-the-broken-ai-audit-trail

---

## AI Visibility Belongs on the Endpoint

**Author:** Matt Hand | **Date:** 2026-05-11

A refreshingly honest comparison of the three layers where AI telemetry could be collected — network, browser, or endpoint — including genuine credit to competitors. Network-layer collection is a legitimate, fast-to-deploy answer if the goal is just watching egress to public AI providers. Enterprise browsers (**named specifically: Island, Menlo**) are the right tool for in-page control of browser-based chatbot use. Neither sees what an agent does on the host after a response returns, or agents that never touch a browser or public API at all.

**Worth remembering — the honest cost admission:** *"There's no way around this: endpoint visibility means deploying software on the endpoints... there is a rollout step that network-layer collection doesn't have, and we're not going to pretend otherwise."* Refreshingly non-hype framing: value minus pain, and for organizations where AI does real work on real machines, the math isn't close.

See full blog post: https://www.originhq.com/blog/ai-visibility-belongs-on-the-endpoint

---

## What is Endpoint Observability?

**Author:** Matt Hand | **Date:** 2026-04-30

The best definitional piece in the set. Traces "observability" back to its actual origin: **Rudolf Kálmán's 1960 control theory paper** — a system is observable if you can reconstruct its internal state from its outputs over time, not just detect that an output occurred.

**The factory floor analogy, genuinely clean:** a part inspector at the end of an assembly line who flags a faulty unit is *monitoring*. Instrumenting the whole line so a faulty unit traces back to a specific machine with a worn bearing is *observability*. Same factory, completely different ability to act.

Applies this directly to agents: the "internal state" worth measuring is **intent** — what the user asked the agent to do, and whether the agent's actions align with that. Traditional monitoring watches for known-bad patterns; it structurally cannot answer whether behavior matches intent.

See full blog post: https://www.originhq.com/blog/what-is-endpoint-observability

---

## Lacking Intelligence About Our Intelligence

**Author:** Spencer Thompson (CEO) | **Date:** 2026-04-23

The founder's own origin story for why Origin was built — genuinely personal, not a case study. In October 2025, Spencer asked his own product/engineering leads a simple question — who's using AI, and how — and discovered no tool in their existing stack (MDM, EDR) could answer it.

**A genuinely useful maturity framework, distinct from anything else in this KB:** three phases of AI adoption — **Adopt** (convince people to use it at all, zero thought given to monitoring or cost), **De-constrain** (open the budget, get out of the way, encourage maximum usage — most organizations are here now), **Rationalize** (which model for which work, where is spend actually going — the phase that exposes everything not built during De-constrain).

**Worth remembering — real external stat:** Uber's CTO publicly disclosed the company **blew through its entire Anthropic AI budget by April** 2026.

See full blog post: https://www.originhq.com/blog/lacking-intelligence-about-our-intelligence

---

## What is AI Observability?

**Author:** Spencer Thompson (CEO) | **Date:** 2026-04-21

Opens with a personal Datadog-bill anecdote from his first company — observability as "the ability to understand the internal state of a system," paid for specifically so failures could be diagnosed fast enough to act on them. Argues traditional observability assumed deterministic software; AI agents are non-deterministic, multi-threaded, and take actions nobody individually approved.

**The sharpest line in the piece:** *"Policy without observability is theater."* Governance rules written without the ability to verify whether agents are actually following them are just words.

Reinforces the EU AI Act point (auditable records required for high-risk systems, can't be produced retroactively) and frames AI observability as the shared foundation underneath security, governance, cost, and performance questions alike — you can't solve any of the four without first answering "what is my AI actually doing."

See full blog post: https://www.originhq.com/blog/what-is-ai-observability

---

## The Era of Semantic Security: Computer Use Agents and the End of Signatures

**Author:** Matt Hand | **Date:** 2025-11-26

The deepest, most technically substantive piece in the set — genuine security research, not product marketing. Central argument: local computer-use agents make legitimate and malicious use **semantically identical** at the operating-system level — same API calls, same objects, same observable behavior. The only difference is context and intent, which existing tools have no concept of.

**A real proof-of-concept, not a hypothetical:** the team built an internal research tool called **"Terminator"** and used a local agent — with only the permissions a user had already granted it, no malware, no exploits — to read a sensitive iMessage business conversation directly off a laptop. Demonstrated on video.

**The historical parallel, genuinely excellent and worth using in conversation:** draws a direct line to **PowerShell and AMSI**. PowerShell became a favored attacker tool specifically because its legitimate and malicious uses were semantically identical — an admin querying Active Directory looks exactly like an attacker doing reconnaissance. AMSI (the defensive response) caught the obviously malicious cases but was quickly bypassed by motivated adversaries. The piece argues today's LLM guardrails (prompt filtering, safety classifiers) are "just AMSI for the LLM age," and will fail the same way — every jailbreak and successful prompt injection is a preview.

**Worth remembering:** "incentivized overpermissioning" — agents become more useful with more access, so both the agent itself and the user asking for expanded permissions are structurally incentivized to keep granting more, regardless of security implications.

See full blog post: https://www.originhq.com/blog/era-of-semantic-security

---

## It's (Finally) Time For The Next Generation of Endpoint Security

**Author:** Spencer Thompson (CEO) | **Date:** 2025-10-26 (written while still Prelude Security, pre-pivot)

The oldest and most historically grounded piece — genuinely useful for understanding the full arc the company sees itself part of. Opens with a sharp framing device: the ideal cybersecurity budget for any organization is $0 — security is a cost nobody actually wants, which explains why change in the category only happens under real pressure, not preference.

**The historical arc, cleanly laid out:**
- **Antivirus (1990s–2010s):** internet + email created the file-download attack vector; signature-based "known bad" databases worked well until attackers moved to fileless techniques (PowerShell, WMI) that avoided files entirely
- **EDR (2010s–2025):** kernel-level telemetry + cloud-shared signatures (CrowdStrike, Defender, SentinelOne) answered fileless attacks — but adoption took years even with clear threat intelligence, because installing new agents is genuinely painful

**Why change is happening again now, argued with real numbers:** ransomware up 104% in two years despite widespread AV/EDR adoption, now costing organizations over $50B annually; Microsoft's own Windows Resiliency Initiative (June 2025) shifting endpoint security away from kernel-level architecture toward user mode — external validation for Origin's own architectural bet, not just their own claim.

**The closing argument:** an endpoint's function has changed again — 1990s: gateway for files, 2010s: home-work applications, 2025+: **host for a new form of intelligence**. AI agents create a genuinely new attribution problem — code execution that's simultaneously novel (can't be signatured), autonomous (no human verification), and legitimate-looking (identical to normal operations) — breaking the core assumption both AV and EDR were built on.

See full blog post: https://www.originhq.com/blog/time-for-the-next-generation-of-endpoint-security

---

## Additional Posts Found, Not Yet Read

A few older/deeper technical posts surfaced during this research pass but weren't part of the original reading list — flagging for a future session if useful:

- *The Mythos We Have At Home: A Patch-Diffing Pipeline for N-Day Generation*
- *All Your Claude Are Belong To Us — Redux*
- *Your Agent's Hidden Supply Chain*
- *Escaping the Sandbox: Confused Deputies* (referenced inline in "Observability Requires Proximity")

These appear to be older, deeper security-research-oriented posts, possibly from a separate research/technical blog category rather than the main "Building Origin" blog.
