# Practical Observability

**Document Type:** Personal POV / Opinion Piece  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** September 2026  

---

## The Core Thesis

Observability is the hot word in this space right now. Everyone building an endpoint tool, a SIEM, an agent platform wants to say they do it. But most of what gets called observability is really just data collection with a nicer name — and the difference matters more than the industry currently admits.

**My core position: observability without a purpose is just data.** The question that actually matters isn't "can we see it," it's "why do we need to see it, what are we going to do with it, and how." Skip that question and you've built a very expensive way to store logs.

---

## The False Observability Problem

A lot of what gets sold as observability is really a **time-travel snapshot**. Something breaks, an engineer pieces together logs, traces, and timestamps after the fact, and reconstructs what probably happened. That's forensics. It's genuinely useful — but it's not the same thing as observability, and calling it that muddies what the word should mean.

The actual definition, the one Origin's own writing traces back to Rudolf Kálmán's 1960 control theory paper (see `origin-blog-digest.md`), is about reconstructing a system's **internal state from its outputs, continuously** — not assembling a single after-the-fact timeline once you already know something went wrong. Real observability should let you catch the drift *while it's happening*, not just explain it cleanly once it's already cost you something.

**The test I'd apply to any "observability" product:** if the only thing it does well is answer "what happened after the fact," it's a logging tool with better UX. If it can tell you something is drifting wrong *before* the damage compounds, that's the real thing.

---

## The Real Question: Data for What?

Collecting data is the easy part now. Storage is cheap, agents generate enormous volumes of telemetry, and every vendor in this space can show you a dashboard full of activity. None of that answers the question that actually determines whether the product is worth anything:

- **Why do we need this data?** — what decision does it inform, what risk does it reduce
- **What can we leverage it on?** — governance, cost control, incident prevention, compliance evidence
- **How does it actually get used?** — does a human have to manually build a process around it, or does the system act on it

Skip these questions and observability becomes a very sophisticated way to generate reports nobody acts on.

---

## The Evidence, As of September 2026

This isn't abstract — three real, current examples from this same research session make the point concretely.

**Rootly acquired ThinkHive (July 28, 2026)** specifically because pure agent observability wasn't enough on its own. Their own framing: *"An AI agent that quietly starts giving wrong answers trips nothing."* They didn't just want to see the drift — they wanted to catch it, score it, and shadow-test a fix before it reached a customer. Observability was the first step, not the destination.

**C1's entire Launch Week (July 2026)** was built as a four-part sequence for exactly this reason: Discover → Secure → Govern → Remediate. They didn't stop at "here's what we found" — every discovery becomes a governed access item, every risky call gets scored and can be blocked in real time. The observability layer only exists to feed the action layer.

**Origin, by contrast, still stops at evidence** across all three of its own solutions (Governance, Adoption, Investment) — Discover, Detect, Investigate, Prove; Map, Track, Watch, Reuse; Observe, Attribute, Optimize, Prove. Every framework ends in an audit-ready record or a recommendation, never an actual action. The intelligence is genuinely powerful — SACR independently called them the most technically differentiated vendor in their category — but the customer has to build the "now what" themselves. That's not automatically fatal, but it's a real structural gap, and it puts the entire burden of value realization on whoever's using the tool.

---

## The Honest Counter-Argument

This doesn't mean every pure-observability company is doomed to be acquired or made irrelevant. There's a real counter-case, and it's worth taking seriously rather than assuming action always wins.

**Cribl is the clearest example.** Its entire business model is staying a neutral pipe rather than a destination — it deliberately doesn't act on the data, because acting on it would mean picking a side (which SIEM, which destination) and losing the vendor-neutral position that makes it valuable in the first place. For Cribl, staying "just data" is the whole point.

**Origin's implicit bet is that its data itself is the moat** — patented CPU-level telemetry, a local graph database on every endpoint, no kernel driver, no cloud round trip. If that technical depth is genuinely hard enough to replicate, other vendors might prefer to license or integrate with Origin's data rather than rebuild it themselves — the same way C1 explicitly supports ingesting third-party findings via API rather than only trusting its own.

**So the real dividing line isn't observability vs. action — it's whether the data itself is defensible enough to survive as a standalone layer, or whether it's replaceable enough that whoever owns the action layer downstream will eventually just acquire or out-build it.** Rootly buying ThinkHive is evidence for the second case. Cribl's decade-plus of staying independent is evidence for the first. Both are real, valid strategies — the mistake is assuming every observability company is playing the same game.

---

## Why This Matters for How I Evaluate Any Company in This Space

Going forward, when I look at a new company in the ZTAI ecosystem, "do they have observability" isn't the interesting question anymore. The questions that actually tell me something are:

1. **Does their observability feed an action, or does it stop at a dashboard?**
2. **If it stops at a dashboard, is their data specifically hard enough to replicate that it survives as a standalone layer?**
3. **If not, who's the most likely company to eventually own both the data and the action — and is that company already circling?**

This is the same "closes the loop automatically" property already built into the ZTAI ecosystem map's layer deep-dives (Detection, Endpoint Visibility, Hybrid Workforce Observability, Agentic Reliability) — this piece is really the *why* underneath that axis, not a new fact, but the reasoning that explains why the axis was worth adding in the first place.

---

## Key Takeaways

- **Observability without a purpose is just data** — the useful question is always why, on what, and how it gets acted on
- **A lot of "observability" is actually forensics** — piecing logs together after the fact is useful, but it's not the same as continuously reconstructing state, and conflating the two waters down what the word should mean
- **The current evidence points one direction more than the other** — Rootly, C1, and the broader pattern across this KB show real companies actively building or acquiring their way from pure observability into closed-loop action
- **But pure observability isn't automatically doomed** — Cribl's neutral-pipe model and Origin's bet on genuinely hard-to-replicate data both represent a real, valid alternative strategy, not a fallback position
- **The dividing line to watch for in any new company**: is their data defensible enough to survive standalone, or does it look like the next acquisition target for whoever owns the action layer above it

---

## Related

- See `ztia-ecosystem-map.md` for the "closes the loop automatically" property this piece explains the reasoning behind
- See `origin-research.md` for the Kálmán observability definition and Origin's own three-solution structure
- See `rootly-research.md` and `c1-research.md` for the concrete evidence cited above
- See `agentic-vs-human-identity-governance.md` for the companion POV piece this doc is styled after
