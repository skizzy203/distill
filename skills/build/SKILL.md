---
name: build
description: >
  This skill should be used when the user wants to construct any business, system, offer, or
  strategy from scratch using only fundamental truths — no industry conventions, no inherited
  approaches. Validates every constraint before accepting it and inverts the assumptions that
  produce velocity and compounding advantage. Distinct from Decide (which resolves what to do) —
  Build constructs the actual thing from zero. Triggers: "start from scratch", "rebuild",
  "if we built this today", "contrarian version", "from zero", "ignore how it is done",
  "redesign", "what would you make", "build this from first principles",
  "what would shock the industry", "no legacy constraints".
  Do NOT use if a system exists and needs improvement (use Diagnose) or a decision needs
  making (use Decide) — Build is strictly for zero-to-one construction with no legacy constraints.
license: MIT
compatibility: "Designed for Claude.ai Cowork mode. The /think command requires Cowork plugin runtime. Core skills function in Claude Code and Claude.ai."
metadata:
  author: Scott Wise
  version: 3.0.0
---

# Build

Construct from scratch using only fundamental truths. Every convention is a suspect. Every inherited structure is a question. Build only what is necessary to solve the real problem — nothing more.

If Chain Memory from a previous skill contains business_context, use it to ground your analysis in the user's company, market, goals, and constraints. If running standalone, ask the user to briefly describe their business context before proceeding, or check `references/business-context-template.md` if present.

If Chain Memory is present from a previous skill, read it before proceeding. Do not re-derive what has already been established. Build on it.

## Step 1 — Zero State

Describe the world without this thing. What need exists in its absence? What is the simplest possible response to that need?

No features. No structure. No inherited vocabulary. Just the need and the most minimal intervention that addresses it.

One sentence: "The need is [X]. The minimal true response is [Y]."

## Step 2 — Contrarian Vision

What would this look like if every convention in the space were wrong?

Not incrementally different — structurally different. What would practitioners in this field find genuinely shocking? Build the case for the contrarian version before discarding it.

Conventions worth interrogating: how it's priced, who it serves, how it's delivered, how it makes money, how it grows, what it optimizes for.

## Step 3 — Eliminations

Apply ruthlessly: if you're not adding back at least 10% of what you cut, you didn't cut enough.

What can be removed entirely from the conventional version?
- Features that exist because of inertia, not need
- Steps that exist to manage risk created by earlier steps (remove the earlier steps instead)
- Costs that exist to maintain complexity you built
- Roles that exist to manage coordination friction
- Revenue streams that create customer misalignment

## Step 4 — Inversions

Test five structural inversions:

- **Revenue inversion:** What if the business model were the opposite of the category standard? (e.g., subscription instead of transactional, or free-to-pay instead of pay-to-access)
- **Delivery inversion:** What if the delivery mechanism were reversed? (e.g., the customer does what the provider typically does, or vice versa)
- **Audience inversion:** What if you served the opposite customer? (e.g., the person the category ignores, or the customer's customer)
- **Pricing inversion:** What if the pricing structure were inverted? (e.g., pay on outcome instead of on input)
- **Velocity inversion:** What if you optimized for speed of iteration instead of quality of output? (Good enough, shipped fast, iterated to great)

For each: "If this were true, what would the business actually look like?"

## Step 5 — Blueprint

From what survived eliminations and inversions, design the full system.

Include:
- **Structure** — How it's organized and why
- **Economics** — Unit economics, revenue model, margin architecture
- **Defensibility** — What makes this hard to replicate (moat type: switching costs, network effects, brand, process, cornered resource)
- **Scaling Architecture** — How does this grow 10x without breaking? What has to change vs. what stays the same?

## Step 6 — Smallest True Version

What is the minimum version that tests the core thesis?

Not MVP as "stripped-down product." Not a prototype. The smallest thing that proves whether the fundamental insight is correct. If the thesis survives, build the rest. If it doesn't, you spent the minimum to find out.

One sentence: "The core thesis is [X]. We can test it by [Y] in [timeframe] for [cost]."

## Zero State

[The need in its rawest form. The minimal true response.]

## Contrarian Vision

[What this looks like if every convention is wrong. The shocking version.]

## Blueprint

[Full system: structure, economics, defensibility, scaling architecture.]

## Smallest True Version

[The minimum that tests whether the fundamental insight is correct.]

---

The strongest argument against this design is [X]. It survives / does not survive because [Y].

---

## Example

**User says:** "If you were building a business coaching offer from scratch today, what would it look like?"

**Skill does:**
- Step 1: Zero state — the need is a decision-maker who is stuck and needs to move faster with more confidence. Minimal response: access to a better thinking partner on demand
- Step 2: Contrarian vision — every convention says: monthly retainer, long discovery phase, deliverable-based engagement, coach as expert. Contrarian: async, outcome-specific, no retainer, priced per decision not per month
- Step 3: Eliminates: intake forms, monthly check-ins, PDF deliverables, strategy decks, "onboarding" — all exist to justify time billing, not to produce outcomes
- Step 4: Inversions tested — pricing inversion (pay on outcome = misaligned incentives, rejected); delivery inversion (client runs the session, coach asks questions = valid, keep); audience inversion (serve operators not founders = interesting but scope-creep)
- Step 5: Blueprint — async decision coaching: submit a decision, get a structured first-principles analysis back within 24 hours, one revision round, done. No retainer, priced per engagement at $500-2k depending on stakes
- Step 6: Smallest true version — run 5 paid engagements with existing contacts at $500 each, measure whether clients make the decision faster and with more confidence than before

**Output:** Zero State, Contrarian Vision, Blueprint with economics and defensibility, Smallest True Version with thesis test.

---

## Chain Memory (for next skill)

Compress your key findings into a structured block:

**Build found:**
- Zero State: [The core need and minimal true response]
- Contrarian Vision: [The structural departure from convention]
- Blueprint: [Key design decisions — structure, economics, defensibility]
- Smallest True Version: [The thesis and how to test it]

---

*Want to Amplify this to find what compounds it? Or Pressure Test before committing?*
