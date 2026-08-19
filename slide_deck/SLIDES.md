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

**Live demo slides:** Slides marked `[LIVE DEMO]` are holding-screen placeholders shown while the instructor works in a terminal. They should display a short orienting statement and the prompt or task being demonstrated — enough for the audience to follow along without reading code off the projector's second screen. Use a dark background with monospace type to signal "we are in the terminal now."

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
- An Agent is good at reverse engineering (and eager to). It does not know your data, your conventions, or your goals.
- Every new session starts from minimal "memory"
- Persistent durability into the context is dependent on you.

## 03-durability-spectrum

- Key message: "Persistent context options in current landscape"
- Agents are starting to build "memory" features, but the durability of context is still largely in your hands.
- Present as a horizontal spectrum from "always present" to "on demand":
  - **Always loaded** — Context documents (AGENTS.md). Read every time, regardless of task.
  - **Invoked on match** — Skills, named procedures. Loaded when a task fits.
  - **Auto-triggered** — Rules, path-scoped constraints. Fire when specific files are touched.
  - **Delegated** — Subagents, specialized personas. Summoned for specific expertise.

## 04-today-focus

- Key message: "Today: Two options on the spectrum"
- We'll work with the two most common and transferable mechanisms:
  - A context document (AGENTS.md) — always-on, loaded every session
  - A skill — on-demand, invoked when the task matches
- These cover most researchers' needs. The others are refinements you'll reach for as projects grow.

## 05-introducing-snowex

- Key message: "SnowEx: a Python library for a research database"
- SnowEx ....
- Clone the forked repo - Hint: Agents cheat!

## 06-scientific-use-case

- Key message: "Scientific use case: Querying snow depth layer data"
- Display the exact prompt in large monospace:
  "Create me a code block that queries the database and returns snow depth layer data for a snow pit and date during the Alaska campaign"
- This question has multiple answers. One for a standard user and one for a power user.
- For the default answer, we want to guide users to the simple solution first.

## 08-demo-no-context

[LIVE DEMO]

- Display text: "Demo: Repository with no context"

## 09-first-result

- Key message: "Confident, fast, and complicated"
- After the demo, highlight the observed issues:
  - The agent went straight into reverse engineering
  - It confidently suggested the more technical solution, even though the README shows the simpler as preferred
  - It burned a lot of tokens guessing the query parameters

## 10-hands-on-01

- Key message: "HANDS ON - Compare your output with a partner"
- Instruction slide: "Buddy up. Compare your agent's output. How different are they?"

## 11-start-adding-context

- Key message: "How to guide the LLM with context?"
- First option: Add a central context document - AGENTS.md
- Official guidelines: <https://agents.md>
- Put the quote as the central message on the slide:
- "Think of AGENTS.md as a README for agents: a dedicated, predictable place to provide the context and instructions to help AI coding agents"

## 12-writing-tips

- Key message: "A good AGENTS.md is concise and actionable"
- Start simple and expand as needed
- Be specific - "Follow best practices" vs "Run lint after every change"
- Shorter is better. Keep under 200 lines or 32 KiB
- Nested files are good for big repos or if a folder diverges from main file. The "closest" file wins.
- It's a guide not an enforcement. There is no guarantee that "DO NOT EDIT" files won't get changed
- Keep everything for humans in the repo README, LLMs will read that too
- Be aware that future version of LLM models might have learned from public information

## 13-demo-with-agents

[LIVE DEMO]

- Display text: "Demo: Re-run with AGENTS.md"
- Orienting statement:
  - Does it pick the right connection type?
  - Does it still guess at filter options?

## 14-hands-on-02

- Key message: "Compare again — what changed?"
- Instruction slide:
  - Compare outputs now.
    - How different are they from each other?
    - From the first attempt?

## 15-agents-summary

- Key message: "What goes in, what stays out"
- Two columns or a split layout:
  - **Belongs:** Project structure, naming conventions, domain vocabulary the model can't infer, common pitfalls, standards for how work should be done
  - **Does not belong:** Anything the agent can discover by reading code, information that changes frequently, contradictions with the actual codebase, personal preferences that don't apply to others
- KISS principle: Keep it simple stup...

## 16-introduction-skills

- Key message: "Context documents are always-on. Skills are on-demand."
- AGENTS.md fires on every session, every task — it's the foundation.
- A skill = a reusable procedure with a trigger
- A skill is a named procedure the agent invokes when the task matches — like a recipe it reaches for only when cooking that dish.
- Show the structure of a skill on the side
  - name, description (used for matching), and instructions.
- This is the very basic start. Skills can be advanced through multiple options. See: <https://agentskills.io>

## 17-skill-example

- Key message: Show the db-query skill structure
- Display the skeleton of the skill file in monospace: name, description, the key steps it encodes.

## 18-demo-adding-skill

[LIVE DEMO]

- Display text: "Demo: Adding a skill and re-running"
- Show: creating the llm/skills/ directory, adding the skill file, updating AGENTS.md to reference it, re-running the prompt
- Orienting statement:
  - Does the agent invoke the skill?
  - Does the output follow the skill's prescribed pattern?

## 19-hands-on03

- Key message: "What changed with the skill?"
- Instruction slide:
  - What's different now?
  - Is the output more consistent between partners?
  - Think of ways to improve the skill.

## 20-context-vs-skill

- Key message: "Always-on context vs. on-demand procedure"
- When to use each:
  - Context document: information needed regardless of task (structure, vocabulary, conventions)
  - Skill: a specific procedure that only applies to tasks (querying the DB, running the test suite)
- Create bridges to skills in the AGENTS.md so the LLM knows about them

## 21-takeaways

- Key message: "Context engineering is the researcher's primary lever"
- Three takeaways:
  1. The model's built-in knowledge ends at your project boundary.
  1. Domain knowledge of your work must be engineered in.
  1. Add context as you observer LLM behavior
  1. Choose the mechanism that matches how broadly the context applies.
