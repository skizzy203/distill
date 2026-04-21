---
name: translate
description: >
  This skill should be used when the user wants to convert any analysis or output to plain language
  for non-expert audiences, or package it into a formatted deliverable. Offers format selection
  (plain text, document, PDF, slides, HTML) and visual styling (4 presets, custom, or external
  DESIGN.md file). Loads references/DESIGN.md automatically if present. Generates and saves
  DESIGN.md for future sessions. Terminal skill — nothing chains after it. Consumes other skills'
  output contracts. Triggers: "explain simply", "no jargon", "like I am 12", "ELI5",
  "make it accessible", "plain language", "non-expert audience", "break it down for",
  "how do I explain this to", "turn this into a document", "create a deliverable",
  "format this", "make a PDF", "build slides", "package this".
  Do NOT generate new analysis — Translate only converts existing analysis (from a prior skill
  or provided by the user) into plain language or a formatted deliverable.
license: MIT
compatibility: "Designed for Claude.ai Cowork mode. The /think command requires Cowork plugin runtime. Core skills function in Claude Code and Claude.ai."
metadata:
  author: Scott Wise
  version: 3.0.0
---

# Translate

Two jobs: (1) make the analysis understandable to someone who wasn't in the room, and (2) package it into a format they can use. This is the terminal skill — nothing chains after it.

If Chain Memory from a previous skill contains business_context, use it to calibrate tone and audience framing. If running standalone, check `references/business-context-template.md` if present.

If Chain Memory is present from a previous skill, read it. Translate consumes other skills' output — it does not generate its own analysis.

## Step 1 — Identify the Audience

Who will read this? What do they already know? What do they need to walk away with?

Name the audience specifically: "This is for [role/person], who [knows X], and needs to [do/decide/understand Y]."

If no audience is specified, ask: "Who will read this — a client, a team, an investor, an executive, or someone else?"

## Step 2 — Convert to Plain Language

Rewrite using only language the audience already has. No jargon. No assumed context. No shorthand from the analysis.

If a concept resists simplification: surface the exact point where the complexity lives and ask the user how to proceed. ("This concept has a part that's genuinely hard to simplify without losing accuracy — want me to use an analogy, or keep the technical term with a brief definition?")

Test: could a smart 12-year-old follow this? If not, simplify further.

## Step 3 — Format Selection

After conversion, offer packaging options:

---

How would you like this packaged?

1. **Plain text** — Conversation output as-is
2. **Document (.docx)** — Structured document, headings mapped to analysis sections
3. **PDF** — Same structure, PDF format
4. **Slides (.pptx)** — Key findings, one section per slide
5. **HTML** — Single-file interactive artifact, shareable without tools

---

If the user selects plain text (1): deliver the converted output now. Skip Steps 4-5.

## Step 4 — Style Selection

If the user selects any formatted option (2-5):

**Check first:** Does `references/DESIGN.md` already exist in the plugin directory?
- **If yes:** "You have a saved style. Use it, or pick a new one?"
- **If no:** Present the style menu below.

---

Pick a visual style for your output:

1. **Minimal** — Clean white, system fonts, maximum whitespace
2. **Corporate** — Navy/gray palette, serif headings, structured and formal
3. **Bold** — High-contrast, strong color accents, modern sans-serif
4. **Editorial** — Warm tones, editorial typography, magazine-feel
5. **Custom** — Describe your brand colors, fonts, and vibe in one sentence

Or grab a pre-built DESIGN.md from:
→ github.com/VoltAgent/awesome-design-md (66+ brand-inspired themes)
→ neuform.ai (generate custom themes with AI)

Drop any DESIGN.md into references/ and I'll use it automatically next time.

---

**If user picks 1-4:** Generate a DESIGN.md following the Neuform 9-section standard and save it to `references/DESIGN.md`. It will be used automatically in future sessions.

**If user picks 5 (Custom):** Ask for one sentence: "Describe your brand in terms of colors, fonts, and feel." Generate DESIGN.md from that description. Save to `references/DESIGN.md`.

**If user provides a DESIGN.md file:** Use it directly. Save to `references/DESIGN.md`.

**Neuform 9-section standard for generated DESIGN.md:**
1. Visual Theme & Atmosphere
2. Color Palette & Roles (hex values + semantic roles)
3. Typography Rules (families, size hierarchy, weights)
4. Component Styles (tables, callouts, code, bullets)
5. Layout Principles (spacing, margins, content width)
6. Depth & Elevation (shadows for HTML, borders for docs)
7. Do's and Don'ts
8. Responsive Behavior (for HTML: breakpoints, mobile)
9. Agent Prompt Guide (quick-reference values for copy-paste use)

## Step 5 — Generate Formatted Output

Apply the DESIGN.md to generate the formatted deliverable. Map the Output Contract sections from the prior skill(s) to the appropriate headings, slide titles, or document structure.

For HTML: generate a single self-contained file with embedded CSS.
For docs/PDFs: use the color palette, typography, and component styles.
For slides: one major section per slide, key findings as bullets, visual hierarchy from the DESIGN.md.

No Output Contract. No Chain Memory closing block. Translate is terminal.

---

## Example

**User says (after Decide skill):** "Turn this into a one-pager for my business partner who wasn't in this conversation."

**Skill does:**
- Step 1: Audience = business partner, knows the business but not the analysis; needs to understand the decision and why it was made
- Step 2: Converts Chain Memory from Decide into plain language — removes "constraint inventory," "ghost constraints," "Physics Floor Test" language; replaces with "we tested whether this was a real limitation or just an assumption"
- Step 3: Format selection offered — user picks Document (.docx)
- Step 4: No existing DESIGN.md found; presents style menu; user picks Corporate
- Step 5: Generates DESIGN.md (navy/gray, serif headings), saves to references/DESIGN.md, produces .docx with: Problem → What We Tested → What We Decided → Why → What We're Watching For

**Output:** Plain-language .docx with the decision framed for a non-participant reader, DESIGN.md saved for future sessions.
