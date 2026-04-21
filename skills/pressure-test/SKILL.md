---
name: pressure-test
description: >
  This skill should be used when the user wants to attack any conclusion, plan, or decision from
  three angles before acting on it — Dialectical Test (Steelman vs. Strawman simultaneously),
  Pre-mortem (assume failure, work backward), and Second-order consequences (assume success, find
  what breaks). Only what survives all three is worth committing to. Run after Decide, Build, or
  any skill that produces an actionable conclusion. Triggers: "pressure test this", "stress test",
  "attack this", "is this actually right", "what could go wrong", "challenge this", "poke holes",
  "devil's advocate", "what am I missing", "test this before I commit", "pre-mortem".
  Do NOT use to explore a topic or generate initial analysis — run only after Decide, Build,
  Amplify, or any skill that produces an actionable conclusion worth attacking before commitment.
license: MIT
compatibility: "Designed for Claude.ai Cowork mode. The /think command requires Cowork plugin runtime. Core skills function in Claude Code and Claude.ai."
metadata:
  author: Scott Wise
  version: 3.0.0
---

# Pressure Test

Three attacks on any conclusion, plan, or decision. Run before committing to anything that matters. Only what survives all three attacks is worth acting on.

If Chain Memory from a previous skill contains business_context, use it to ground your attacks in the user's company, market, goals, and constraints. If running standalone, ask the user to briefly describe their business context before proceeding, or check `references/business-context-template.md` if present.

If Chain Memory is present from a previous skill, read it before proceeding. This skill attacks the conclusion from prior skills, not re-derives it.

## Attack 1 — Dialectical Test

Run Steelman and Strawman simultaneously. Surface what each reveals before synthesizing.

**CRITICAL — run Steelman and Strawman separately before synthesizing.** Do not collapse them.

**Steelman:** Build the strongest possible case FOR this conclusion. Best evidence, best logic, most favorable reading of the data. What would a smart, informed defender with full information say?

**Strawman:** Find the weakest load-bearing point. Where does the reasoning thin out? Where is the argument propped up by assumption rather than evidence? What would a smart, adversarial skeptic with full information say?

Surface what each reveals separately before synthesizing. The gap between the Steelman and the Strawman is where the real risk lives.

## Attack 2 — Pre-Mortem

It is 18 months from now. This was fully executed and completely failed — not a near-miss. A clear, unambiguous failure. Working backward:

- What was the actual cause of failure?
- What early warning signals were visible but rationalized away?
- Which assumption turned out to be wrong?
- What external change made the plan obsolete?
- What did you optimize for that turned out not to matter?

For each failure mode identified, assign a probability tag:
- **Likelihood:** High (>50%) / Medium (20–50%) / Low (<20%)
- **Confidence:** How certain are you in that estimate? (High / Medium / Low)
- **Rationale:** One sentence on why you assigned that likelihood

Rank failure modes by Likelihood × Impact before surfacing. The goal is not to predict failure — it is to surface the rationalization patterns that suppress early warning signals, and to force honest probability estimates that reveal which risks are being minimized.

## Attack 3 — Second-Order Consequences

Assume full success. The plan worked exactly as designed. Now:

- **First-order:** What does success immediately change?
- **Second-order:** What does that change trigger?
- Does any second-order consequence create a problem worse than the one being solved?

Watch for:
- Success creates dependency on something you don't control
- Success attracts competition that erodes the advantage that made it work
- Success requires scaling something that doesn't scale
- Success changes incentives in a way that undermines the original goal
- Success makes the next problem harder, not easier

## What Survives

State the conclusions that held through all three attacks. For anything that crumbled: name the attack that broke it and whether the failure mode is fixable (continue with modification) or fatal (requires rethinking the underlying approach).

## Steelman

[The strongest case for this conclusion. Best evidence, best logic.]

## Strawman

[The weakest load-bearing point. Where reasoning thins. The most honest attack.]

## Pre-Mortem

[The failure scenario 18 months out. For each failure mode: cause, early signals, wrong assumption, external change. Each tagged with Likelihood (High/Medium/Low), Confidence (High/Medium/Low), and one-line rationale. Ranked by Likelihood × Impact.]

## Second-Order

[What success immediately changes. What that triggers. Whether any second-order consequence creates a worse problem.]

## What Survives

[What held through all three attacks. What crumbled, which attack broke it, and whether it's fixable or fatal.]

---

## Example

**User says:** "I've decided to productize my consulting into a $3k/month retainer with 3 deliverables. Pressure test it."

**Skill does:**
- Attack 1 (Dialectical): Steelman — productized consulting removes scope creep, creates predictable revenue, attracts clients who want clarity. Strawman — $3k retainer with 3 deliverables is just consulting with a cap; the real constraint (client dependency on your time) is unchanged
- Attack 2 (Pre-mortem): 18 months out, full failure. Cause: clients kept requesting revisions and additions beyond the 3 deliverables; the "productized" frame broke down at delivery; revenue was predictable but margin wasn't. Early signal rationalized away: first client asked for a 4th deliverable in month 2 and you said yes
- Attack 3 (Second-order): Success creates a waiting list. Waiting list creates pressure to hire. Hiring changes economics — the product that was profitable at solo scale becomes unprofitable with a team delivering it. The success case requires a systems build that wasn't in the plan
- What survives: the pricing level and recurring model. What crumbles: the deliverable-based scope definition — needs to shift to outcome-based or time-boxed to be truly productized

**Output:** Steelman, Strawman, Pre-Mortem (with failure cause and rationalized signals), Second-Order (with specific consequence chain), What Survives (fixable vs. fatal).

---

## Chain Memory (for next skill)

Compress your key findings into a structured block:

**Pressure Test found:**
- Steelman: [Core strength of the position in 1 sentence]
- Strawman: [The weakest point and where it thins]
- Pre-Mortem: [Most likely failure mode and the assumption that was wrong]
- Second-Order: [Most important consequence of success]
- What Survives: [What held and what didn't — fixable or fatal]

---

*Want to Amplify what survived? Or Translate it into something you can communicate?*
