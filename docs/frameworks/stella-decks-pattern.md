# Stella Decks Pattern

A pattern for building presentation decks as HTML/CSS code with a three-file harness (CLAUDE.md + DESIGN.md + BRIEF.md), git-versioned, Puppeteer-exported, LLM-iterable. Originated by Ryan Sarver as the [Stella Decks](https://github.com/rsarver/stella-decks) project.

## The core insight

LLMs cannot read PowerPoint, Keynote, or Google Slides — those are proprietary binary formats. But LLMs are *extremely good* at HTML, CSS, and prose, which is literally what a deck is made of: a visual artifact made of code that exists to communicate a narrative.

Build the deck as code and Claude (or any LLM) becomes a competent deck designer; build it in Keynote and you're back to dragging text boxes by hand and watching the model fail to understand what it's looking at.

## The three-file harness

The pattern's architectural choice is the separation of three configuration files. Each has a different scope. The LLM reads all three before touching a slide.

### CLAUDE.md — *Generic, system-level*

Teaches the LLM how the deck-building system itself works: file structure, HTML patterns, manifest conventions, the standard slide component library. No brand opinions, no narrative content. This file stays the same across every deck project that uses this pattern.

### DESIGN.md — *Specific to one brand*

The visual identity codified. Hex values, named Google Fonts, pixel spacing, component visual rules, brand voice. One DESIGN.md per brand — when you build a new deck for the same brand, you reuse the same DESIGN.md.

DESIGN.md is a broader pattern in its own right, documented separately in this toolkit — see [`prompts/design-md-author.md`](../../prompts/design-md-author.md) for how to generate one.

### BRIEF.md — *Specific to one deck*

The narrative anchor. Five things every BRIEF.md should answer:

1. Who is the audience?
2. What do they currently believe?
3. What do you need them to believe (or do) after this deck?
4. What's the ask?
5. What's the constraint — time, format, channel?

This is what turns "a tool that makes slides" into "a tool that thinks about the story."

## File structure

```
your-deck-repo/
  CLAUDE.md                  # System rules (generic)
  DESIGN.md                  # Brand design system
  decks/
    styles/deck.css          # Shared CSS, token-driven
    assets/                  # Shared images
    your-deck/
      BRIEF.md               # Deck-specific narrative
      manifest.json          # ["slide-cover.html", "slide-problem.html", ...]
      slides/
        slide-cover.html
        slide-problem.html
        slide-solution.html
        slide-ask.html
  viewer/index.html          # Browser viewer (keyboard nav, grid)
  scripts/
    export-deck.mjs          # Puppeteer: 2x retina screenshots → PDF
    generate-image.mjs       # Optional: design-aligned image generation
  context/                   # Drop brand materials here (logos, refs)
  archive/                   # Parked slides (move, don't delete)
  exports/                   # Generated PNGs and PDFs
```

Each slide is a standalone HTML file, exactly 1280×720px, linking to `deck.css`. Slides know nothing about each other; the order lives only in `manifest.json`. To reorder, edit the manifest. To A/B test openings, create two manifests pointing at the same slide pool.

## Why HTML over PPTX

**What you gain:**

- `git diff` shows exactly what changed slide-to-slide
- Branch to try a radically different opening without risking the main deck
- Slides become a library to compose from, not a fixed sequence
- One shared design system applies across many decks (Ryan Sarver reports building 8 fundraising decks on one shared design system)
- Browser-based viewer deploys to Vercel for shareable deck URLs

**What you give up:**

- Drag-and-drop visual manipulation
- Real-time multi-user collaboration (git branches cover async collaboration well)
- Slideshow presenter tools (workaround: browser viewer with keyboard nav)

## How it composes with this toolkit

The Stella Decks repo relies on three Claude Code skills. Equivalents are already bundled in this toolkit:

| Stella Decks needs... | This toolkit provides... |
|---|---|
| `/design-setup` — conversational design consultation that produces DESIGN.md | `skills/design-consultation` |
| Narrative review skill — communications-advisor evaluation of the full arc | `skills/design-review` |
| `/gstack` — visual critique with variants | `skills/design-shotgun` |

If you install this toolkit and clone Ryan's stella-decks repo into a project, the skills compose cleanly — same family of patterns.

## Setup

```bash
git clone https://github.com/rsarver/stella-decks
cd stella-decks
# In Claude Code:
#   /design-consultation  → generates DESIGN.md
#   Write BRIEF.md
#   Start with slide-cover.html, then slide-by-slide
```

For the system-prompt version (paste into Claude.ai or ChatGPT/Cursor), see [`prompts/html-deck-author.md`](../../prompts/html-deck-author.md).

## Iteration observation

Ryan Sarver's note from building 8 decks on one shared design system: Claude learns the voice and rhythm of a project as the session progresses. Early slides need more rounds of feedback. By slide 15, first versions are often close to production-ready. This is a natural consequence of the context window accumulating project-specific information — the deck itself becomes part of the context.

## Sister pattern: CLAUDE.md for code behavior

The same architectural idea (one markdown file that constrains LLM behavior across a project) shows up in [andrej-karpathy-skills](https://github.com/sharbel/andrej-karpathy-skills), a CLAUDE.md preset for fixing common LLM coding failures. DESIGN.md is the same shape applied to visual design; karpathy-skills is the same shape applied to code behavior. Both belong in the root of any project where an LLM is doing serious work.

## Credit

Pattern by Ryan Sarver, open-sourced at [github.com/rsarver/stella-decks](https://github.com/rsarver/stella-decks). Distilled into this toolkit reference from public material and Shaurya's wiki notes.
