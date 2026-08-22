---
name: slide-redesign
description: Redesign or create slides for the Context Engineering tutorial deck
whenToUse: When the user asks to restyle, redesign, create, or fix a slide in this presentation deck
---

# Slide Redesign Skill

## Pedagogy principles

This is an educational deck for a 60-minute hands-on tutorial. Every design decision serves learning:

- **Background color signals mode.** White = content the audience absorbs (read/learn). Purple gradient = activity the audience does (demo, hands-on). This is intentional mode signaling — the audience knows what's expected of them before reading a word.
- **Activity slides always have audience instructions.** Every demo slide needs a "WATCH FOR" box. Every hands-on slide needs a "DISCUSS" box. These are large and clearly visible — they tell the audience what to pay attention to or talk about.
- **Progressive disclosure.** Introduce concepts before examples, examples before practice. Don't show code structure on the same slide as the conceptual definition. Each slide has ONE job.
- **Back-of-room readability.** This is presented in a classroom. Everything must be readable from 10+ meters away. Minimum body text ~1rem, headlines 2.4rem+, icons 36px+, SVG strokes 2px+.
- **Reduce cognitive load.** One anchoring element per slide. No walls of text. Bullets are talking points delivered aloud, not rendered on the slide.

## Accessibility constraints

- Gold (#ffc700) is NEVER used as text on white backgrounds — fails WCAG AA (~1.5:1 contrast ratio). On white: gold for borders, accents, bullets, bars only. Text emphasis = purple.
- Gold text IS fine on purple gradient backgrounds.
- Never use black backgrounds. Always UW purple gradient or white with gold accent.
- All colors must be high-contrast and color-blind safe. Never rely on color alone to convey meaning — use shapes, text labels, or patterns as secondary indicators.
- No text with opacity below 0.7 if the audience needs to read it.
- No gray lighter than gray-70 (#555) for body text on white backgrounds. Gray-50 (#767676) only for decorative/optional text.

## Technical procedure

### Step 1: Understand the context

1. Read the SLIDES.md entry for the target slide — it has the content spec and layout description.
2. Read `shared/slide-patterns.css` to find the matching pattern (A1–A4 for activity, B1–B6 for content, C1–C2 for special).
3. Read the current HTML file in `content/XX-name.html` (if it exists).
4. Read adjacent slides to understand flow and avoid duplicating content.

### Step 2: Build the slide

1. Write all CSS in an inline `<style>` block inside the `<section>`.
2. Use `.slide-XX` prefix on all class names (where XX = the slide number from the filename).
3. NEVER use shared CSS classes from `styles.css` — they lose specificity against `section.slide.active { display: flex }` in header.html.
4. The outer div (`.slide-XX`) MUST have `width: 100%; height: 100%; display: flex;` to fill the section properly (the parent section is `display: flex` when active).
5. Copy the appropriate pattern's CSS structure from `shared/slide-patterns.css`, then customize.

### Step 3: Update documentation

1. **SLIDES.md** — Update the slide's entry with a plain-English layout description. NO CSS syntax in SLIDES.md — describe visual outcomes ("two-column grid", "gold top bar", "purple-tinted background"), not implementation details.
2. **VISUALS.md** — If the slide has any built visual elements (SVG icons, diagrams, decorative elements), document them in the per-slide section. Mark built elements as "(built)" to distinguish from future photography/additions.

### Step 4: Verify

Run `bash build.sh .` and confirm the build succeeds with the expected slide count (currently 22).

## Common patterns

- **White content slides:** gold top bar (5px, via ::before pseudo-element), flex column, left-aligned, padding space-8/space-12.
- **Purple activity slides:** radial-gradient background, centered, terminal window shape for demos, large badge + headline + instruction boxes for hands-on.
- **Card grids:** icon (in purple-tinted rounded square) + bold title + description. Subtle purple border, very light purple-tinted background.
- **Callout boxes:** gold left-border for principles/quotes on white slides. Gold-tinted background band for tips/analogies.
- **Demo slides:** "LIVE DEMO" badge (2rem, gold border), monospace title, `$ command` in gold, description in white at 75% opacity, "WATCH FOR" box (full width, gold border).
- **Hands-on slides:** "YOUR TURN" badge, bold headline, instruction container with gold "→" markers, "DISCUSS" box (gold border, centered).

## What NOT to do

- Don't use shared `.handson-slide` or `.demo-slide` classes from styles.css
- Don't put CSS in SLIDES.md
- Don't use black backgrounds
- Don't use gold text on white
- Don't forget to update both SLIDES.md AND VISUALS.md
- Don't duplicate content that's on an adjacent slide
- Don't make font sizes below 0.85rem for anything the audience reads
- Don't use SVG strokes thinner than 1.8px for important elements
