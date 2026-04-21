# Distill 3.0

![Version](https://img.shields.io/badge/version-3.0.0-blue) ![License](https://img.shields.io/badge/license-MIT-green) ![Skills](https://img.shields.io/badge/skills-8-purple) ![Platform](https://img.shields.io/badge/platform-Claude%20Cowork-orange)

**Distill turns complex problems into clear decisions.**

Strip inherited assumptions, find the direct path, and attack your conclusions before you commit — using a chain of composable first-principles thinking skills. Start with `/think`.

---

## Installation

1. Download or clone this repository
2. Open Claude.ai → **Settings → Capabilities → Skills**
3. Click **Upload skill** and select the `distill/` folder (zip it first if required)
4. Enable the Distill plugin toggle
5. Start a new conversation and run `/think`

**Cowork users:** Install via the plugin directory or load the `.plugin` file directly.

---

## Quick Start

Run `/think` and describe what you're working on. The `/think` entry point will identify the right skill and guide you through the analysis. You can also invoke any skill by name directly.

For best results: paste your business context when prompted. Open `references/business-context-template.md`, fill in the questions, and paste the result into `/think`. Every skill uses this context to ground its analysis in your specific company, market, and goals.

---

## The Skills

### Menu Skills — You Select

| Skill | What It Does | When to Use |
|-------|-------------|-------------|
| **Understand** | Strip a concept to what is actually true, then rebuild | Questioning a belief, entering a new field, stress-testing understanding |
| **Diagnose** | Find what is broken, wasteful, or constrained | Auditing systems, offers, processes, operations |
| **Decide** | Resolve a live problem using The Algorithm | Choosing between options, stuck, finding the direct path |
| **Build** | Construct from zero with no inherited constraints | Starting from scratch, redesigning, contrarian architecture |
| **Amplify** | Find what compounds or what to cut (2x / 10x / −x) | A plan exists. Make it more valuable, not just bigger — or find what to remove. |

### Contextual Skills — System Offers at the Right Moment

| Skill | Trigger | Purpose |
|-------|---------|---------|
| **Pressure Test** | After Decide, Build, or any commitment point | Three-angle attack before acting |
| **Translate** | After any skill completes | Plain-language conversion + format selection (doc / PDF / slides / HTML) + visual styling |
| **Reframe** | `/think` detects frame confusion, or invoke directly | Questions whether the right problem is being solved before analysis begins |

---

## How Skills Chain

Skills pass structured context to each other — each downstream skill builds on upstream work instead of starting over.

**Common paths:**

- `Understand → Diagnose → Decide → Translate` — Full analysis chain for a complex business problem
- `Diagnose → Translate` — Fast audit with deliverable
- `Build → Amplify 10x → Pressure Test → Translate` — Complete product/strategy design cycle
- `Decide → Pressure Test → Translate` — Decision with adversarial check and output

After every skill, `/think` offers the most relevant next steps. You can also jump directly to any skill by name.

---

## Output Contracts

Every skill produces the same named sections every time. Chain Memory depends on this.

| Skill | Output Sections |
|-------|----------------|
| Understand | `## Axioms` · `## Removed Assumptions` · `## Rebuilt Concept` |
| Diagnose | `## Constraints` · `## Waste Map` · `## Highest-Leverage Move` |
| Decide | `## Problem Statement` · `## Constraint Inventory` · `## Direct Path` · `## Decision Framework` |
| Build | `## Zero State` · `## Contrarian Vision` · `## Blueprint` · `## Smallest True Version` |
| Amplify | `## Current Ceiling` · `## Additions` · `## Choosing Frame` |
| Pressure Test | `## Steelman` · `## Strawman` · `## Pre-Mortem` · `## Second-Order` · `## What Survives` |
| Reframe | `## Current Frame` · `## Alternative Frames` · `## Committed Frame` · `## Route To` |
| Translate | Adapts to selected format — no fixed contract |

---

## Visual Styling with DESIGN.md

When you run **Translate** and select a formatted output (doc, PDF, slides, or HTML), you'll be offered styling options:

1. **Minimal** — Clean white, system fonts, maximum whitespace
2. **Corporate** — Navy/gray palette, serif headings, structured and formal
3. **Bold** — High-contrast, strong color accents, modern sans-serif
4. **Editorial** — Warm tones, editorial typography, magazine-feel
5. **Custom** — Describe your brand in one sentence

Once you choose a style, a `references/DESIGN.md` file is generated and saved. Every future Translate session uses it automatically without asking again.

### Pre-Built Themes

You can also drop any pre-built DESIGN.md into the `references/` folder:

- **[awesome-design-md](https://github.com/VoltAgent/awesome-design-md)** — 66+ brand-inspired themes (Claude, Stripe, Tesla, Linear, and more)
- **[neuform.ai](https://neuform.ai)** — Generate custom themes with AI, export as DESIGN.md

Drop any DESIGN.md into `references/` and Translate will use it automatically.

---

## Business Context

The plugin works best when it knows your business. Open `references/business-context-template.md`, fill in the questions, and paste the result into `/think` when starting a session.

Context includes: company description, market, target customer, current stage, goals, and constraints. It travels through every skill in a chain as ambient context — grounding constraint classification, assumption testing, and solution design.

Once loaded, `/think` saves context to memory and uses it silently in future sessions without asking again.

---

## Contribution

Add strategy frameworks to `references/catalog.md` via PR. Five lines per framework, format:

```
- **Name:** [1-line description]. Key insight: [the non-obvious thing this framework reveals].
```

No separate files. No duplicates. Frameworks used by Amplify 10x and Build are prioritized.

---

## License

MIT — Scott Wise
