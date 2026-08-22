# Visual Elements — Context Engineering

Companion file to SLIDES.md. This file governs the **second pass** of the two-pass workflow.

## How to use this file (instructions for the slide generator)

**This is an additions document, not a parallel specification.** The first pass (governed by SLIDES.md) has already produced rendered HTML slides. This file specifies visual elements — photographs, diagrammatic accents, icons — to **add** to those existing slides.

- Modify the existing HTML for each slide; do not regenerate from scratch.
- Add only what this file specifies. Slides not listed here remain unchanged.
- If a visual element here would conflict with the first-pass layout, the first-pass layout wins — flag the conflict rather than overriding it.
- Slide identifiers (`## 01-title`, `## 02-overview`, etc.) match SLIDES.md exactly. Use them as anchors.

## Global styling for diagrammatic elements

- **Line weight:** thin, uniform. No filled shapes.
- **Color:** gold accent on transparent or neutral background.
- **Level of abstraction:** geometric and minimal. No literal pictograms.
- **Scale:** small. Visual accents, not focal elements. Typography remains primary.

## Global styling for photographs

- **Source:** [describe your photo source]
- **Composition preference:** wide-frame moments showing relational context over tight portraits.
- **Treatment:** consistent color grading across the deck.
- **Rule:** one photograph per slide maximum.

---

## Per-slide additions

### 01-title

- **Photograph suggestion:** A wide-frame image of researchers working in a snowy field setting with laptops or instruments — establishes the scientific context and the "outdoor lab meets code" tension that the talk addresses.
- **Placement:** Right third of the slide, behind a semi-transparent purple overlay so text remains dominant.
- **Alternative (diagrammatic):** A thin gold geometric node-graph accent in the upper-right corner — abstract representation of "connected knowledge."

### 02-the-problem

- **Diagrammatic accent (built):** "Two minds" motif — large solid-outline circle (YOU) dense with gold dots, dashed arrow pointing to a smaller dashed-outline circle (AGENT) with only 2 faint dots. Labels below each. Positioned bottom-right, 420×300px. Communicates knowledge asymmetry at a glance.
- **Photograph option:** A researcher's desk or whiteboard covered in sticky notes, diagrams, and handwritten annotations — the messy richness of domain knowledge that can't transfer automatically. Cropped tight, desaturated with a subtle purple tint, placed as a background element behind the left circle of the SVG with low opacity (15-20%).

### 03-durability-spectrum

No additions.

### 04-today-focus

No additions.

### 05-introducing-snowex

- **Logo (built):** SnowEx logo from https://snowexsql.readthedocs.io/en/latest/_static/logo.png, 90×90px, top-left beside headline.
- **Schematic diagram (built):** SVG flow diagram showing data access pattern: "Your code" → "snowexsql" (with PointMeasurements, LayerMeasurements listed) → "SnowEx DB", with a return path labeled "→ DataFrame". Gold-highlighted border on the snowexsql box to draw attention to the package as the focal point.
- **Photograph option:** A wide-frame shot of a SnowEx field campaign — researchers at a snow pit with instruments. Would reinforce the real-world scientific context. Place as a subtle background strip across the top 20% of the slide with low opacity (10-15%) and a white gradient fade at the bottom edge.

### 06-scientific-use-case

- **Forking-path diagram (built):** Gold SVG showing a single line branching into two paths — solid gold line to the left (standard user, recommended) and dashed white line to the right (power user). Communicates "one question, two valid approaches" at a glance.
- **Path cards (built):** Two side-by-side cards with person icons. Left card has gold border and "Start here" pill badge; right card is subtler. Visual hierarchy guides the eye to the simple solution first.
- **Photograph option:** A researcher at a snow pit taking depth measurements — reinforces the real-world scientific context of the query. Place as a faint background image (10% opacity) behind the prompt block.

### 07-demo-no-context

- **Terminal window (built):** Semi-transparent dark rounded rectangle (70%×60%) centered on slide with three gold traffic-light dots in top-left. Signals "we are in the terminal" without using a black background. Applied consistently to all demo slides (08, 13, 18).
- **`$ claude` command (built):** Gold monospace text showing the command being executed.

### 08-first-result

- **Icons (built):** Three gold-stroke SVG icons — magnifying glass with code lines (reverse engineering), upward trend arrow (wrong path/complexity), clock face (time/tokens wasted). Placed at top of each observation card.

### 09-hands-on-01

- **Activity icons (built):** Three minimal SVG icons in a horizontal row — a terminal window (run prompt), two side-by-side panels with a dashed connector (compare), and a downward arrow (discuss). Gold stroke, no fill.
- **Prompt box (built):** Dark translucent box at bottom with the initial prompt in monospace — signals "copy/paste this into your terminal."

### 10-start-adding-context

No additions.

### 11-writing-tips

No additions.

### 12-demo-with-agents

- **Terminal window (built):** Same treatment as 08-demo-no-context — terminal shape with dots, `$ claude` command, orienting questions in white.

### 13-hands-on-02

No additions.

### 14-agents-summary

No additions.

### 15-introduction-skills

No additions.

### 16-skill-example

No additions.

### 17-demo-adding-skill

- **Terminal window (built):** Same treatment as 08-demo-no-context — terminal shape with dots, `$ claude` command, orienting questions in white.

### 18-hands-on-03

No additions.

### 19-context-vs-skill

No additions.

### 20-takeaways

No additions.
