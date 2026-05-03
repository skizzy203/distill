---
name: translate
description: >
  Convert any analysis or output to plain language for non-expert audiences, or
  package it into a formatted deliverable. Format options: plain text, document,
  PDF, slides, HTML, System Map (themed Mermaid diagrams in an HTML artifact).
  Loads references/DESIGN.md automatically if present. Terminal skill — nothing
  chains after it.
when_to_use: >
  Use when the user says: "explain simply", "no jargon", "like I am 12", "ELI5",
  "make it accessible", "plain language", "non-expert audience", "break it down
  for", "how do I explain this to", "turn this into a document", "create a
  deliverable", "format this", "make a PDF", "build slides", "package this". Do
  NOT generate new analysis — only converts existing output.
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
6. **System Map** — Themed Mermaid diagrams in an HTML artifact

---

If the user selects plain text (1): deliver the converted output now. Skip Steps 4-5.

If the user selects System Map (6): proceed to Step 4 for style selection, then execute the **System Map Render** section instead of the standard Step 5. If the user appended "full stack" to their request, activate power-user mode (all relevant diagram types, capped at 4).

## Step 4 — Style Selection

If the user selects any formatted option (2-6):

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
6. **Builder Branding Co** — Glassmorphism dark, sky-400 accents

Or grab a pre-built DESIGN.md from:
→ github.com/VoltAgent/awesome-design-md (66+ brand-inspired themes)
→ neuform.ai (generate custom themes with AI)

Drop any DESIGN.md into references/ and I'll use it automatically next time.

---

**If user picks 1-4:** Generate a DESIGN.md following the Neuform 10-section standard and save it to `references/DESIGN.md`. It will be used automatically in future sessions.

**If user picks 5 (Custom):** Ask for one sentence: "Describe your brand in terms of colors, fonts, and feel." Generate DESIGN.md from that description. Save to `references/DESIGN.md`.

**If user picks 6 (Builder Branding Co):** Generate DESIGN.md using the Builder Branding Co preset: dark glassmorphism system, `#050810` background, `#0EA5E9` sky-400 secondary, glass surfaces (`rgba(10,15,26,0.8)` + 1px white border + 24px blur), 8px spacing rhythm, system fonts, Solar icons. Include pre-derived Mermaid themeVariables in Section 10 (see below). Save to `references/DESIGN.md`.

**If user provides a DESIGN.md file:** Use it directly. Save to `references/DESIGN.md`.

**Neuform 10-section standard for generated DESIGN.md:**
1. Visual Theme & Atmosphere
2. Color Palette & Roles (hex values + semantic roles)
3. Typography Rules (families, size hierarchy, weights)
4. Component Styles (tables, callouts, code, bullets)
5. Layout Principles (spacing, margins, content width)
6. Depth & Elevation (shadows for HTML, borders for docs)
7. Do's and Don'ts
8. Responsive Behavior (for HTML: breakpoints, mobile)
9. Agent Prompt Guide (quick-reference values for copy-paste use)
10. Mermaid Theme (pre-derived `themeVariables` for System Map renders)

**Section 10 format:**

```
## Mermaid Theme

primaryColor: <hex from Color Palette primary>
primaryTextColor: <hex from Color Palette text-primary>
primaryBorderColor: <hex from Color Palette primary, darkened 20%>
lineColor: <hex from Color Palette secondary>
secondaryColor: <hex from Color Palette secondary at 20% opacity>
background: <hex from Color Palette background>
fontFamily: <font family from Typography>
fontSize: 14px
look: handDrawn
layout: elk
```

Always include Section 10 whenever generating or saving a DESIGN.md.

## Step 5 — Generate Formatted Output

Apply the DESIGN.md to generate the formatted deliverable. Map the Output Contract sections from the prior skill(s) to the appropriate headings, slide titles, or document structure.

For HTML: generate a single self-contained file with embedded CSS.
For docs/PDFs: use the color palette, typography, and component styles.
For slides: one major section per slide, key findings as bullets, visual hierarchy from the DESIGN.md.

**If option 6 (System Map) was selected:** skip the prose deliverable. Execute the **System Map Render** section below instead.

No Output Contract. No Chain Memory closing block. Translate is terminal.

---

## System Map Render

Execute this section only when the user selected option 6 (System Map) in Step 3.

### 1. Load visual-primitives.md

Read `references/visual-primitives.md` now. Do not proceed without it. If the file is missing, inform the user: "visual-primitives.md not found in references/. Please ensure Distill 3.2.0 is fully installed."

### 2. Detect source skill and select diagrams

Scan Chain Memory for Output Contract sections. Identify which skill(s) ran:

- Diagnose contract present (no Build): → Flowchart (AS-IS) + Sankey
- Build contract present (no Diagnose): → Flowchart (TO-BE) + Wardley
- Both Diagnose + Build contracts: → Animated morph Flowchart + Diff Sankey
- Decide contract: → Quadrant + Flowchart (decision flow)
- Reframe contract: → Mindmap
- Pressure Test contract: → Flowchart with [+]/[!]/[X] markers
- Amplify contract: → Flowchart with [+] overlay
- Understand contract: → Mindmap
- Diverge contract: → Flowchart with cross-domain bridge edges

**Power-user mode** (user said "full stack"): render all applicable types up to 4. If more than 4 apply, list the options and ask which 4 to render.

### 3. Read DESIGN.md themeVariables

Open `references/DESIGN.md`. Read the `## Mermaid Theme` section (Section 10) to get themeVariables. If Section 10 is absent, derive values from the color palette using the derivation rules in visual-primitives.md.

Resolve all `{{token}}` placeholders before writing the HTML artifact.

### 4. Translate Output Contract content to diagram nodes

Map each Output Contract section to diagram elements using the node/edge vocabulary in visual-primitives.md. Rules:

- Use exact quotes from the Output Contract for node labels where possible (abbreviated to 3–6 words for readability).
- Apply the primitive name as the first word in every node label (OFFER, AVATAR, FRICTION, etc.).
- Assign `data-section` attributes to nodes pointing to the relevant Output Contract section key (e.g., `data-section="waste-map"`).
- SYSTEM nodes: populate from `business_context.systems_and_tools` if present in Chain Memory.
- Do not fabricate nodes. If content is thin, render fewer nodes rather than inventing them.

### 5. Animated morph check (Diagnose + Build chain only)

Count nodes in AS-IS state:
- ≤ 12 nodes → render animated morph (see visual-primitives.md Animation section).
- > 12 nodes → render static side-by-side diff. Label: "AS-IS → TO-BE (static diff — too large to animate)."

### 6. Build the HTML artifact

Generate a single self-contained HTML file. Structure:

```
<head>
  - DESIGN.md CSS variables
  - Mermaid init script (pinned to v11)
  - Diagram-specific CSS (classDef colors, animation keyframes if morph)
  - Side panel CSS
  - Insight Layer CSS
</head>
<body>
  - Header: title + subtitle from Output Contract
  - Diagram container(s): one per diagram type selected
  - Side panel: hidden by default, revealed on node click
  - Strategic Insight Layer: 3-line block below last diagram
  - Interactive JS: node click handlers, side panel open/close
</body>
```

**CSS foundations (derive from DESIGN.md):**

```css
:root {
  --bg: {{colors.background}};
  --surface: rgba(10,15,26,0.8);
  --border: rgba(255,255,255,0.08);
  --text-primary: {{colors.text-primary}};
  --accent: {{colors.secondary}};
  --radius: 20px;
  --blur: 24px;
}

body {
  background: var(--bg);
  color: var(--text-primary);
  font-family: {{fontFamily}};
  margin: 0;
  padding: 32px;
  min-height: 100vh;
}

.diagram-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 32px;
  backdrop-filter: blur(var(--blur));
  margin-bottom: 24px;
}

.diagram-title {
  font-size: 13px;
  font-weight: 600;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--accent);
  margin-bottom: 20px;
}

#side-panel {
  position: fixed;
  top: 0; right: -400px;
  width: 380px;
  height: 100vh;
  background: var(--surface);
  border-left: 1px solid var(--border);
  backdrop-filter: blur(var(--blur));
  padding: 32px;
  transition: right 0.3s ease;
  overflow-y: auto;
  z-index: 100;
}

#side-panel.open { right: 0; }

#panel-close {
  position: absolute;
  top: 16px; right: 16px;
  background: none;
  border: none;
  color: var(--text-primary);
  font-size: 18px;
  cursor: pointer;
  opacity: 0.6;
}

#panel-close:hover { opacity: 1; }

.insight-layer {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 24px 32px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.insight-row {
  display: flex;
  gap: 16px;
  align-items: baseline;
}

.insight-label {
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--accent);
  min-width: 160px;
  flex-shrink: 0;
}

.insight-value {
  font-size: 14px;
  color: var(--text-primary);
  opacity: 0.85;
}
```

**Mermaid init script:**

```html
<script type="module">
  import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@11/dist/mermaid.esm.min.mjs';
  mermaid.initialize({
    startOnLoad: true,
    theme: 'base',
    themeVariables: {
      primaryColor: '{{primaryColor}}',
      primaryTextColor: '{{primaryTextColor}}',
      primaryBorderColor: '{{primaryBorderColor}}',
      lineColor: '{{lineColor}}',
      secondaryColor: '{{secondaryColor}}',
      background: '{{background}}',
      fontFamily: '{{fontFamily}}',
      fontSize: '14px'
    },
    look: 'handDrawn',
    layout: 'elk'
  });
</script>
```

**Interactive JS (node click handlers + side panel):**

```html
<script>
  document.addEventListener('DOMContentLoaded', () => {
    const sections = { /* populate from Output Contract at render time */ };

    setTimeout(() => {
      document.querySelectorAll('.node').forEach(node => {
        const sectionId = node.dataset.section;
        if (sectionId && sections[sectionId]) {
          node.style.cursor = 'pointer';
          node.addEventListener('click', () => {
            document.querySelector('#side-panel .panel-content').innerHTML = sections[sectionId];
            document.querySelector('#side-panel').classList.add('open');
          });
        }
      });
      document.querySelector('#panel-close')?.addEventListener('click', () => {
        document.querySelector('#side-panel').classList.remove('open');
      });
    }, 600);
  });
</script>
```

### 7. Populate the Strategic Insight Layer

Pull these three values from Chain Memory Output Contracts. Omit any line where the source field is absent. Never fabricate.

- **Revenue leak:** Diagnose → Waste Map → highest-loss item (single phrase or figure).
- **Leverage point:** Diagnose → Highest-Leverage Move, or Build → Blueprint → first action.
- **Removed constraint:** Diagnose → Constraints → the Ghost-classified item (the one that turned out to be an assumption, not a real constraint).

### 8. Deliver

Output the completed HTML artifact inline. Do not produce a prose summary alongside it — the visual is the deliverable. Optionally append one sentence: "Open in browser for best rendering. Hover on nodes to pause animation. Click any node to see the linked analysis."

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
