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

**Live demo slides:** Slides marked `[LIVE DEMO]` are holding-screen placeholders shown while the instructor works in a terminal. They should display a short orienting statement and the prompt or task being demonstrated — enough for the audience to follow along without reading code off the projector's second screen. Never use black or near-black backgrounds anywhere in this deck. Demo slide visual treatment:
  - Purple gradient background
  - A semi-transparent dark terminal window shape (rounded rect, 70% width, 60% height) centered on the slide with three dots (traffic light) in the top-left corner
  - Bold gold "LIVE DEMO" badge
  - Title in large monospace
  - A `$ claude` command line in gold to show what's being executed
  - Orienting questions in white body text below

---

## 01-title

Title slide with UW branding.

- Title: "Context Engineering for AI Coding Agents"
- Subtitle: "Making your project knowledge durable"
- Presenter names: Anthony Arendt, Joachim Meyer
- Affiliation: University of Washington / eScience Institute, Boise State University
- Date: August 2026

## 02-the-problem

- Key message: "Your agent does not remember most of your project context"
- Layout: Headline spans the full width. Four supporting points arranged in a 2×2 grid below, each with a gold left-border accent. Use the full slide width — no narrow column.
- Bullets (rendered as 2×2 grid, reading order top-left → top-right → bottom-left → bottom-right):
  1. Every new session starts from minimal "memory" (concrete problem)
  2. Doesn't know your data, your conventions, or your goals (what's missing)
  3. Good at reverse engineering — and eager to try (the trap: fills the gap confidently but wrong)
  4. Persistent durability is dependent on you (call to action, transitions to next slide)

## 03-durability-spectrum

- Key message: "Persistent context options in current landscape"
- Subhead (rendered): "Agents are building 'memory' features, but durability is still largely in your hands."
- Layout: Four equal cards in a horizontal grid spanning full width. Each card has a gold top border, a bold uppercase label, a one-line description, and a monospace example. Below the cards, a gradient line (gold → gray) with axis labels: "Always present" on the left, "On demand" on the right.
- Cards (left to right):
  1. **Always loaded** — Context documents read every time, regardless of task. Example: AGENTS.md
  2. **Invoked on match** — Skills and named procedures loaded when a task fits. Example: Skills
  3. **Auto-triggered** — Rules and path-scoped constraints that fire on specific files. Example: Rules
  4. **Delegated** — Subagents and specialized personas summoned for expertise. Example: Subagents

## 04-today-focus

- Key message: "Today: Two options on the spectrum"
- Layout: Two side-by-side cards spanning the full slide width below the headline. Each card contains a large number, a bold label, and a short description. Cards have a subtle gold border and translucent background on the purple gradient.
- Card 1: Context document (AGENTS.md) — always-on, loaded every session, the foundation of what your agent knows
- Card 2: Skill — on-demand, invoked when the task matches, a recipe reached for only when needed
- Note to self: These cover most researchers' needs. The others are refinements you'll reach for as projects grow.

## 05-introducing-snowex

- Key message: "snowexsql — A Python library for the SnowEx database"
- Layout: Logo top-left beside headline. Below, a two-column grid: left column has 4 summary bullets with gold left-border; right column has a schematic diagram showing the data flow (Your code → snowexsql package → SnowEx DB → DataFrame). Bottom callout about cloning the repo.
- Logo: https://snowexsql.readthedocs.io/en/latest/_static/logo.png
- Summary points:
  - NASA SnowEx campaigns — multi-year field and airborne snow measurements across western US and Alaska
  - PostgreSQL/PostGIS database — snow depths, density, temperature, stratigraphy, SWE
  - Python package — query via a Lambda client (no credentials) or direct DB connection
  - Returns DataFrames — filters by campaign, date, type, location
- Schematic: Your code → snowexsql (PointMeasurements, LayerMeasurements) → SnowEx DB, returns DataFrame
- Callout: "Clone the forked repo: github.com/jomey/snowexsql — Hint: Agents cheat!"

## 06-scientific-use-case

- Key message: "Scientific use case: Querying snow depth layer data"
- Layout: centered on purple background, three vertical sections
- Top: headline in gold uppercase, prompt in bordered monospace box (80% width, centered)
- Middle: forking-path SVG diagram showing decision point branching into two paths
- Bottom: two side-by-side cards comparing answer paths:
  - Left card (gold border, "Start here" badge): Standard user — simple high-level API query
  - Right card (subtle border): Power user — advanced joins and raw SQL
- Footer note: "This question has multiple valid answers — we guide the agent to recommend the simple solution first."
- Display the exact prompt in large monospace:
  "Create me a code block that queries the database and returns snow depth layer data for a snow pit and date during the Alaska campaign"
- This question has multiple answers. One for a standard user and one for a power user.
- For the default answer, we want to guide users to the simple solution first.

## 07-demo-no-context

[LIVE DEMO]

- Display text: "Demo: Repository with no context"

## 08-first-result

- Key message: "Confident, fast, and complicated"
- Layout: Three equal cards in a horizontal grid, each with an SVG icon, bold label, and description. Cards have gold top border and subtle purple-tinted background. Order builds pedagogically: what it did → why it's wrong → what it cost.
- Card 1: Reverse engineered — dove into source code instead of using documented patterns (magnifying glass icon)
- Card 2: Chose the complex path — suggested advanced solution when README shows simpler as preferred (upward trend arrow icon)
- Card 3: Burned tokens guessing — spent effort guessing query parameters it could have been told (clock icon)

## 09-hands-on-01

- Key message: "YOUR TURN - Run the prompt, then compare with a partner"
- Layout: Purple gradient background. "Your Turn" badge (gold border). Headline. A 3-step activity row inside a subtle bordered container with SVG icons: Run prompt → Compare outputs → Discuss. Below, a dark prompt box with explicit "Paste this prompt" instruction and the query. A discussion question at the bottom in gold-accented text.
- Activity steps with icons: terminal window (run prompt) → two side-by-side panels with dashed connector (compare) → two overlapping circles (discuss)
- Prompt box: "Create me a code block that queries the database and returns snow depth layer data for a snow pit and date during the Alaska campaign"
- Discussion prompt: "How different are the outputs? Did you get the same solution?"

## 10-start-adding-context

- Key message: "How to guide the LLM with context?"
- First option: Add a central context document - AGENTS.md
- Official guidelines: <https://agents.md>
- Put the quote as the central message on the slide:
- "Think of AGENTS.md as a README for agents: a dedicated, predictable place to provide the context and instructions to help AI coding agents"

## 11-writing-tips

- Key message: "A good AGENTS.md is concise and actionable"
- Start simple and expand as needed
- Be specific - "Follow best practices" vs "Run lint after every change"
- Shorter is better. Keep under 200 lines or 32 KiB
- Nested files are good for big repos or if a folder diverges from main file. The "closest" file wins.
- It's a guide not an enforcement. There is no guarantee that "DO NOT EDIT" files won't get changed
- Keep everything for humans in the repo README, LLMs will read that too
- Be aware that future version of LLM models might have learned from public information

## 12-demo-with-agents

[LIVE DEMO]

- Display text: "Demo: Re-run with AGENTS.md"
- Orienting statement:
  - Does it pick the right connection type?
  - Does it still guess at filter options?

## 13-hands-on-02

- Key message: "Compare again — what changed?"
- Instruction slide:
  - Compare outputs now.
    - How different are they from each other?
    - From the first attempt?

## 14-agents-summary

- Key message: "What goes in, what stays out"
- Two columns or a split layout:
  - **Belongs:** Project structure, naming conventions, domain vocabulary the model can't infer, common pitfalls, standards for how work should be done
  - **Does not belong:** Anything the agent can discover by reading code, information that changes frequently, contradictions with the actual codebase, personal preferences that don't apply to others
- KISS principle: Keep it simple stup...

## 15-introduction-skills

- Key message: "Context documents are always-on. Skills are on-demand."
- AGENTS.md fires on every session, every task — it's the foundation.
- A skill = a reusable procedure with a trigger
- A skill is a named procedure the agent invokes when the task matches — like a recipe it reaches for only when cooking that dish.
- Show the structure of a skill on the side
  - name, description (used for matching), and instructions.
- This is the very basic start. Skills can be advanced through multiple options. See: <https://agentskills.io>

## 16-skill-example

- Key message: Show the db-query skill structure
- Display the skeleton of the skill file in monospace: name, description, the key steps it encodes.

## 17-demo-adding-skill

[LIVE DEMO]

- Display text: "Demo: Adding a skill and re-running"
- Show: creating the llm/skills/ directory, adding the skill file, updating AGENTS.md to reference it, re-running the prompt
- Orienting statement:
  - Does the agent invoke the skill?
  - Does the output follow the skill's prescribed pattern?

## 18-hands-on-03

- Key message: "What changed with the skill?"
- Instruction slide:
  - What's different now?
  - Is the output more consistent between partners?
  - Think of ways to improve the skill.

## 19-context-vs-skill

- Key message: "Always-on context vs. on-demand procedure"
- When to use each:
  - Context document: information needed regardless of task (structure, vocabulary, conventions)
  - Skill: a specific procedure that only applies to tasks (querying the DB, running the test suite)
- Create bridges to skills in the AGENTS.md so the LLM knows about them

## 20-takeaways

- Key message: "Context engineering is the researcher's primary lever"
- Three takeaways:
  1. The model's built-in knowledge ends at your project boundary.
  1. Domain knowledge of your work must be engineered in.
  1. Add context as you observer LLM behavior
  1. Choose the mechanism that matches how broadly the context applies.
