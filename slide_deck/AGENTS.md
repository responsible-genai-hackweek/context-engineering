# Context Engineering Slide Deck

A 22-slide HTML presentation for a 60-minute tutorial on context engineering for AI coding agents. UW-branded, designed for classroom delivery with back-of-room readability.

## Build

```
bash build.sh .
```

Reads `## XX-name` headings from SLIDES.md and concatenates corresponding `content/*.html` files into `build/index.html`.

## Key files

- `SLIDES.md` — Design brief for all slides. Content and plain-English layout descriptions. NO CSS in this file.
- `VISUALS.md` — Second-pass visual additions (photos, diagrams, icons). Documents what's already built.
- `shared/slide-patterns.css` — CSS recipe book. NOT a linked stylesheet. Read it, copy patterns into inline `<style>` blocks.
- `shared/header.html` — Base styles, CSS custom properties, navigation JS.
- `content/*.html` — Individual slide files with inline `<style>` blocks using `.slide-XX` prefixes.

## Architecture

Each slide is a `<section class="slide">` with its own `<style>` block using `.slide-XX` prefixed classes. Shared CSS classes from `styles.css` lose specificity against `section.slide.active { display: flex }` in header.html — never use them.

## Skills

- **slide-redesign** (`skills/slide-redesign.md`) — Use when creating, restyling, or fixing any slide. Covers pedagogy principles, accessibility constraints, and the exact build procedure.

## Critical rules

- White background = content slides. Purple gradient = activity slides (demos, hands-on).
- Gold (#ffc700) is NEVER text on white backgrounds. Gold for borders/accents only on white.
- Always update SLIDES.md AND VISUALS.md when changing a slide.
- Every activity slide must have audience instructions (WATCH FOR or DISCUSS box).
- Design for back-of-room readability: large fonts, thick strokes, high contrast.
- No CSS syntax in SLIDES.md — describe layouts in plain English, reference pattern names from slide-patterns.css.
