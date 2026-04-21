# Changelog

All notable changes to Distill are documented here.
Format: [Keep a Changelog](https://keepachangelog.com) · [Semantic Versioning](https://semver.org)

---

## [3.0.0] — 2026-04-20

Complete ground-up rewrite. New architecture, new skill chain system, new reference structure.

### Added
- **Output Contracts** — every skill produces the same named sections on every run, enabling reliable Chain Memory handoffs
- **Chain Memory** — ~200-token compressed context block passed between chained skills; downstream skills build on upstream work
- **Translate skill** — plain-language conversion + format selection (doc / PDF / slides / HTML) with DESIGN.md visual styling
- **`/think` command** — single entry point: business context soft-check → frame detection → routing → chain offers after every skill
- **`references/catalog.md`** — 28 frameworks across 8 categories for Amplify 10x and Build
- **`references/business-context-template.md`** — self-contained 16-question intake; replaces external artifact dependency
- **Via Negativa (−x mode)** in Amplify — subtractive amplification: find what to remove to make everything remaining compound harder
- **Cynefin classification** as Step 0 in Reframe — Simple / Complicated / Complex / Chaotic routing before three-angle attack
- **Probability scoring** in Pressure Test pre-mortem — Likelihood × Impact tags on each failure mode; ranked before surfacing
- YAML `license`, `compatibility`, and `metadata` fields across all 8 skills per open skills standard
- Negative trigger clauses and `CRITICAL:` markers in all skill files
- Example blocks in all 8 SKILL.md files
- CONTRIBUTING.md and FUTURE_SKILLS.md
- README badges and installation section

### Changed
- Amplify extended: 2x / 10x → 2x / 10x / −x
- `business_context` instruction rephrased to accurately reflect Chain Memory architecture
- Plugin description rewritten outcome-first
- Hardcoded artifact URL in `/think` replaced with bundled template file
- `${CLAUDE_PLUGIN_ROOT}` path variable replaced with explicit Read tool instruction
- `reframe` description updated: clarified standalone invocation separate from `/think` auto-trigger

### Removed
- **Automate skill** — logic absorbed into Decide Step 6 (The Algorithm with automation classification)
- **Amplify 5x tier** — phantom middle removed; no distinct behavior from adjacent tiers
- **Plugin-managed session memory** — Claude's native auto-memory handles persistence
- **GT/bias orientation detection** — unverifiable at runtime
- **6 domain pack reference files** — consolidated to single catalog.md
- **Hardcoded artifact URL** — replaced with bundled business-context-template.md
- **`${CLAUDE_PLUGIN_ROOT}` path variable** — replaced with explicit Read instruction

---

## [2.1.0] — 2026-04-10

First packaged `.plugin` file (24.5 KB). Eight skills organized by cognitive operation — user always knows what they are trying to *do*.

**Menu skills (5):** Understand · Diagnose · Decide · Build · Amplify
**Contextual skills (3):** Reframe (auto-triggered on frame confusion) · Pressure Test (offered after Decide and Build) · Translate (terminal, offered after any skill)

`/think` router: plain-language input → frame check → Reframe or menu → skill → chain offers. Chain Memory passes context between skills in a session.

**Design principles:** Five choices in the menu. Three contextual skills activate without occupying menu space. Constraints are guilty until proven innocent. Conclusions survive attack or get rebuilt.

**Predecessor skill lineage:**

| Distill Skill | Built From |
|---|---|
| Understand | first-principles-learning-mode, first-principles-topic-mode |
| Diagnose | axiomatic-audit-mode |
| Decide | first-principles-business-mode |
| Build | musk-test-mode |
| Amplify | radical-accretive-innovation |

---

## [Pre-Distill — Standalone Skills] — 2026-03-25

Seven independent skills autoresearched with binary evals (5 runs × 6 eval dimensions = 30 points each). Results determined which improvements were kept vs. discarded before consolidation into Distill.

| Skill | Score | Outcome |
|---|---|---|
| first-principles-learning-mode | 100% | Baseline held — 3 experiments tested, all discarded |
| first-principles-topic-mode | 80% → 96.7% | Improved — strip-down classification labels added: Foundation / Inherited Thinking / Partial Truth; rebuild section must demonstrate functional difference from conventional version |
| first-principles-business-mode | 100% | Baseline held |
| musk-test-mode | 100% | Baseline held |
| feynman-mode | 96.7% | Baseline held |
| axiomatic-audit-mode | 100% | Baseline held |
| radical-accretive-innovation | 100% | Baseline held — concrete example of accretion vs. addition degraded structural compliance |

**Key carry-forward:** Foundation / Inherited Thinking / Partial Truth taxonomy from first-principles-topic-mode became the strip-down classification system used throughout Understand and Decide.
