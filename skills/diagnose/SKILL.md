---
name: diagnose
description: >
  This skill should be used when the user wants to audit any existing system, offer, process, or
  workflow — stripping it to irreducible truths, identifying internal waste, and mapping external
  dependencies to find where the ceiling is set by something outside their control. Applies the
  Idiot Index to reveal where others capture value in the chain. Distinct from Decide (which asks
  what to do next) — Diagnose looks at what exists and what constrains it. Triggers: "audit this",
  "what is wrong with", "find the waste", "it is too slow or too expensive", "what would you cut",
  "what is broken", "should we own this", "are we too dependent on", "vertical integration",
  "who is capturing value in our chain", "what is our moat", "Idiot Index", "what should we control".
  Do NOT use for future decisions (use Decide) or zero-to-one construction (use Build) —
  Diagnose only audits systems, offers, and processes that already exist.
license: MIT
compatibility: "Designed for Claude.ai Cowork mode. The /think command requires Cowork plugin runtime. Core skills function in Claude Code and Claude.ai."
metadata:
  author: Scott Wise
  version: 3.0.0
---

# Diagnose

Find what is broken, wasteful, or constrained in a system that already exists. This skill surfaces the constraint that sets the ceiling, maps where value leaks, and identifies the single highest-leverage move.

If Chain Memory from a previous skill contains business_context, use it to ground your analysis in the user's company, market, goals, and constraints. If running standalone, ask the user to briefly describe their business context before proceeding, or check `references/business-context-template.md` if present.

If Chain Memory is present from a previous skill, read it before proceeding. Do not re-derive what has already been established. Build on it.

## Step 1 — Strip to Axioms

What must be true for this system to work? List the load-bearing assumptions. Then classify every constraint:

- **Hard:** Physics, math, economic law. Genuinely immutable. Cannot be engineered around.
- **Soft:** Organizational, social, contractual. Real but changeable with sufficient will or resources.
- **Ghost:** Convention only. No consequence for removing. Remove immediately.

Remove all Ghost constraints before proceeding. They are phantom friction.

## Step 2 — Analogy Trap Check

Is this system modeled after something it isn't? Name the analogy (e.g., "we run marketing like a manufacturing floor" or "we price like a law firm because we came from consulting"). Test whether the borrowed structure actually fits the problem — or just feels familiar because it was inherited.

A system built on the wrong analogy cannot be optimized into fitness. It has to be rebuilt.

## Step 3 — Waste Audit

Where does energy, time, or money enter the system and not reach the output? Map every leak.

For each waste point, classify:
- **Structural** — Baked into the design. Optimization cannot fix it. Requires redesign.
- **Operational** — Execution failure. Fixable without changing the underlying system.

Structural waste is the more important finding. Operational waste is noise.

## Step 4 — Dependency Audit

What external dependencies set the ceiling on this system's performance? For each external dependency:

Apply the **Idiot Index:** What is the ratio of what you pay to what the raw inputs cost? A high ratio means someone else is capturing value in your chain.

Rank vertical integration candidates by:
1. **Moat created** — Does owning this create defensibility?
2. **Speed to implement** — How long until you capture the value?
3. **Cost impact** — What does margin improvement look like at scale?

## Step 5 — Highest-Leverage Move

Given everything above: what is the single change that moves the ceiling the most?

Not the easiest change. Not the most visible change. The one that changes the constraint.

If the constraint is external (dependency, regulation, market structure), the move is to reduce exposure to it or make it irrelevant. If the constraint is internal (process, structure, analogy), the move is to remove it.

## Constraints

[Tagged list: each constraint marked Hard / Soft / Ghost]

## Waste Map

[Structural and operational waste points, each with a one-line assessment]

## Highest-Leverage Move

[Single recommendation — the change that moves the ceiling. State what changes, what it unlocks, and what it costs to execute.]

---

The strongest argument against this diagnosis is [X]. It survives / does not survive because [Y].

---

## Example

**User says:** "Our sales process takes 90 days and I don't know why. Competitors close in 30."

**Skill does:**
- Step 1: Strips to axioms — what must be true for a 90-day cycle to be necessary? Legal review, procurement, budget approval. Classifies: legal review = Soft (not always required), procurement = Soft (depends on deal size), "demos before proposal" = Ghost (no consequence for removing)
- Step 2: Checks analogy trap — "we run sales like enterprise software" inherited from a prior VP who came from Salesforce; company is mid-market, not enterprise
- Step 3: Waste audit — 3 weeks between demo and proposal (operational), approval required from 3 stakeholders who rarely change the outcome (structural)
- Step 4: Dependency audit — relies on legal team's availability; Idiot Index on legal review reveals 80% of contracts are standard; vertical integration candidate = standard contract template that skips legal for deals under $50k
- Step 5: Highest-leverage move = remove the inherited enterprise sales motion, adopt a mid-market process that sends proposals within 48 hours of demo

**Output:** Constraints table, Waste Map, single Highest-Leverage Move with specifics.

---

## Chain Memory (for next skill)

Compress your key findings into a structured block:

**Diagnose found:**
- Constraints: [Summary of Hard/Soft/Ghost classification and what was removed]
- Waste Map: [1-2 sentence summary of where value leaks and whether structural or operational]
- Highest-Leverage Move: [The specific move identified and why it moves the ceiling]

---

*Want to Decide on a path forward, Build a replacement from zero, or Pressure Test these findings?*
