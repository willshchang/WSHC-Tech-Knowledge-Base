# The Growing Pain

**Document Type:** Living Field Journal / POV Piece  
**Author:** Will Chang  
**Audience:** Knowledge Growth  
**Last Updated:** July 2026  

---

## What This Doc Is

This is a running, growing capture of real pain points observed in the field — moments where something is clearly broken, inefficient, or structurally missing, caught in the act rather than reconstructed after the fact.

It's not tied to one framework. Some entries will naturally connect to PIPR (Proactive Incident Pattern Recognition). Others might connect to ecosystem gaps, governance gaps, or nothing named yet. The point is to capture the pain first, honestly and specifically, and let the pattern or lens emerge afterward — not force every entry into a predefined shape.

This doc is a seed bank. Some entries stay as observations. Some eventually become lab projects, KB pieces, or interview talking points. This is where they start.

---

## Entry: The iOS Compliance Incident (July 2026)

**Where:** AHS service desk queue

**The pain observed:** Roughly 85% of my ticket queue is repetitive, copy-paste-instruction solvable. The answer is already known somewhere — it just doesn't reach the next person fast enough.

**The specific incident:** A cluster of INCs came in where clients couldn't open Outlook or Teams on their mobile phones. The common configuration across every ticket: iOS 16 and under, enrolled in Workspace ONE (WSO).

**Root cause — identified immediately, without looking up the error:** Microsoft had stopped supporting older iOS versions with the most current Office mobile app builds. Devices were failing Intune compliance checks as a downstream result. I didn't need to search the error message ("Intune xxx compliance xxx") — the pattern was recognizable on sight from experience.

**Fix, identified at the same time:**
1. Update device to iOS 26.5
2. Delete existing Office apps
3. Redownload from Intelligent Hub to get the compliant, current version

### The Timeline of What Actually Happened

| Step | What Happened | Time Cost |
|---|---|---|
| 1 | Pattern identified, root cause diagnosed, fix known — on first ticket | Immediate |
| 2 | Brought up to manager with proposed solution | Same week |
| 3 | No action taken | — |
| 4 | More tickets came in over the following days | Ongoing ticket volume, repeated manual triage |
| 5 | Raised again on a Friday | ~1 week after original flag |
| 6 | Manager finally recognized severity | 1 week later |
| 7 | Email looped in service desk team leads to push awareness ahead of the weekend, to protect on-call | 1 week later |
| 8 | "A proper KB will be built later" | Still pending as of writing |

**Total elapsed time from correct diagnosis to team-wide awareness: roughly one week**, during which the same ticket type kept arriving and getting manually triaged one at a time — each instance costing an engineer's time to independently re-reach the conclusion I'd already reached on day one.

### What Should Have Happened (The PIPR Lens)

This is exactly the workflow PIPR was designed for:

1. **Pattern recognition** — first instance flagged as a potential systemic issue, not a one-off ticket, the moment a second matching case appeared
2. **Root cause documentation** — captured immediately in a lightweight internal KB entry, while the diagnosis was fresh
3. **Proactive push** — surfaced to service desk and on-call *before* the weekend ticket volume hit, not after
4. **No repeated diagnosis** — every subsequent ticket resolved by copy-paste instruction instead of independently re-diagnosed by whichever engineer picks it up next

None of this required new tooling that didn't already exist. It required a **process** that treated "I've seen this pattern before" as an immediate trigger for documentation and escalation — not something that waits for a manager to notice ticket volume increasing.

### The Broader Pattern This Points To

This incident isn't an outlier — it's representative of the 85% baseline. Structurally, it's the identical shape of problem Devin Stein (Dosu's founder) described as his own origin story: *"You have a few experts, and many users or fewer non-experts working on a project."* Swap "codebase" for "known device compliance issue," and it's the same knowledge-imbalance problem — a small number of people hold the context, and everyone else either waits or re-derives it from scratch.

Dosu solved this for open source maintainers and codebases. Nobody has solved it well for enterprise IT service desks, where the same pattern plays out constantly, at real operational cost — real people burning real hours on-call over a weekend for an issue that was already understood a week earlier.

### Why This Entry Is Lab-Worthy

- **The pain is real and recent** — happened within two weeks of this entry
- **The root cause is structural, not technical** — the knowledge existed; the pipeline from "one engineer knows this" to "the team acts on this" didn't
- **It connects directly to the ZTIA/agentic ecosystem thinking already in this KB** — fundamentally a knowledge-grounding and pattern-recognition problem, the same category Dosu operates in for codebases
- **It's provable at small scale** — a lab build doesn't need to solve enterprise IT at AHS scale; it needs to demonstrate the mechanism: pattern detection → automatic KB draft → proactive push, in a scoped, demonstrable way

---

## Key Takeaways (Living — Updated as Entries Grow)

- **Correct diagnosis on day one can still take a week to become team-wide action** — the bottleneck is process, not knowledge
- **This is the same category of problem Dosu was founded to solve** — knowledge imbalance between a few experts and many non-experts, just in enterprise IT instead of open source
- **85% of ticket volume is repetitive** — most of it could be short-circuited by the same "grounded knowledge, surfaced proactively" mechanism Dosu applies to codebases
- **PIPR names the right workflow** — pattern recognition, immediate documentation, proactive push — the current gap is that it's manual and depends on one person's initiative rather than being built into the process

---

## Related

- See `dosu-research.md` in `company-portfolio/dosu/` for the company-level parallel (Devin Stein's founding insight)
- Ties into future lab scoping — a small-scale demonstration of pattern detection → KB generation → proactive alerting, applied to IT service desk ticket patterns
