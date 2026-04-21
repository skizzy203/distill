# Future Skills & Roadmap

Planned enhancements for Distill 3.x. Items here are confirmed direction — not speculation.
If you want to contribute an item from this list, read CONTRIBUTING.md first.

---

## Shipped in v3.0.0

These were planned for v3.1 and shipped early as part of the v3.0.0 rewrite.

**Amplify — Via Negativa (−x mode):** Third Amplify mode. Subtractive amplification — find what to remove to make everything remaining compound harder. Trigger phrases: "simplify this," "what should we cut," "too much going on," "what's the dead weight."

**Reframe — Cynefin Classification (Step 0):** Problem-type classification before the Three-Angle Attack. Simple / Complicated → Decide or Diagnose. Complex → Understand first. Chaotic → Build.

**Pressure Test — Probability Scoring:** Each Pre-Mortem failure mode now tagged with Likelihood (High/Medium/Low), Confidence, and one-line rationale. Ranked by Likelihood × Impact before surfacing.

---

## Planned for v3.1

Nothing confirmed yet. If you have a proposal that meets the criteria in CONTRIBUTING.md, open an issue.

---

## Under Consideration (Not Yet Confirmed)

These are patterns that have come up in usage but haven't been scoped for the chain yet.

**Synthesize** — A skill for combining outputs from multiple separate chains into a unified
recommendation. Useful when you've run Understand + Diagnose + Build in separate sessions and
want to integrate the findings. Currently users do this manually. High value but complex Output
Contract definition needed.

**Map** — A visual output skill (HTML/Mermaid) that takes Chain Memory from any skill and
generates a visual representation: constraint maps, assumption trees, decision trees. Would
chain after any analytical skill, before Translate. Currently Translate handles some of this
but not in structured visual form.

---

## Explicitly Out of Scope

These won't be added to Distill core, regardless of quality:

- **Domain-specific packs** (PE, Brand, Legal, etc.) — the catalog.md reference handles domain
  depth without fragmenting the skill chain. Domain packs belong in separate plugins that
  reference Distill's chain, not in Distill itself.

- **Standalone frameworks as individual skills** (OODA, Cynefin as a skill, Bayesian reasoning,
  etc.) — Distill is a reasoning system, not a framework library. These belong in a separate
  "thinking frameworks" plugin (see cc-thinking-skills for the pattern).

- **Output-only skills** (Report, Deck, Dashboard, etc.) — Translate already handles formatted
  output. Additional output skills would fragment the terminal step without adding chain value.

- **Data or research skills** — Distill operates on business logic and reasoning, not data
  retrieval or research synthesis. Use the data: or enterprise-search: plugins for those.
