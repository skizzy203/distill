# Contributing to Distill

Distill is open source under the MIT license. Contributions are welcome — but the bar is high.
Every addition must compound the system. Read this before opening a PR.

---

## What Distill Is (and Isn't)

Distill is a **chained reasoning system**, not a framework library. The 8 skills work together
through Output Contracts and Chain Memory. Adding a new skill that works well in isolation but
doesn't chain with the others is not a contribution — it's noise.

The test for any new skill or change: **does this make the existing system more valuable, or does
it just give the system more things?** If it's the latter, it belongs in a different plugin.

---

## How to Contribute

### Adding frameworks to `references/catalog.md`

This is the most common and most welcome contribution. The catalog is the reference library
for Amplify 10x and Build — the richer it is, the more powerful those skills become.

**Format (exactly 5 lines per framework):**

```
- **Framework Name:** One-line description of what the framework is and does.
  Key insight: [the non-obvious thing this framework reveals — the thing practitioners miss].
```

**Requirements:**
- The key insight must be the *non-obvious* version, not a summary of the framework
- No duplicates — search the catalog before adding
- Frameworks must be applicable to business strategy, offer design, brand, operations, or enterprise value
- Pure academic frameworks with no business application don't belong here

**Current categories (add to existing ones; don't create new categories without discussion):**
Enterprise Value · Scaling · Brand Strategy · Competitive Analysis · Negotiation · Systems & Leverage · Psychology & Behavior · Decision-Making

---

### Modifying existing skills

**Before changing a SKILL.md:**
- Understand how that skill's Output Contract feeds downstream skills
- Changing output section names breaks Chain Memory — this requires updating all downstream skills simultaneously
- Test changes against the example in the skill's `## Example` section

**What's in scope:**
- Improving step specificity or clarity
- Fixing over/under-triggering in the description
- Adding edge case handling
- Improving the Example block

**What's out of scope:**
- Changing output section names (breaking change — requires full chain audit)
- Adding new steps that bloat token usage beyond what the chain can sustain
- Changing the skill's core methodology (open an issue and discuss first)

---

### Proposing new skills

New skills must meet all four criteria:

1. **Chains with existing skills** — has a clear place in the chain and passes/receives Chain Memory
2. **Fills a genuine gap** — addresses something the 8 existing skills cannot do, not a variation of an existing skill
3. **Serves general business use** — not developer-specific, not domain-specific, works across industries
4. **Passes the accretion test** — its presence makes existing skills more valuable, not just more numerous

Before building: open an issue with the proposed skill name, its Output Contract, and which existing skills it would chain with. Get a response before writing the SKILL.md.

---

### YAML frontmatter requirements

All skills must follow the Anthropic open skills standard:

```yaml
---
name: skill-name
description: >
  [What it does] + [When to use it] + [Specific trigger phrases].
  Do NOT use for [exclusions] — [scope boundary].
license: MIT
compatibility: "Designed for Claude.ai Cowork mode. The /think command requires Cowork plugin runtime. Core skills function in Claude Code and Claude.ai."
metadata:
  author: [Your Name]
  version: [x.x.x]
---
```

- Description must be under 1,024 characters
- Must include at least 5 trigger phrases
- Must include at least one "Do NOT use for..." exclusion clause
- No XML angle brackets in description
- kebab-case skill folder name, must match `name` field

---

## Pull Request Process

1. Fork the repo, create a feature branch
2. Make your changes
3. Test against the example scenario in the affected skill(s)
4. Update CHANGELOG.md under a `[Unreleased]` heading
5. Open a PR with: what changed, why, and what it does to the chain

PRs that don't update the CHANGELOG won't be merged.

---

## What We're Looking For (See FUTURE_SKILLS.md)

Check `FUTURE_SKILLS.md` for enhancements that are on the roadmap. PRs that implement
roadmap items are prioritized.

---

MIT License · Scott Wise
