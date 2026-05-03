# Changelog

All notable changes to Distill are documented here.
Format: [Keep a Changelog](https://keepachangelog.com) · [Semantic Versioning](https://semver.org)

---

## [3.2.0] — 2026-05-03

### Visual Layer (PRD v0.5.0)

**Added**
- `references/visual-primitives.md` — New reference file loaded by Translate when option 6 (System Map) fires. Contains 8 node types mapped to Mermaid native shapes, 5 edge types, render templates for all 9 diagram types (Flowchart, Sankey, Quadrant, Wardley, Mindmap, Timeline), DESIGN.md→themeVariables derivation rules, animation spec for Diagnose+Build chain morph, interactive side panel JS pattern, Strategic Insight Layer template, and extension instructions for domain-specific primitives.
- `skills/translate/SKILL.md` — Option 6 (System Map) in Step 3 format menu. Full System Map Render section: source-skill-to-diagram mapping, DESIGN.md theme injection, animated AS-IS→TO-BE morph (Diagnose+Build chain, ≤12 nodes), interactive node click side panel, Strategic Insight Layer (3-line block from Output Contracts). Power-user "full stack" mode (up to 4 diagram types per artifact).
- `references/DESIGN.md` — Section 10 (Mermaid Theme) added with Builder Branding Co pre-derived `themeVariables`: `primaryColor: #4B5563`, `lineColor: #0EA5E9`, `background: #050810`, `look: handDrawn`, `layout: elk`.
- `references/business-context-template.md` — Optional "What tools and systems run the business?" question added to Operations section. Populates `[SYSTEM]` nodes in Flowchart renders and component layers in Wardley Maps.

**Modified**
- `skills/translate/SKILL.md` — Step 4 style menu gains option 6 (Builder Branding Co preset). DESIGN.md generation standard updated from 9-section to 10-section (adds Mermaid Theme). Builder Branding Co preset spec included. Frontmatter description updated to mention System Map.
- `.claude-plugin/plugin.json` — Version bumped to 3.2.0.
- `.claude-plugin/marketplace.json` — Version bumped to 3.2.0.

**Architecture note:** Zero new skills. Zero new menu surfaces outside Translate. The visual layer slots entirely inside Translate's Step 5. Core 8-skill architecture unchanged.

---

## [3.1.0] — 2026-04-28

### New skill: Diverge

**Added**
- `skills/diverge/SKILL.md` — Escapes modal thinking via probability-weighted distribution scanning. Surfaces non-obvious cross-domain approaches the user's domain expertise would miss. Mandatory Confidence Audit section prevents hallucinated domain claims. Routes to Build, Decide, or Pressure Test.

**Modified**
- `skills/amplify/SKILL.md` — Step 2 now generates candidates as a probability-weighted list (0.0–1.0). Requires minimum 2 candidates below 0.10 threshold, 8 generated internally before selection. Replaces "generate at least six" heuristic with research-backed divergence mechanics. (Research basis: Zhang et al., arXiv:2510.01171, Stanford 2025.)
- `skills/reframe/SKILL.md` — Step 3 uses same probability-weighted mechanics. Minimum 2 frames required below 0.10 threshold, 6 generated internally. Replaces aspirational "genuinely different" instruction with structural escape from modal distribution.
- `commands/think.md` — Added Diverge as menu item 6, routing table trigger phrases, and chain offers after Amplify and Diverge completion.
- `README.md` — Added Diverge to skills table and Output Contracts table.
- `.claude-plugin/plugin.json` — Fixed validation schema: removed invalid `schema_version`, `commands`, and `skills` fields. Auto-discovery now handles both. Version bumped to 3.1.0.

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
