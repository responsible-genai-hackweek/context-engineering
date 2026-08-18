# Context Engineering

A 60-minute tutorial on making project context durable for AI coding agents — so they remember your conventions, vocabulary, and structure across sessions.

Target audience: Researchers and developers using AI coding agents on scientific codebases
Duration: 60 minutes (slides + live demos interleaved)

## How to render this deck (instructions for the slide generator)

**This document is a design brief, not slide copy.**

**Two-pass workflow.** This deck is built in two passes, and SLIDES.md governs only the first.

- **First pass (this file): content and structure only.** Build the deck to a publishable-looking, intentional state using only typography, layout, color palette, and the gold accent. Use no photographs and no decorative icons in this pass. The deck should look complete on its own — if it had to be presented tomorrow with no images, it should feel finished rather than naked.
- **Second pass (separate VISUALS.md): additive visual elements.** After the first pass is rendered and rehearsed, VISUALS.md specifies photographs, diagrammatic accents, and iconography to *add* to existing slides. The second pass modifies the already-rendered HTML; it does not rebuild slides from scratch.
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
- Presenter names: Anthony Arendt, Joe Meyer
- Affiliation: University of Washington / eScience Institute
- Date: August 2026

## 02-the-problem

- Key message: "Your agent forgets everything between sessions"
- The model knows Python. It does not know your data, your conventions, or your goals.
- Every new session starts from zero — unless you engineer durability into the context.
- Note to self: Bridge from Tutorial 1's "built-in knowledge vs. in the prompt" distinction. That tutorial showed the gap; this one shows how to close it permanently.

## 03-durability-spectrum

- Key message: "A spectrum of durability"
- The agent forgets everything between sessions. You make context durable by placing it somewhere the agent will find it again — but where?
- Present as a horizontal spectrum from "always present" to "summoned on demand":
  - **Always loaded** — Context documents (AGENTS.md, CLAUDE.md). Read at session start, every time, regardless of task.
  - **Auto-triggered** — Rules, path-scoped constraints. Fire when specific files are touched.
  - **Invoked on match** — Skills, named procedures. The agent reaches for them when a task fits.
  - **Delegated** — Subagents, specialized personas. Summoned for specific expertise.
- Note to self: Don't present this as a canonical four-item list. The specific mechanisms vary by tool and will evolve. What's durable is the spectrum concept: you're choosing how broadly and how automatically context gets loaded. Say something like "Current tools give you several controls along this spectrum — here are the ones you'll encounter today."

## 04-tradeoff

- Key message: "Always-on costs tokens. On-demand requires recognition."
- The core tradeoff on the spectrum:
  - Left side (always loaded): guaranteed to be present, but consumes context budget every turn whether needed or not
  - Right side (on demand): precise and efficient, but the agent must recognize when to reach for it
- This is not a fixed taxonomy — tools are evolving and the specific mechanisms will change. The tradeoff is what's durable: you're always choosing between "pay the cost of loading it every time" and "trust the agent to know when it's needed."
- Note to self: This is the conceptual slide that makes the rest of the tutorial make sense. When someone asks "why not just put everything in AGENTS.md?" — point back here. When someone asks "why not make everything a skill?" — same answer.

## 05-today-focus

- Key message: "Today: two points on the spectrum"
- We'll work with the two most common and transferable mechanisms:
  - A context document (AGENTS.md) — always-on, loaded every session
  - A skill — on-demand, invoked when the task matches
- The pattern: observe failure → add targeted context → verify improvement.
- These two cover most researchers' needs. The others are refinements you'll reach for as projects grow.
- Note to self: Don't say "the other two levers are for later" — that reifies the count. Say "other mechanisms exist for finer control; these two get you most of the way."

## 06-introducing-snowex

- Key message: "SnowEx: a real research database"
- Briefly introduce the SnowEx SQL database: snow hydrology measurements, multiple campaigns, domain-specific vocabulary.
- This is a real scientific artifact — not a toy example. It has naming conventions, table relationships, and domain terms the model has never seen.
- Note to self: Keep this short. The point is just to establish that participants are working with something realistic, not a demo repo designed to make AI look good.

## 07-the-task

- Key message: The prompt we'll use throughout
- Display the exact prompt in large monospace:
  "Create me a code block that queries the database and returns snow depth layer data for a snow pit and date during the Alaska campaign"
- This question has a correct answer and multiple wrong paths to it.
- Note to self: Emphasize that this prompt stays constant — the only variable is what context the agent has.

## 08-demo-no-context

[LIVE DEMO]

- Display text: "Demo: Agent with no context"
- Show the prompt being sent
- Orienting statement: "Watch for: guessed column names, wrong tables, confident wrong turns"
- Note to self: Run the prompt against Claude Code with no AGENTS.md. Narrate what the agent does. Let it fail visibly. ~3 minutes.

## 09-failure-modes

- Key message: "Confident, fast, and wrong"
- After the demo, name the failure modes the audience just saw:
  - Guesses at column names that don't exist
  - Picks the wrong table
  - Applies naming conventions from other projects
  - Takes many turns fumbling toward something that looks right but isn't
- The problem isn't slowness — it's confident wrong turns that waste the researcher's time.
- Note to self: Ask participants to buddy up and compare what they saw. 2 minutes.

## 10-partner-compare-1

- Key message: "Compare with a partner"
- Instruction slide: "Buddy up. Compare your agent's output. How different are they?"
- Note to self: This is the first pair activity. Give 2 minutes. The point is that without context, outputs diverge wildly — the agent is guessing differently each time.

## 11-building-incrementally

- Key message: "Context is added in response to observed behavior"
- The authoring pattern:
  1. Observe a failure
  2. Add targeted context
  3. Re-run the same prompt
  4. Verify improvement
- You don't write AGENTS.md speculatively. You write it in response to what you saw go wrong.
- Note to self: This is the core pedagogical message. Don't front-load the authoring — let the failures drive what gets written.

## 12-step1-minimal

- Key message: "Start with one sentence"
- Show a minimal AGENTS.md: just "This is a snow hydrology database built on PostgreSQL."
- That's it. One line. Enough to orient but not enough to prevent the failures we saw.
- Note to self: Transition to the demo — we'll add this file and re-run.

## 13-demo-minimal-context

[LIVE DEMO]

- Display text: "Demo: Re-run with minimal AGENTS.md"
- Show: adding the one-line AGENTS.md, then re-running the same prompt
- Orienting statement: "Watch for: Does it pick the right database type? Does it still guess at table names?"
- Note to self: Modest improvement expected — it knows it's PostgreSQL now but still doesn't know the schema. ~2 minutes.

## 14-step2-structure

- Key message: "Add project structure"
- Show the AGENTS.md growing: table names, how they relate, primary key conventions.
- The agent now knows what exists — it doesn't have to guess at table names.
- Note to self: This is the "navigation" layer. The agent can find things but may still misinterpret domain terms.

## 15-demo-with-structure

[LIVE DEMO]

- Display text: "Demo: Re-run with structure added"
- Show: the updated AGENTS.md with table/relationship info, then re-running the prompt
- Orienting statement: "Watch for: correct table navigation, but possible domain confusion (what is a 'layer'? what counts as 'Alaska campaign'?)"
- Note to self: Better navigation, still domain confusion. ~2 minutes.

## 16-step3-vocabulary

- Key message: "Add domain vocabulary"
- Show AGENTS.md gaining domain terms: what "layer" means in snow science, how campaigns are named, what units are used, how time series are stored.
- This is knowledge the model cannot get from reading code — it's expert knowledge about the scientific domain.
- Note to self: This is the key insight for researchers: YOUR domain knowledge is exactly what the agent lacks. You are the source of truth for vocabulary.

## 17-demo-with-vocabulary

[LIVE DEMO]

- Display text: "Demo: Re-run with domain vocabulary"
- Show: full AGENTS.md with vocabulary, re-running the same prompt
- Orienting statement: "Watch for: correct interpretation of 'snow depth layer', correct campaign filter, appropriate units"
- Note to self: This should be the "aha" moment — same prompt, dramatically better result. ~2 minutes.

## 18-partner-compare-2

- Key message: "Compare again — what changed?"
- Instruction slide: "Same pairs. Compare outputs now. How different are they from each other? From the first attempt?"
- Note to self: Outputs should converge — with shared context, agents produce more consistent results. 2 minutes. The convergence itself is evidence that context engineering works.

## 19-what-belongs

- Key message: "What goes in, what stays out"
- Two columns or a split layout:
  - **Belongs:** Project structure, naming conventions, domain vocabulary the model can't infer, common pitfalls, standards for how work should be done
  - **Does not belong:** Anything the agent can discover by reading code, information that changes frequently, contradictions with the actual codebase, personal preferences that don't apply to others
- Note to self: Connect to the guidelines from agents.md — keep under 200 lines / 32 KiB, be specific not vague, shorter is better.

## 20-goldilocks

- Key message: "Too much context is also a failure mode"
- Over-stuffing: bloated file consumes context window on every turn, crowds out task-specific context, agent drowns in instructions
- Under-stuffing: agent falls back to guessing, produces confident hallucinations
- The test: does agent behavior improve on realistic prompts? That's how you know you have the balance right.
- Note to self: This is a common mistake — people try to document everything. The AGENTS.md is not a README.

## 21-transition-to-skills

- Key message: "Context documents are always-on. Skills are on-demand."
- AGENTS.md fires on every session, every task — it's the foundation.
- But some context only matters for specific tasks. That's what skills are for.
- A skill is a named procedure the agent invokes when the task matches — like a recipe it reaches for only when cooking that dish.
- Note to self: Transition to the second lever. Refer back to the spectrum slide (04).

## 22-skills-intro

- Key message: "A skill = a reusable procedure with a trigger"
- Structure of a skill: a name, a description (used for matching), and step-by-step instructions.
- The agent decides when to invoke it based on task match — you don't have to remember to ask.
- Source: https://agentskills.io
- Note to self: Keep this conceptual. The demo will make it concrete.

## 23-skill-example

- Key message: Show the db-query skill structure
- Display the skeleton of the skill file in monospace: name, description, the key steps it encodes.
- The skill knows: connection details, which tables to query for what, the correct join patterns, output format expectations.
- Note to self: This is the actual db-query.md skill file from Joe's materials. Don't show the whole thing — just enough to see the pattern.

## 24-demo-adding-skill

[LIVE DEMO]

- Display text: "Demo: Adding a skill and re-running"
- Show: creating the llm/skills/ directory, adding the skill file, updating AGENTS.md to reference it, re-running the prompt
- Orienting statement: "Watch for: does the agent invoke the skill? Does the output follow the skill's prescribed pattern?"
- Note to self: Add the skill file, add the reference to AGENTS.md ("## Skills — See llm/skills for a list of skills and their descriptions"), re-run the same prompt. ~3 minutes.

## 25-partner-compare-3

- Key message: "What changed with the skill?"
- Instruction slide: "Same pairs. What's different now? Is the output more consistent between partners? Think of ways to improve the skill."
- Note to self: 2 minutes. Outputs should be very consistent now — the skill prescribes a procedure, not just vocabulary. The procedure converges behavior.

## 26-context-vs-skill

- Key message: "Always-on context vs. on-demand procedure"
- When to use each:
  - Context document: information needed regardless of task (structure, vocabulary, conventions)
  - Skill: a specific procedure that only applies to a class of tasks (querying the DB, running the test suite, deploying)
- A skill reference in AGENTS.md is the bridge — the context document points to the skill so the agent knows it exists.
- Note to self: Reinforce the "levers" framing. You're choosing a durability mechanism based on how broadly applicable the context is.

## 27-iterative-refinement

- Key message: "The loop never ends"
- Context engineering is not a one-time setup. It's an ongoing practice:
  - Observe agent behavior → identify failures → add context → verify
  - Remove context that's no longer needed (the codebase changed, the convention evolved)
  - Ask the agent what's missing — it can tell you what confused it
- Note to self: Mention the optional exercise: "Ask the agent what's missing in the agents.md or skills file." Be critical of its suggestions — remember what belongs and what doesn't.

## 28-demo-ask-agent

[LIVE DEMO]

- Display text: "Demo: Asking the agent what's missing"
- Show: prompting the agent to review the AGENTS.md and suggest improvements
- Orienting statement: "Be critical of suggestions. Does the agent recommend things it could discover by reading code? Is it too specific? Too generic?"
- Note to self: Optional/time-permitting. The agent will often over-suggest. Use this to reinforce the "what belongs" criteria. ~3 minutes if time allows.

## 29-guidelines-summary

- Key message: "Practical guidelines"
- The rules of thumb from agents.md:
  - Start simple and expand as needed
  - Be specific: "Run lint after every change" not "Follow best practices"
  - Keep under 200 lines / 32 KiB
  - Nested files for subdirectories that diverge from root
  - It's a guide, not enforcement — no guarantee the agent obeys
  - Keep human-readable content in README; machine-optimized content in AGENTS.md
- Source: https://agents.md
- Note to self: These are reference points, not things to read aloud. The slide should be scannable.

## 30-spectrum-revisited

- Key message: "You now own two points on the spectrum"
- Return to the spectrum diagram from slide 03, now with context documents and skills highlighted as "practiced today."
- As your project grows, you may reach for finer-grained mechanisms — path-scoped rules, specialized subagents, or whatever new controls tools introduce next.
- The transferable skill is the spectrum thinking: how broadly does this context apply, and how should it get loaded?
- Note to self: Brief forward-looking slide. Don't enumerate what's left — the point is that the mental model transfers even as tooling changes.

## 31-takeaways

- Key message: "Context engineering is the researcher's primary lever"
- Three takeaways:
  1. The model's built-in knowledge ends at your project boundary. Everything specific to your work must be engineered in.
  2. Context is added in response to observed behavior — not written speculatively in advance.
  3. Durability is a spectrum: from always-on (documents) to on-demand (skills) to triggered (rules) to delegated (subagents). Choose the mechanism that matches how broadly the context applies.
- Note to self: This is the synthesis. Connect back to Tutorial 1's framing and forward to whatever comes next.

## 32-next-steps

- Key message: "What to do after this tutorial"
- Practical next steps:
  - Write an AGENTS.md for one of your own research repositories this week
  - Start with one sentence. Run a prompt. Observe. Add context. Repeat.
  - Share your AGENTS.md with a collaborator — does the agent behave consistently for them too?
- Note to self: Give participants a concrete commitment. One repo, this week.
