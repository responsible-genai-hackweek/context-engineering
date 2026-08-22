# Context Engineering

A 60-minute tutorial on making project context durable for AI coding agents — so they remember your conventions, vocabulary, and structure across sessions.

Target audience: Researchers and developers using AI coding agents on scientific codebases
Duration: 60 minutes (slides + live demos interleaved)

## How to render this deck (instructions for the slide generator)

**This document is a design brief, not slide copy.**

**Two-pass workflow.** This deck is built in two passes, and SLIDES.md governs only the first.

- **First pass (this file): content and structure only.** Build the deck to a publishable-looking, intentional state using only typography, layout, color palette, and the gold accent. Use no photographs and no decorative icons in this pass. The deck should look complete on its own — if it had to be presented tomorrow with no images, it should feel finished rather than naked.
- **Second pass (separate VISUALS.md): additive visual elements.** After the first pass is rendered and rehearsed, VISUALS.md specifies photographs, diagrammatic accents, and iconography to _add_ to existing slides. The second pass modifies the already-rendered HTML; it does not rebuild slides from scratch.
- **Do not anticipate the second pass during the first.** If a slide feels visually sparse, the correct response is stronger typography or layout, not a placeholder.

**General rules:**

- The **Key message** line is the slide's headline — often the only substantial text shown, set in large type.
- **Bullets** are talking points the speaker will deliver aloud. Do not render them verbatim on the slide.
- **Note to self** lines are for the speaker only. Never render them on the slide.
- **Source** lines render as a small footer citation — never as a content bullet.
- Default to one anchoring element per slide: a phrase, a number, or a small structural composition. When in doubt, less text.
- Maintain visual continuity: consistent type scale, generous whitespace, and the gold accent from the title slide.

**CSS Pattern Reference:** All slide patterns (layout, colors, typography, spacing) are defined in `shared/slide-patterns.css`. This is a **recipe book** — not a linked stylesheet. When building a slide:

1. Read the pattern file to find the matching pattern (e.g. "A1. DEMO SLIDE", "B1. CARD GRID")
2. Copy the CSS into the slide's inline `<style>` block
3. Replace the generic class name (e.g. `.demo-slide`) with `.slide-XX`
4. Follow the HTML structure documented in the pattern's comment block
5. Do NOT use shared CSS classes from `styles.css` — they lose specificity battles

**Background color signals mode:**

- White = content (absorb/read) — patterns B1–B6
- Purple gradient = activity (do something) — patterns A1–A4
- Gold (#ffc700) is NEVER used as text on white backgrounds (fails WCAG AA). On white: gold for borders/accents only; text emphasis = purple. On purple: gold text is fine.

**Live demo slides:** Use pattern **A1 (demo-slide)** from `shared/slide-patterns.css`. Slides marked `[LIVE DEMO]` are holding-screen placeholders shown while the instructor works in a terminal.

**Hands-on slides:** Use pattern **A2 (handson-slide)** or **A3 (handson-slide full)** from `shared/slide-patterns.css`. Activity slides where learners do the work.

**Transition slides:** Use pattern **A4 (transition-slide)** for topic pivots between sections.

---

## 01-title

Title slide with UW branding.

- Layout: purple gradient background, gold top bar, gold bottom-left accent bar (40% width). Left-aligned, vertically centered.
- Title: "Context Engineering for AI Coding Agents" — extra-large display weight. "Context Engineering" in gold.
- Subtitle: "Making your project knowledge durable" — light weight, muted.
- Presenter names: Anthony Arendt, Joachim Meyer — names in bold white, affiliations in muted gray.
- Affiliation: University of Washington / eScience Institute, Boise State University.
- Date: "August 2026" — small gold uppercase.
- Decorative element: abstract gold node-graph SVG in upper-right corner, low opacity. Geometric circles connected by thin lines.

## 02-the-problem

- Key message: "Your agent does not remember most of your project context"
- Layout: white background, gold top bar. Headline full-width, then two-column grid below (slightly wider right column for the SVG visual).
- Left column: four point cards stacked vertically. Each card has an icon in a purple-tinted rounded square, a bold title, and a one-line description.
- Points (order):
  1. "Blind to your project" — Doesn't know your data, conventions, or goals (info circle icon)
  2. "Resets every session" — No memory carries over — starts fresh each time (radial lines icon)
  3. "Fills gaps confidently" — Good at reverse engineering — and eager to guess wrong (warning triangle icon)
  4. "Durability is up to you" — You decide what persists — the agent won't do it for you (shield icon)
- Right column: "Two minds" SVG diagram — large solid circle (YOU) dense with purple dots, dashed gold arrow pointing to a smaller dashed circle (AGENT) with only 2 faint dots and "? ?" text. Labels below each circle. Communicates knowledge asymmetry at a glance.

## 03-durability-spectrum

- Key message: "Persistent context options in current landscape"
- Subhead (rendered): "Agents are building 'memory' features, but durability is still largely in your hands."
- Layout: white background, gold top bar. Four equal cards in a horizontal grid, full width. Below the cards, a gradient axis line (gold → gray) with labels.
- Each card: gold top border, gradient purple-tinted background, vertical stack of label/description/example.
- Cards (left to right):
  1. **Always loaded** — Context documents read every time, regardless of task. Example: `AGENTS.md`
  2. **Invoked on match** — Skills and named procedures loaded when a task fits. Example: `Skills`
  3. **Auto-triggered** — Rules and path-scoped constraints that fire on specific files. Example: `Rules`
  4. **Delegated** — Subagents and specialized personas summoned for expertise. Example: `Subagents`
- Axis line: gradient bar (gold on left, gray on right) spanning full width.
- Axis labels: "Always present" on the left, "On demand" on the right. Small condensed uppercase gold text.

## 04-today-focus

- Key message: "Today: Two options on the spectrum"
- Layout: white background, gold top bar. Left-aligned headline, then two focus cards side by side, then two ghost cards below.
- Headline: large display. "Two options" has gold underline accent.
- Focus cards: two equal cards side by side, gold top border, purple-tinted background, rounded. Each contains a large number, bold label, and description.
- Card 1: "1" — "Context document `AGENTS.md`" — "Always-on, loaded every session — the foundation of what your agent knows"
- Card 2: "2" — "Skill" — "On-demand, invoked when the task matches — a recipe reached for only when needed"
- Ghost cards: two equal cards below, dashed border, gray top border (not gold), very subtle background. Signal "more exists but not today."
  - Each has a "Not covered today" badge (small pill), a label, and short description.
- Ghost 1: Rules — "Auto-triggered on specific files"
- Ghost 2: Subagents — "Delegated specialized personas"
- Note to self: These cover most researchers' needs. The others are refinements you'll reach for as projects grow.

## 05-introducing-snowex

- Key message: "snowexsql — A Python library for the SnowEx database"
- Layout: white background, gold top bar. Headline with code-styled package name. Two-column grid below: summary points on left, SVG schematic on right.
- Logo: SnowEx logo image positioned top-right, large (fills corner area), slight transparency. Source: <https://snowexsql.readthedocs.io/en/latest/_static/logo.png>
- Left column: four summary items with gold left-border accent. Each has bold lead text and description.
  - NASA SnowEx campaigns — multi-year field and airborne snow measurements across western US and Alaska
  - PostgreSQL/PostGIS database — snow depths, density, temperature, stratigraphy, SWE
  - Python package — query via a Lambda client (no credentials) or direct DB connection
  - Returns DataFrames — filters by campaign, date, type, location
- Right column: SVG flow diagram showing data access pattern:
  - Boxes: "Your code" → "snowexsql" (gold-highlighted border, with PointMeasurements/LayerMeasurements listed) → "SnowEx DB" cylinder
  - Return path: dashed line back labeled "→ DataFrame" in gold
- Callout at bottom: gold left-border. "Clone the forked repo: github.com/jomey/snowexsql — Hint: Agents cheat!"

## 06-scientific-use-case

- Key message: "Scientific use case: Querying snow depth layer data"
- Layout: white background. Centered layout with three vertical sections.
- Top: headline in small uppercase purple, centered.
- Prompt block: monospace text in a bordered rounded box, centered, generous width. Contains:
  - "Create me a code block that queries the database and returns snow depth layer data for a snow pit and date during the Alaska campaign"
- Middle: forking-path SVG diagram — single dot branching into two paths (gold solid left, purple dashed right).
- Bottom: two side-by-side path cards.
  - Left card (recommended): gold border, gold top accent, "Start here" badge, person icon. "Standard user" — simple high-level API query.
  - Right card: subtle border, no badge. "Power user" — advanced joins and raw SQL.
- Footer note: "This question has multiple valid answers — we guide the agent to recommend the simple solution first." — centered, muted.

## 07-demo-no-context

[LIVE DEMO]

- Pattern: A1 (demo-slide) from `shared/slide-patterns.css`
- Badge: "LIVE DEMO"
- Title: "Repository with no context"
- Command: `$ claude`
- Description: "Running the snow depth query prompt against a bare repository — no AGENTS.md, no skills."
- Watch-for box: "What does the agent do when it has no guidance? Where does it guess?"

## 08-first-result

- Key message: "Confident, fast, and complicated"
- Layout: white background, gold top bar. Large headline, then three equal cards in a horizontal grid.
- Each card: gold top border, purple-tinted background, rounded. Contains an SVG icon (large, gold stroke), bold label, and description.
- Cards (order: what it did → why it's wrong → what it cost):
  1. **Reverse engineered** (magnifying glass icon) — dove into source code instead of using documented patterns
  2. **Chose the complex path** (upward trend arrow icon) — suggested advanced solution when README shows simpler as preferred
  3. **Burned tokens guessing** (clock icon) — spent effort guessing query parameters it could have been told

## 09-hands-on-01

- Pattern: A2 (handson-slide) from `shared/slide-patterns.css`, plus additional elements.
- Badge: "YOUR TURN"
- Headline: "Run the prompt, then compare with a partner"
- Activity row: three-step visual inside a subtle bordered container. Each step has a large SVG icon (gold strokes) and a label, connected by gold arrow characters:
  1. Terminal window icon → "Run prompt"
  2. Two side-by-side panels with dashed connector → "Compare outputs"
  3. Two overlapping circles → "Discuss"
- Prompt box: dark translucent background, gold border, left-aligned, generous width. Label "Paste this prompt into your terminal" in small gold uppercase. Monospace text in white:
  - "Create me a code block that queries the database and returns snow depth layer data for a snow pit and date during the Alaska campaign"
- Discuss box: "How different are the outputs? Did you get the same solution?"

## 10-start-adding-context

- Key message: "How to guide the LLM with context?"
- Layout: white background (no gold top bar). Two-column grid: content on left, document visual on right.
- Headline: two-line — question + answer ("Add a central context document").
- Quote block: gold left-border blockquote, large italic text.
  - "Think of AGENTS.md as a README for agents: a dedicated, predictable place to provide the context and instructions to help AI coding agents"
- Adoption note: "An open standard — supported by Copilot, Codex, Cursor, Claude Code, and many more. Used in 60k+ open-source projects."
- Source link: "Further reading: agents.md" → <https://agents.md> — purple text with gold underline.
- Right column: stylized document card visual representing AGENTS.md:
  - Purple gradient header with gold file icon and "AGENTS.md" filename in monospace
  - Body with abstract content lines (rounded bars, varying widths) grouped in sections with gold bullet dots
  - Card has soft shadow and rounded corners
- Note: does NOT list what goes in it (that's slide 14) or writing tips (slide 11).

## 11-writing-tips

- Key message: "A good AGENTS.md is concise and actionable" (gold underline on "concise and actionable")
- Layout: white background, gold top bar. Headline with highlighted phrase, then 2×3 grid of tip cards.
- Each tip card: icon in purple-tinted rounded square + bold title + description. Cards have subtle purple border and background.
- Card order (pedagogical — strongest first, advanced last):
  1. Be specific — Not "follow best practices" → `Run lint after every change`
  2. Start simple — Begin with a few lines, expand as you learn
  3. Keep it short — Under 200 lines or 32 KiB
  4. It's a guide, not enforcement — No guarantee "DO NOT EDIT" is honored
  5. Nest for big repos — Subdirectory files override root, closest wins
  6. Public repos: models may learn from it — Keep secrets out

## 12-demo-with-agents

[LIVE DEMO]

- Pattern: A1 (demo-slide) from `shared/slide-patterns.css`
- Badge: "LIVE DEMO"
- Title: "Re-run with AGENTS.md"
- Command: `$ claude`
- Description: "Same prompt, same repo — but now with an AGENTS.md guiding the agent."
- Watch-for box: "Does it pick the right connection type? Does it still guess at filter options?"

## 13-hands-on-02

- Pattern: A2 (handson-slide) from `shared/slide-patterns.css`
- Badge: "YOUR TURN"
- Headline: "Compare again — what changed?"
- Instructions (bordered container, centered, gold arrow markers):
  - "How different are the outputs from each other?"
  - "How do they compare to the first attempt?"
- Discuss box: "Did the AGENTS.md make a difference? What improved? What still needs work?"

## 14-agents-summary

- Key message: "What goes in, what stays out"
- Layout: white background, gold top bar. Headline, then two-column grid of rounded cards, then guiding principle below.
- Left column (Include): purple-tinted background and border. Header with checkmark icon, purple underline. Items with "✓" markers.
- Right column (Leave out): gray-tinted background and border. Header with X icon, gray underline. Items with "✗" markers.
- **Include** (ordered by non-obvious first): Domain vocabulary the model can't infer, build and test commands, project structure overview, naming conventions, common pitfalls and gotchas
- **Leave out** (principle-first): Anything discoverable by reading code, information that changes frequently, contradictions with the actual codebase, lengthy tutorials or explanations
- Guiding principle: "If the agent can figure it out by reading, don't repeat it. If it can't, write it down." — italic, gold left-border accent.

## 14b-bridge-to-skills

- Transition slide — signals topic pivot from AGENTS.md to Skills.
- Pattern: A4 (transition-slide) from `shared/slide-patterns.css`
- Layout: purple gradient background, gold top bar. Centered, vertically stacked.
- Top: progress indicator — pill-shaped container with two steps connected by a line:
  - Step 1 (AGENTS.md): gold-filled circle with checkmark inside
  - Step 2 (Skills): outlined circle with "2" inside
  - Labels below each dot
- Center: large bridge question — "What if you need guidance only for specific tasks?"
- Below: context box with subtle gold border — "AGENTS.md is always on. But some instructions only matter for certain kinds of work."
- Purpose: creates curiosity before introducing skills; gives learners a mental filing moment.

## 15-introduction-skills

- Key message: "Context documents are always-on. Skills are on-demand."
- Layout: white background, gold top bar. Headline, then two contrast cards side by side, then analogy callout band, then tip box, then source link.
- Each contrast card: icon in purple-tinted rounded square + bold label + mode badge (small uppercase pill) + description. Subtle purple border and background.
- Card 1 (pinned note icon — rectangle with pin dot, content lines): **AGENTS.md** — badge "Always loaded" — "Fires every session, every task — the foundation of what your agent knows about this project"
- Card 2 (card with lightning bolt — invoked on demand): **Skill** — badge "On demand" — "A named procedure invoked only when the task matches — pulled from the drawer when you need that specific recipe"
- Analogy callout: full-width gold-tinted band with house/kitchen SVG icon on left. Large italic text with bold purple lead-in:
  - "Think of it like a kitchen: AGENTS.md is the house rules posted on the wall. A skill is a recipe card you pull from the drawer when you're making a specific dish."
- Tip box: full-width purple-tinted card with info circle icon.
  - "Tip: Reference your skills in AGENTS.md — any agent that reads it will discover them, regardless of tool."
- Source: "Further reading: agentskills.io" — linked, gold-underlined.
- Note: does NOT show skill structure (that's slide 16). Focuses purely on the conceptual contrast.

## 16-skill-example

- Key message: "A real skill: db-query" — showing what an actual skill file looks like
- Layout: white background, gold top bar. Headline with inline code-styled "db-query". Two-column grid below (wider left for code, narrower right for annotations). Columns stretch to equal height.
- Left column: monospace code block in purple-tinted rounded container. Shows a truncated sub-sample of the real skill:
  - Frontmatter: name, description, whenToUse
  - One short body section: "No setup required" (single line about Lambda client)
  - Faded ellipsis: "... (filtering, query limits)" — signals truncation
- Right column: three annotation cards stacked vertically, then download link below.
  - Each annotation card: small icon in rounded square + bold title + description
  1. **name** (tag icon) — "How you invoke it — short and memorable"
  2. **description + whenToUse** (search icon) — "How the agent decides whether to load this skill — match criteria"
  3. **body (instructions)** (document icon) — "The procedure the agent follows — constraints, tips, and guardrails"
- Download link: gold-tinted box with download icon. "Download full skill: db-query.md" → <https://github.com/user-attachments/files/31163900/db-query.md>
- Source content: real skill from the snowexsql project workshop repo.

## 17-demo-adding-skill

[LIVE DEMO]

- Pattern: A1 (demo-slide) from `shared/slide-patterns.css`
- Badge: "LIVE DEMO"
- Title: "Adding a skill and re-running"
- Command: `$ claude`
- Description: "Same prompt again — but now with a skill registered for database queries."
- Watch-for box: "Does the agent invoke the skill? Does the output follow the skill's prescribed pattern?"
- Note to self: demo shows creating the llm/skills/ directory, adding the skill file, updating AGENTS.md to reference it, re-running the prompt.

## 18-hands-on-03

- Pattern: A2 (handson-slide) from `shared/slide-patterns.css`
- Badge: "YOUR TURN"
- Headline: "What changed with the skill?"
- Instructions (bordered container, centered, gold arrow markers):
  - "Is the output more consistent between partners?"
  - "Think of ways to improve the skill"
- Discuss box: "What would you add or change in the skill to get better results?"

## 19-context-vs-skill

- Key message: "What we built today"
- Layout: white background, gold top bar. Headline, then three-step horizontal journey with gold arrows between steps, then outcome callout below.
- Each step: centered card with icon in large purple-tinted rounded square, bold label, short description, and result badge (emphasized text in purple-tinted pill).
- Steps connected by large gold "→" arrows:
  1. **Bare repo** (monitor icon) — "No guidance" → badge "Confident but wrong"
  2. **+ AGENTS.md** (file icon) — "Always-on context" → badge "Right direction"
  3. **+ Skill** (lightning-card icon) — "On-demand procedure" → badge "Consistent output"
- Outcome callout: full-width gold-tinted box with checkmark circle icon, strong gold border.
  - "Each layer reduced guessing — the agent spent tokens following your instructions instead of reverse-engineering your project."
- Purpose: visual recap of the workshop progression, gives audience a sense of accomplishment before closing takeaways.

## 20-takeaways

- Key message: "You're a context engineer now"
- Layout: white background, gold top bar. Headline, then two-column grid (mirrors slide 14's structure), then guiding principle below.
- Both columns: purple-tinted background and border, rounded. Header with icon, bold uppercase label, purple underline. Items with gold "→" markers (not checkmarks — these are next steps, not done/don't).
- Left column (file icon): **AGENTS.md**
  - Start with 5 lines — project name, build command, test command
  - Add domain vocabulary the model gets wrong
  - Grow it as you observe agent mistakes
- Right column (lightning-card icon): **Skills**
  - Identify a task you repeat — that's your first skill
  - Write the steps you'd tell a colleague
  - Reference the skill from AGENTS.md so the agent finds it
- Guiding principle: "Context engineering is iterative: observe what the agent gets wrong, then write the context that would have prevented it." — italic, gold left-border accent.
