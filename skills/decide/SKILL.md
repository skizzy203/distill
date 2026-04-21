---
name: decide
description: >
  This skill should be used when the user needs to resolve a live problem or decision by stripping
  assumptions, interrogating every constraint for whether it is real or inherited, finding the most
  direct path, and applying The Algorithm before committing. Distinct from Reframe (which questions
  the problem frame) and Diagnose (which audits an existing system). Triggers: "solve", "decide",
  "stuck on", "what should I do", "what is the simplest way", "help me think through",
  "I cannot figure out how to", "overcomplicating", "what is the right move",
  "I need to make a decision", "should I", "which option", "what is the move".
  Do NOT use for understanding concepts (use Understand), auditing systems (use Diagnose),
  or building from scratch (use Build) — only for live decisions with real options and stakes.
license: MIT
compatibility: "Designed for Claude.ai Cowork mode. The /think command requires Cowork plugin runtime. Core skills function in Claude Code and Claude.ai."
metadata:
  author: Scott Wise
  version: 3.0.0
---

# Decide

Resolve a live problem or decision. This skill strips phantom constraints, finds the direct path, and applies The Algorithm before committing to any course of action.

If Chain Memory from a previous skill contains business_context, use it to ground your analysis in the user's company, market, goals, and constraints. If running standalone, ask the user to briefly describe their business context before proceeding, or check `references/business-context-template.md` if present.

If Chain Memory is present from a previous skill, read it before proceeding. Do not re-derive what has already been established. Build on it.

## Step 1 — Problem Statement

State the decision in one sentence. If the sentence contains "and," it's two decisions. Split them and confirm which one to solve first.

One sentence: "The decision is whether to [X] or [Y], in order to achieve [goal]."

## Step 2 — Constraint Inventory

List every constraint currently preventing or shaping this decision. Classify each:

- **Hard:** Physics, math, economic law, or legal obligation. Immutable.
- **Soft:** Organizational, contractual, social. Real, but changeable.
- **Ghost:** Assumed constraint with no actual consequence for removal. Eliminate immediately.

Remove all Ghosts before proceeding.

## Step 3 — Constraint Interrogation

For each remaining Hard and Soft constraint, ask five questions:

1. **Source** — Who told you this is a constraint? Is that source authoritative or assumed?
2. **Consequence** — What actually happens if you violate it? Is the consequence real or imagined?
3. **Precedent** — Has anyone violated this constraint successfully? Under what conditions?
4. **Duration** — Is this constraint permanent, or temporary? Does it expire?
5. **Scope** — Does this constraint apply to the goal, or only to the current method of achieving it?

A constraint that fails even one of these questions is reclassified as Soft or Ghost.

## Step 4 — Assumption Strip-Down

What are you assuming about the market, the customer, the timeline, the resources, the team, the competition?

List all load-bearing assumptions. For each, apply the **CRITICAL — Physics/Economics Floor Test:**
*"Would this assumption fail if tested against fundamental physics, math, or economic law?"*
- If it survives → keep it.
- If you cannot articulate why → treat as Inherited Thinking until proven otherwise.
Do not skip this test. Assumptions that survive scrutiny are the only ones worth building on.

## Step 5 — Direct Path

Given only what survived Steps 3 and 4: what is the most direct route from the current position to the needed outcome?

Not the safest route. Not the most familiar. Not the one that protects existing investments. The most direct.

If the direct path is blocked by a Hard constraint that survived interrogation, the decision is about how to remove or route around that constraint specifically — not about optimizing within it.

## Step 6 — The Algorithm

Apply in strict sequence. The order is non-negotiable.

**1. Make requirements less dumb.** Question every requirement. The most dangerous requirements come from smart, credentialed people — you don't question them enough because of who said them.

**2. Delete.** Remove components, steps, processes, people, meetings, approvals, tools. If you're not adding back at least 10% of what you deleted, you didn't delete enough.

**3. Simplify.** Only after deletion. Simplifying something that should be deleted makes it harder to delete later.

**4. Accelerate.** Speed up what remains. Increase iteration rate. Shorten cycle time.

**5. Automate.** Last step, never first. Classify every remaining process:
- **Automate:** Rule-based, repetitive, clear input → output. No relationship or judgment component.
- **Augment:** Complex but patternable. Human judgment remains, AI increases leverage and throughput.
- **Human-Essential:** Relationship-driven, trust-dependent, or requires irreducible creative judgment. Do not automate.

## Problem Statement

[The decision stated in one sentence.]

## Constraint Inventory

[Full list with Hard / Soft / Ghost classification. Ghosts removed. What survived and why.]

## Direct Path

[The most direct route from current position to needed outcome, given only what survived.]

## Decision Framework

[Recommended path. What you're committing to. What you're giving up. The conditions under which you would reverse this decision.]

---

The strongest argument against this decision is [X]. It survives / does not survive because [Y].

---

## Example

**User says:** "Should I raise prices 20% or add a lower-tier offer to grow volume?"

**Skill does:**
- Step 1: Detects two decisions bundled — splits into (a) pricing optimization and (b) offer architecture. Confirms which to solve first: offer architecture, because it defines the price ceiling
- Step 2: Constraint inventory — "customers won't pay more" = Ghost (assumed, untested), "we need volume to cover costs" = Soft (depends on margin structure), "can't change pricing mid-contract" = Hard (legal, for existing customers only)
- Step 3: Interrogates the "volume" assumption — source is CFO intuition, not unit economics data; consequence of removing = unclear; precedent = similar SaaS companies raised prices and reduced volume with better net revenue
- Step 4: Strips the assumption that more customers = more revenue — fails the economics floor test if LTV:CAC is inverted at lower tiers
- Step 5: Direct path = raise prices for new customers, test lower tier in a separate channel with no cross-contamination of existing positioning

**Output:** Problem Statement, Constraint Inventory with classifications, Direct Path, Decision Framework with reversal condition.

---

## Chain Memory (for next skill)

Compress your key findings into a structured block:

**Decide found:**
- Problem Statement: [The decision in one sentence]
- Constraint Inventory: [Key constraints that survived — Hard and Soft only]
- Direct Path: [The recommended route in 1-2 sentences]
- Decision Framework: [The commitment, the trade-off, and the reversal condition]

---

*Want to Pressure Test this decision before committing? Or Build the solution from zero?*
