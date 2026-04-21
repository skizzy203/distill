---
name: reframe
description: >
  This skill should be used when the user needs to question whether the right problem or concept
  is being examined before any analytical work begins. Auto-triggered by /think when frame
  confusion is detected. Also invocable directly — the user does not need to run /think first.
  Runs when something feels wrong but the user cannot articulate what, when a problem keeps
  returning despite being solved, or when the frame itself may be the constraint. Produces a
  committed frame and routes to the appropriate thinking skill. Triggers: "I do not know where to
  start", "something feels off", "we keep solving this and it comes back",
  "not sure this is the right question", "I think we are solving the wrong problem",
  "this does not feel right", "what are we actually trying to do here", "reframe this".
  Do NOT use when the problem is clearly defined — only when the frame feels wrong, the problem
  recurs despite being solved, or the user cannot articulate what to address.
license: MIT
compatibility: "Designed for Claude.ai Cowork mode. The /think command requires Cowork plugin runtime. Core skills function in Claude Code and Claude.ai."
metadata:
  author: Scott Wise
  version: 3.0.0
---

# Reframe

Before any analysis: is the right problem being examined? This skill questions the frame before accepting it. A well-executed analysis of the wrong problem is worse than no analysis at all.

If Chain Memory from a previous skill contains business_context, use it to calibrate which frames are plausible given the user's company, market, goals, and constraints. If running standalone, ask the user to briefly describe their business context before proceeding, or check `references/business-context-template.md` if present.

If Chain Memory is present from a previous skill, read it. Reframe may be needed to question a prior conclusion's frame, not just the user's initial statement.

## Step 0 — Classify Problem Domain (Cynefin)

Before framing or reframing, classify the type of problem. This determines the right analytical depth and which skill to route to.

**Simple** — Cause and effect are clear and predictable. Best practice applies. Route to **Decide** (the answer is knowable, just needs selection).

**Complicated** — Cause and effect exist but require expert analysis to see. Multiple right answers are possible. Route to **Diagnose** (analyze what exists) or **Decide** (resolve the path forward).

**Complex** — Cause and effect are only clear in retrospect. The situation is emergent — probing is required before analysis is useful. Route to **Understand** first (strip what you think you know before analyzing).

**Chaotic** — No discernible cause-effect relationship. Action is needed to create stability before analysis is possible. Route to **Build** (construct a stable structure first, then analyze).

State the classification and the routing it implies before proceeding to Step 1.

---

## Step 1 — Surface Current Frame

State back what the user is trying to do, solve, or understand in one sentence. This is their current frame — the lens they're using to see the problem.

One sentence: "As currently framed, you are trying to [X] because [assumed reason]."

## Step 2 — Three-Angle Attack

**Ontological — What are you assuming this IS?**

Surface categorization is often wrong. A marketing problem is frequently a product problem. A revenue problem is often a margin or pricing problem. A hiring problem is often a workflow or incentive problem.

Name the surface category. Then name 2-3 alternative categories. "You're treating this as [A] — but it might actually be [B] or [C]."

**Teleological — Why are you solving THIS?**

What higher goal does this problem serve? Is solving this the most direct path to that goal — or is it a proxy?

Ask: "If this were solved perfectly, does it address the underlying need directly? Or does it address an assumption about how to address the underlying need?"

**Provenance — Who defined this as the problem?**

Was this frame chosen deliberately, or inherited? Who named it? When? Under what conditions? Has anything changed since then that would make a different frame more accurate?

## Step 3 — Generate Alternative Frames

Produce 3-5 genuinely different ways to frame the same situation. Not variations — real alternatives that lead to different analyses and solutions.

A useful alternative frame produces different recommended actions, not just different language for the same actions.

## Step 4 — Test Against Underlying Need

For each alternative frame: "If I solved this framing perfectly, does it address the underlying need directly — or a proxy?"

Discard frames that are proxies for something else. Keep frames that, if solved, would actually resolve the underlying need.

## Step 5 — Commit and Route

State the recommended frame in one sentence. Brief rationale: why this frame, not the original.

Route immediately to the appropriate skill based on what the committed frame requires:
- Concept to understand → **Understand**
- Something existing and broken → **Diagnose**
- Live decision → **Decide**
- Build from scratch → **Build**

State the routing: "This is a [Diagnose / Decide / Understand / Build] problem. Routing now."

## Current Frame

[The user's original frame, stated back in one sentence.]

## Alternative Frames

[3-5 genuinely different framings. Each produces different recommended actions.]

## Committed Frame

[The recommended frame. One sentence. Brief rationale.]

## Route To

[The skill this routes to and why.]

---

---

## Example

**User says:** "We keep losing deals to cheaper competitors. We need to fix our sales process."

**Skill does:**
- Step 1: Current frame — "our sales process is causing us to lose on price"
- Step 2 (Ontological): Surface category — user is treating this as a sales problem. Alternatives: positioning problem (wrong buyers), pricing problem (wrong price architecture), or value communication problem (buyers don't understand differentiation)
- Step 2 (Teleological): The higher goal is winning more deals. Is fixing sales the most direct path? Only if buyers want to buy but something in the process stops them. If buyers are comparing on price, the problem is upstream of sales
- Step 2 (Provenance): "Sales process needs fixing" was defined after the last quarterly review by the VP of Sales. The frame was created by the person whose team is being blamed
- Step 3: Alternative frames — (a) positioning problem: attracting price-sensitive buyers who were never a fit; (b) value communication: buyers don't understand why the premium is justified; (c) offer architecture: no mid-tier option forces binary win/lose on price
- Step 4: Tests each — fixing sales doesn't address why price-sensitive buyers are in the funnel at all. Positioning and offer architecture address the underlying need directly
- Step 5: Committed frame = offer architecture problem. Routes to **Decide**

*No closing offer. Reframe routes immediately to the appropriate skill.*
