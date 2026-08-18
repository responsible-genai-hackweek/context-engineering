# Context Engineering

UW-branded presentation using a two-pass, fragment-based architecture.

## Pass 1 — Content and structure

1. Edit `SLIDES.md` to plan your presentation
2. Request slides through conversation (LLM reads SLIDES.md, writes to `content/`)
3. Build: `./build.sh`
4. Preview: `open build/index.html`
5. Rehearse and revise — repeat until content is settled

## Pass 2 — Visual additions

1. Edit `VISUALS.md` to specify photographs, diagrammatic accents, and icons
2. Run `/uw-slides:apply-visuals` (LLM reads VISUALS.md, writes to `content-with-visuals/`)
3. Build: `./build-visuals.sh`
4. Preview: `open build/index-with-visuals.html`

## Reordering Slides

Edit the `## slide-id` order in `SLIDES.md`, then rebuild with `./build.sh`.

## Structure

- `SLIDES.md` — Pass-1 planning document (slide order + content briefs)
- `VISUALS.md` — Pass-2 visual additions specification
- `content/` — Pass-1 HTML fragments (source of truth; never modified by pass 2)
- `content-with-visuals/` — Pass-2 HTML fragments (only slides that received additions)
- `shared/` — Header and footer templates
- `build/` — Generated presentations (git-ignored)
- `assets/` — Images, diagrams, and fonts
