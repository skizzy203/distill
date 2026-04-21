---
name: amplify
description: >
  This skill should be used when the user wants to find the highest-leverage additions that make an
  existing plan compoundingly more valuable — not just bigger, but multiplicatively better. Evaluates
  additions on accretion, innovation, velocity impact, and buildability. Ranks three additions with
  choosing criteria. Runs after any thinking skill or standalone with any plan the user brings. Two
  modes: 2x (tactical additions) and 10x (paradigm-level structural moves that load the strategy
  catalog). Default is 2x. Triggers: "what are we missing", "make this stronger",
  "what would make this 10x better", "what is the smartest addition",
  "what are we leaving on the table", "what would change everything",
  "what is the move nobody is making", "what would make this truly compelling",
  "amplify this", "compound this", "simplify this plan", "what should we cut",
  "we have too much going on", "what's the dead weight here".
  Do NOT use for editing, proofreading, or creative writing improvement — only for strategic
  plans, business systems, or structured analyses where additions need to compound existing value.
license: MIT
compatibility: "Designed for Claude.ai Cowork mode. The /think command requires Cowork plugin runtime. Core skills function in Claude Code and Claude.ai."
metadata:
  author: Scott Wise
  version: 3.0.0
---

# Amplify

A plan exists. This skill finds what makes it compoundingly more valuable — not just larger. The test is accretion: does adding this make everything already here more powerful, or does it just give you more things?

If Chain Memory from a previous skill contains business_context, use it to ground your analysis in the user's company, market, goals, and constraints. If running standalone, ask the user to briefly describe their business context before proceeding, or check `references/business-context-template.md` if present.

If Chain Memory is present from a previous skill, read it before proceeding. Do not re-derive what has already been established. Build on it.

## Mode Selection

**2x (Tactical) — Default**
Additions to the current plan. What is the single highest-leverage move that makes everything already here more valuable?

**10x (Paradigm)**
Game-changing structural moves. Load `references/catalog.md` using the Read tool for full framework access. Challenge the shape of the plan, not just its contents. Evaluate against enterprise value impact where relevant.

**−x (Via Negativa)**
Subtractive amplification. What can be *removed* from this plan that makes everything remaining more valuable? The accretion test runs in reverse: an element that, when removed, increases the compound value of what stays is the highest-leverage cut. Apply ruthlessly — complexity, dependencies, steps, and revenue streams that exist by inertia rather than necessity. Do not add anything in −x mode. The output is a ranked removal list, not an addition list.

If the user doesn't specify a level, default to 2x. Escalate to 10x when explicitly requested or when the ceiling is structural. Suggest −x when the plan feels heavy, overcomplicated, or when the user says "we have too much going on" or "simplify this."

## Step 1 — State What Exists

Confirm the current plan in 2-3 sentences. State the ceiling: if this plan were executed perfectly as designed, what is the maximum outcome?

Name the ceiling explicitly. This is what Amplify is designed to raise.

## Step 2 — Generate Candidates

**CRITICAL — generate at least six additions internally before surfacing any.** The first three are always obvious — the value lives past that. Do not shortcut to three. Search across five dimensions:

- **Leverage** — Makes existing assets produce more output without additional input
- **Compounding** — Gets more valuable over time, not just at the point of addition
- **Moat** — Makes the plan harder to replicate after the addition is in place
- **Asymmetric** — Disproportionate upside relative to cost or effort
- **Velocity** — Increases the rate of improvement cycles (compounds across all future iterations, not just this one)

For 10x mode: also load `references/catalog.md` using the Read tool and evaluate against enterprise value frameworks (Brand-as-Moat Six Levers, Revenue Architecture, Seven Powers, etc.).

## Step 3 — Filter for Accretion

Test each candidate: "If I added this, would existing elements become more valuable — or would I just have more elements?"

Discard everything additive. Keep only what compounds. An addition that makes the plan 20% bigger is not the same as one that makes the existing 100% worth 3x more.

## Step 4 — Rank

Rank surviving candidates by:
1. **Magnitude of compounding** — How much does it multiply the existing plan?
2. **Durability** — Is it a one-time boost or does it compound continuously?
3. **Buildability** — What does it actually take to implement?
4. **Cost of being wrong** — If it doesn't work, what breaks?

## Step 5 — Present Three

For each of the top three:
- **The move** — One sentence stating exactly what it is
- **Why accrective** — How it makes existing elements more valuable (not just bigger)
- **What it unlocks** — What becomes possible after this is in place
- **What it costs** — Time, money, attention, or trade-offs

## Step 6 — Choosing Frame

2-3 sentences on how to choose between the three additions. What does the choice reveal about what the user is actually optimizing for?

## Current Ceiling

[The plan as it exists and its maximum outcome if executed perfectly.]

## Additions

[Three ranked additions. For each: the move, why accrective, what it unlocks, what it costs.]

## Choosing Frame

[How to choose between them. What the choice reveals.]

---

The strongest argument against this amplification is [X]. It survives / does not survive because [Y].

---

## Example

**User says:** "We've built a solid content strategy — blog, newsletter, LinkedIn. What are we missing?"

**Skill does (2x mode):**
- Step 1: Current ceiling — if executed perfectly, this strategy builds an audience and generates inbound leads, but doesn't compound. Each piece of content is additive, not multiplicative
- Step 2: Generates 6+ candidates internally before surfacing: SEO clustering, repurposing, paid amplification, community, referral loop, proprietary research, co-authorship, content licensing...
- Step 3: Filters for accretion — paid amplification just adds distribution (additive, discard); SEO clustering makes existing content rank better (accrective, keep); proprietary research makes all future content more citable and authoritative (accrective, keep); community makes the audience an asset that amplifies every future piece (accrective, keep)
- Step 4: Ranks by compounding — community > proprietary research > SEO clustering
- Step 5: Presents three with move, why accrective, what it unlocks, what it costs

**Output:** Current Ceiling, three ranked Additions with full assessment, Choosing Frame.

---

## Chain Memory (for next skill)

Compress your key findings into a structured block:

**Amplify found:**
- Current Ceiling: [The plan's maximum outcome before amplification]
- Additions: [The three ranked moves — one sentence each]
- Choosing Frame: [The deciding factor between them]

---

*Want to Pressure Test the amplified plan? Or Translate it into a deliverable?*
