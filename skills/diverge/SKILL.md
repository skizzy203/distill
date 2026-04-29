---
name: diverge
description: >
  This skill should be used when the user wants to escape conventional thinking and find non-obvious
  approaches — including cross-domain imports from fields that have already solved the structural
  problem. Use when stuck in industry-standard thinking, when domain expertise may be limiting
  options, or when the usual solutions are not enough. Triggers: "nobody's cracked this",
  "outside my industry", "what would [field] do", "I don't know what I don't know",
  "break the pattern", "contrarian approach", "help me think outside my field",
  "what are we missing", "cross-domain", "what would Elon do", "borrow from another industry".
version: 3.1.0
---

# Diverge

The best solution to your problem may already exist in a field you have never studied. This skill finds it. It takes any input, reduces it to its fundamental form, and generates a probability-weighted distribution of approaches — including cross-domain imports the user would not know to look for. Every domain claim is confidence-rated before it is surfaced.

If business_context is present, read it first.
If Chain Memory is present, read it before proceeding.

## Step 1 — Physics Floor

Reduce the problem to its fundamental form. Strip all domain vocabulary, industry framing, and inherited structure. Express the constraint in terms of physics, math, or economics only.

One sentence: "The fundamental problem is [X] — a system where [constraint at the floor]."

If domain vocabulary is still present, strip further. The floor statement is what you search from.

## Step 2 — Distribution Scan

Generate a probability-weighted distribution of approaches to the physics-floor problem. For each, assign a probability (0.0–1.0) representing how likely a practitioner in the user's field would recommend it.

Requirements:
- Include both within-domain and cross-domain approaches
- For cross-domain: name the source domain, the mechanism that solved this structural problem there, and what the port to the user's context requires
- Require at least 3 approaches with probability below 0.10
- Generate at least 8 internally before selecting
- Only include cross-domain claims you can characterize with high factual confidence — if uncertain, omit rather than approximate

The low-probability approaches are the target. High-probability options are what the user already knows.

## Step 3 — Surface Three

From the full distribution, surface the 3 most useful low-probability approaches. Exclude anything a practitioner in the user's field would immediately suggest.

For each:
- **The approach** — one sentence
- **Source** — within-domain, or [field name] if cross-domain
- **Why non-obvious** — what assumption has to be abandoned for this to be viable
- **Adaptation required** — what changes for this to work in context (cross-domain only)
- **Confidence** — High / Medium / Low on the factual claims embedded in this option

## Step 4 — Route

State the recommended next Distill skill and why.

- Committing to a new approach → **Build**
- Choosing between options → **Decide**
- Testing before committing → **Pressure Test**
- Frame still uncertain → **Reframe**

---

The strongest argument against this approach is [X]. It survives / does not survive because [Y].

---

## Physics Floor

[The fundamental problem stripped of domain vocabulary.]

## Non-Modal Options

[Three approaches. For each: approach, source, why non-obvious, adaptation if cross-domain, confidence.]

## Confidence Audit

Every external factual claim above — rated High / Medium / Low. For Medium: what to verify before using. For Low: what to verify and note of uncertainty. Any source that cannot be confirmed to exist: named directly.

## Route To

[Recommended next skill and reasoning.]

---

## Chain Memory (for next skill)

**Diverge found:**
- Physics Floor: [One sentence]
- Non-Modal Options: [Three options — one sentence each]
- Highest-Confidence Option: [The one most worth pursuing and why]
- Route To: [Skill and reasoning]

---

*Continue to the recommended skill, or pick any Distill skill directly.*
