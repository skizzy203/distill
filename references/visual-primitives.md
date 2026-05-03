---
name: visual-primitives
description: >
  Visual rendering reference for Translate System Map (option 6). Node types,
  edge types, diagram templates for all 9 diagram types, DESIGN.md-to-Mermaid
  themeVariables derivation rules, Strategic Insight Layer template, and
  extension instructions for domain-specific node types.
  Loaded by Translate only when option 6 fires. Do not load otherwise.
version: "3.2.0"
---

# Visual Primitives — Distill

Loaded by Translate when the user selects option 6 (System Map). Do not load at any other time.

---

## Node Types

Eight semantic node types mapped to Mermaid native shapes. The primitive name is the **FIRST WORD** inside the node label — never used as syntax. Shape carries semantic distinction visually; Mermaid parses shape from brackets, not from label content.

| Primitive   | Mermaid syntax                     | Shape              |
|-------------|------------------------------------|--------------------|
| OFFER       | `id["OFFER: label"]`               | Rounded rectangle  |
| AVATAR      | `id(["AVATAR: label"])`            | Stadium            |
| CHANNEL     | `id[/"CHANNEL: label"/]`           | Parallelogram      |
| CONVERSION  | `id(("CONV: label"))`              | Circle             |
| DELIVERY    | `id[["DELIVERY: label"]]`          | Subroutine         |
| REVENUE     | `id[("REVENUE: label")]`           | Cylinder           |
| SYSTEM      | `id{{"SYSTEM: label"}}`            | Hexagon            |
| FRICTION    | `id{"FRICTION: label"}`            | Rhombus            |

---

## Edge Types

| Edge          | Mermaid syntax              | Meaning                       |
|---------------|-----------------------------|-------------------------------|
| Flow          | `-->`                       | Standard directional flow     |
| Value exchange| `==>`                       | High-value transfer           |
| Feedback loop | `-.->|"feedback"|`          | Recursive or reinforcing path |
| Weak link     | `-.->` (no label)           | Uncertain or thin dependency  |
| Broken path   | `--x`                       | Dead end or blocked path      |

---

## Diagram Templates

### Flowchart (AS-IS / TO-BE)

**Used for:** Diagnose (AS-IS), Build (TO-BE), Decide (decision flow), Pressure Test (survival markers), Amplify (additions overlay), Diverge (cross-domain bridges).

```
flowchart TD
  A["OFFER: label"] ==> B(["AVATAR: label"])
  B --> C[/"CHANNEL: label"/]
  C --> D(("CONV: label"))
  D ==> E[["DELIVERY: label"]]
  E --> F[("REVENUE: label")]
  G{"FRICTION: label"} -.->|"friction"| D
  H{{"SYSTEM: label"}} --> E
```

**Skill-specific modifiers:**

- **Diagnose AS-IS:** Apply `classDef friction fill:#ef4444,stroke:#dc2626,color:#fff` to all FRICTION nodes. Pulse effect: `animation: pulse 1.5s ease-in-out infinite` in CSS.
- **Build TO-BE:** Apply `classDef added fill:#10b981,stroke:#059669,color:#fff` to new nodes `[+]`, `classDef removed opacity:0.3` to removed nodes `[-]`, `classDef changed fill:#f59e0b,stroke:#d97706,color:#fff` to changed nodes `[~]`.
- **Diagnose + Build chain:** See Animation section below.
- **Pressure Test:** Append `[+]` (survives), `[!]` (at risk), or `[X]` (fails) to node labels. Style `[X]` nodes red, `[!]` nodes amber, `[+]` nodes green.
- **Amplify:** Append `[+]` to amplified or new nodes. Style with `classDef added`.
- **Diverge:** Use `-.->` edges for cross-domain bridges. Label with source domain: `-.->|"from: aerospace"|`.

---

### Sankey (Pressure Map)

**Used for:** Diagnose (energy/revenue/time leak), Diagnose+Build diff (before/after flow comparison).

```
sankey-beta
  Source,Destination,Value
  Source,Destination,Value
```

- Nodes = inputs and outputs (revenue streams, time buckets, energy channels).
- Values are relative (1–100 scale). Scale all flows proportionally.
- Leaks route to a `LOST` terminal node.
- For Diagnose+Build diff: render two Sankey charts side by side — AS-IS and TO-BE — labelled "Before" and "After".
- Pull values from Diagnose Output Contract → Waste Map (quantified losses) or estimate relative proportions from the narrative if no explicit numbers are given.

---

### Quadrant (Impact × Effort)

**Used for:** Decide (option prioritization).

```
quadrantChart
  title Impact vs Effort
  x-axis Low Effort --> High Effort
  y-axis Low Impact --> High Impact
  quadrant-1 Do First
  quadrant-2 Schedule
  quadrant-3 Delegate
  quadrant-4 Drop
  Option A: [0.2, 0.8]
  Option B: [0.7, 0.6]
```

- x/y values are 0.0–1.0. Pull coordinates from Decide Output Contract: Impact and Effort ratings.
- If ratings are qualitative (High/Medium/Low), map: High = 0.8, Medium = 0.5, Low = 0.2.

---

### Wardley Map (Strategic Positioning)

**Used for:** Build (TO-BE competitive positioning).

Mermaid has no native Wardley type. Render as LR flowchart with evolution-axis subgraphs:

```
flowchart LR
  subgraph Genesis
    A["label"]
  end
  subgraph Custom
    B["label"]
  end
  subgraph Product
    C["label"]
  end
  subgraph Commodity
    D["label"]
  end
  A --> B --> C --> D
```

- Use SYSTEM node syntax for infrastructure/tools.
- Use OFFER node syntax for value propositions.
- Label evolution stage in the subgraph header, not the node.
- Pull components from Build Output Contract → Blueprint and business-context `systems_and_tools`.

---

### Mindmap (Reframe, Understand)

**Used for:** Reframe (problem decomposition), Understand (concept map).

```
mindmap
  root((Central Concept))
    Branch 1
      Leaf A
      Leaf B
    Branch 2
      Leaf C
      Leaf D
```

- Root = the core subject or reframed problem.
- First-level branches = major themes or decomposed components.
- Leaves = specific insights, sub-concepts, or reframe options.
- Pull structure from Reframe Output Contract → Committed Frame and reframe candidates, or Understand Output Contract → Stripped Truths and Rebuilt Model.

---

### Timeline (Decide, Build — optional)

**Used for:** Implementation sequencing when phases are explicit in Output Contract.

```
timeline
  title Implementation Sequence
  Phase 1 : Step A : Step B
  Phase 2 : Step C : Step D
  Phase 3 : Step E
```

- Only render if the Output Contract contains explicit phases or a sequenced roadmap.
- Pull from Build → Smallest True Version / Blueprint phases, or Decide → Recommended Path next steps.

---

## Source-Skill to Default Diagram Mapping

| Source skill in Chain Memory         | Default diagram(s)                                          |
|--------------------------------------|-------------------------------------------------------------|
| Diagnose only                        | Flowchart (AS-IS) + Sankey (pressure map)                   |
| Build only                           | Flowchart (TO-BE) + Wardley (positioning)                   |
| Decide                               | Quadrant (Impact × Effort) + Flowchart (decision flow)      |
| Diagnose + Build chain               | Animated Flowchart (AS-IS → TO-BE morph) + Diff Sankey      |
| Reframe                              | Mindmap (problem reframing)                                 |
| Pressure Test                        | Flowchart with [+]/[!]/[X] survival markers                 |
| Amplify                              | Flowchart with [+] additions overlaid                       |
| Understand                           | Mindmap (concept decomposition)                             |
| Diverge                              | Flowchart with cross-domain bridge edges                    |

**Power-user mode** (user appends "full stack"): render all relevant types in one artifact, capped at 4 diagrams to control token cost. If more than 4 types are relevant, ask the user which 4 to include.

---

## DESIGN.md → Mermaid themeVariables Derivation

**Check first:** Does `references/DESIGN.md` contain a `## Mermaid Theme` section?

- **If yes:** Read the themeVariables directly from that section and inject as-is.
- **If no:** Derive from DESIGN.md color palette using this mapping:

| themeVariable        | Source in DESIGN.md                                     |
|----------------------|---------------------------------------------------------|
| `primaryColor`       | `colors.primary`                                        |
| `primaryTextColor`   | `colors.text-primary`                                   |
| `primaryBorderColor` | `colors.primary` darkened 20% (or `colors.border` at 10% opacity) |
| `lineColor`          | `colors.secondary`                                      |
| `secondaryColor`     | `colors.secondary` at 20% opacity                       |
| `background`         | `colors.background`                                     |
| `fontFamily`         | `typography.body-md.fontFamily`                         |
| `fontSize`           | `typography.body-md.fontSize`                           |

**Mermaid init block (inject into every System Map artifact):**

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
      fontSize: '{{fontSize}}'
    },
    look: 'handDrawn',
    layout: 'elk'
  });
</script>
```

Replace `{{tokens}}` with resolved values at render time.

---

## Animation — Diagnose + Build Chain

Activates **only** when Chain Memory contains both a Diagnose Output Contract AND a Build Output Contract.

**Node count check:** Count nodes in AS-IS state.
- ≤ 12 nodes: render animated morph (see below).
- > 12 nodes: render static side-by-side diff with [+]/[-]/[~] markers. No morph. Label clearly: "AS-IS → TO-BE diff (static — diagram too large to animate)."

**Animated morph — render instructions:**

Generate a single HTML artifact with two Mermaid diagram containers and CSS keyframe animation:

1. **Both diagrams share stable node IDs.** Nodes that exist in both states use the same ID. Nodes removed in TO-BE have `opacity: 0` in Frame 2. Nodes added in TO-BE have `opacity: 0` in Frame 1.
2. **Three-phase animation loop:**
   - Frame 1 (1s): AS-IS flowchart visible. FRICTION nodes pulsing red (`animation: pulse-red 1.5s ease-in-out infinite`).
   - Morph (1s): removed nodes fade to `opacity: 0`, added nodes fade from `opacity: 0` to `1`, changed nodes cross-fade shape.
   - Frame 2 (1s): TO-BE flowchart stable. Added nodes green.
   - Loop continuously.
3. **Hover to pause:** `.diagram-container:hover { animation-play-state: paused; }`

**CSS keyframe templates:**

```css
@keyframes pulse-red {
  0%, 100% { fill: #ef4444; opacity: 1; }
  50% { fill: #dc2626; opacity: 0.7; }
}
@keyframes fade-out {
  0% { opacity: 1; } 100% { opacity: 0; }
}
@keyframes fade-in {
  0% { opacity: 0; } 100% { opacity: 1; }
}
@keyframes morph-phase {
  0%   { opacity: 1; }  /* Frame 1: AS-IS */
  33%  { opacity: 0; }  /* Morph: transitioning */
  66%  { opacity: 1; }  /* Frame 2: TO-BE */
  100% { opacity: 1; }
}
```

---

## Interactive Side Panel

Each rendered diagram node should carry a `data-section` attribute linking to its relevant Output Contract section. After Mermaid finishes rendering, attach click handlers.

**JavaScript pattern (inject into every System Map artifact):**

```javascript
document.addEventListener('DOMContentLoaded', () => {
  // Wait for Mermaid to finish rendering
  setTimeout(() => {
    document.querySelectorAll('.node').forEach(node => {
      node.style.cursor = 'pointer';
      node.addEventListener('click', () => {
        const sectionId = node.dataset.section;
        const content = sections[sectionId];
        if (content) {
          document.querySelector('#side-panel .panel-content').innerHTML = content;
          document.querySelector('#side-panel').classList.add('open');
        }
      });
    });
    document.querySelector('#panel-close')?.addEventListener('click', () => {
      document.querySelector('#side-panel').classList.remove('open');
    });
  }, 500);
});
```

**`sections` object** — populate from Chain Memory Output Contracts at render time:

```javascript
const sections = {
  'waste-map':          `<h3>Waste Map</h3><p>{{Diagnose.WasteMap}}</p>`,
  'constraints':        `<h3>Constraints</h3><p>{{Diagnose.Constraints}}</p>`,
  'leverage-move':      `<h3>Highest-Leverage Move</h3><p>{{Diagnose.HighestLeverageMove}}</p>`,
  'blueprint':          `<h3>Blueprint</h3><p>{{Build.Blueprint}}</p>`,
  'smallest-true':      `<h3>Smallest True Version</h3><p>{{Build.SmallestTrueVersion}}</p>`,
  'recommended-path':   `<h3>Recommended Path</h3><p>{{Decide.RecommendedPath}}</p>`,
};
```

Replace `{{tokens}}` with actual Output Contract content at render time.

**Side panel HTML:**

```html
<div id="side-panel">
  <button id="panel-close">✕</button>
  <div class="panel-content"></div>
</div>
```

---

## Strategic Insight Layer

Render a structured 3-line block **below every diagram**. Source from Output Contracts — no re-derivation, no new analysis.

```
Revenue leak:       [Diagnose → Waste Map → highest-loss item]
Leverage point:     [Diagnose → Highest-Leverage Move  OR  Build → Blueprint → top action]
Removed constraint: [Diagnose → Constraints → Ghost-classified item]
```

Omit any line where the source field is absent from Chain Memory. Never fabricate.

**HTML template:**

```html
<div class="insight-layer">
  <div class="insight-row">
    <span class="insight-label">Revenue leak</span>
    <span class="insight-value">{{value}}</span>
  </div>
  <div class="insight-row">
    <span class="insight-label">Leverage point</span>
    <span class="insight-value">{{value}}</span>
  </div>
  <div class="insight-row">
    <span class="insight-label">Removed constraint</span>
    <span class="insight-value">{{value}}</span>
  </div>
</div>
```

---

## Extension Instructions (v3.2+)

To add domain-specific node types:

1. Choose a Mermaid native shape not already in the Node Types table.
2. Add a row: Primitive name | Mermaid syntax | Shape name.
3. Document the semantic meaning (what business concept it represents).
4. Add it to the relevant Diagram Template section's modifier notes.
5. Add a `classDef` entry in the CSS block of the artifact template.

**Example — PE deal sourcing domain extension:**

| Primitive | Mermaid syntax               | Shape    | Meaning                    |
|-----------|------------------------------|----------|----------------------------|
| DEAL      | `id[("DEAL: label")]`        | Cylinder | Target acquisition company |
| SPONSOR   | `id(["SPONSOR: label"])`     | Stadium  | PE firm or co-investor     |
| THESIS    | `id{"THESIS: label"}`        | Rhombus  | Investment thesis gate     |
