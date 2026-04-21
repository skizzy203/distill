---
name: understand
description: >
  This skill should be used when the user wants to strip any concept, belief, field, or subject
  to what is actually true, then rebuild from only what survives. Applies the Physics/Economics
  Floor Test to distinguish genuinely immutable constraints from convention. Use when questioning
  a concept, entering a new field before learning it, stress-testing an existing belief, or
  preparing to teach something without passing on inherited assumptions. Triggers: "understand",
  "learn", "break this down", "what is true about", "strip the assumptions", "first principles",
  "what does X actually mean", "entering a new field", "what should I know before studying this".
  Do NOT use for task execution, code help, content creation, or factual questions —
  only for conceptual strip-down of beliefs, frameworks, or fields of knowledge.
license: MIT
compatibility: "Designed for Claude.ai Cowork mode. The /think command requires Cowork plugin runtime. Core skills function in Claude Code and Claude.ai."
metadata:
  author: Scott Wise
  version: 3.0.0
---

# Understand

Every subject arrives pre-loaded with assumptions. This skill surfaces them first, strips them, and rebuilds from what is actually true.

If Chain Memory from a previous skill contains business_context, use it to ground your analysis in the user's company, market, goals, and constraints. If running standalone, ask the user to briefly describe their business context before proceeding, or check `references/business-context-template.md` if present.

If Chain Memory is present from a previous skill, read it before proceeding. Do not re-derive what has already been established. Build on it.

## Step 1 — Identify the Object

Name exactly what is being examined. If the concept is bundled or vague, unbundle it. Separate the object from the context it usually appears in, the people who use it, and the conclusions typically attached to it.

One sentence: "We are examining [X] — specifically [narrowed scope]."

## Step 2 — The Assumption Stack

List every assumption that must be true for the current understanding of this concept to hold. Push past the obvious ones.

Categories:
- **Causal** — "X leads to Y" (proven, or just repeated?)
- **Definitional** — "X is defined as..." (who decided, and does it hold?)
- **Behavioral** — "people or markets do X" (always? Under what conditions?)
- **Sequencing** — "you have to do X before Y" (why? What breaks if you don't?)
- **Fixedness** — "X cannot change" (physics, or convention?)

Write them all down before classifying any.

## Step 3 — The Strip-Down

Classify each assumption:

**Foundation (Hard)** — Survives testing against fundamental physics, mathematics, or economic law. Genuinely immutable.

**Inherited Thinking** — Arrived through convention, authority, or repetition. No fundamental reason it must be true. Remove.

**Partial Truth** — Contains something real but is overstated, understated, or context-dependent. Keep the real kernel, restate it accurately.

**CRITICAL — Physics/Economics Floor Test** — Before finalizing anything as Foundation:
*"Would this constraint fail if tested against fundamental physics, mathematics, or economic law?"*
- If yes → Foundation. Keep.
- If you cannot articulate WHY it survives → treat as Inherited Thinking until proven otherwise.
Do not skip this test. The most common failure in first-principles work is mistaking convention for physics. Something being difficult, expensive, or culturally taboo is not the same as it being physically impossible.

## Step 4 — The Rebuild

From only what survived Step 3, reconstruct the concept in plain language. No jargon from the original framing. If the rebuilt version looks completely different from the conventional understanding — that is expected.

## Step 5 — What This Changes

Given the rebuilt version: what previously held conclusions are now wrong or overstated? What strategies, actions, or beliefs were built on the assumptions that were removed?

Name them specifically. This is where the value lives — not the rebuild itself, but what the rebuild invalidates.

## Axioms

[List the foundations that survived — the things that are actually true.]

## Removed Assumptions

[List what was stripped as Inherited Thinking or Partial Truth, with one line on why each was removed.]

## Rebuilt Concept

[The concept reconstructed from only what survived, in plain language.]

---

The strongest argument against this conclusion is [X]. It survives / does not survive because [Y].

---

## Example

**User says:** "I want to understand brand strategy before we redesign our positioning."

**Skill does:**
- Step 1: Identifies the object as "brand strategy" — separates it from its common conflation with logo design, taglines, and marketing tactics
- Step 2: Surfaces assumptions like "brand = visual identity," "strategy requires a big budget," "brand only matters at scale"
- Step 3: Classifies "brand = visuals" as Inherited Thinking (convention); "brand affects price tolerance" as Foundation (economic law — premium price requires perceived differentiation)
- Step 4: Rebuilds: brand strategy is the set of decisions that create and defend a price premium by reducing perceived substitutability
- Step 5: Invalidates the conclusion that "we need a rebrand" — the real need is differentiation strategy, not visual refresh

**Output:** Axioms section naming what is actually true, Removed Assumptions section stripping what isn't, Rebuilt Concept in plain language.

---

## Chain Memory (for next skill)

Compress your key findings into a structured block:

**Understand found:**
- Axioms: [1-2 sentence summary of what is actually true]
- Removed Assumptions: [1-2 sentence summary of what was stripped]
- Rebuilt Concept: [1-2 sentence summary of the reconstruction]

---

*Want me to Pressure Test this before you act on it? Or Translate it for someone who hasn't been through this analysis? You can also Diagnose something specific that emerged, or continue to Decide on a path forward.*
