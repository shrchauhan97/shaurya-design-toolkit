# Shaurya Design Toolkit

Decks, HTML, video, brand — Shaurya's design stack, originally packaged for the Manaos team, open-sourced for anyone making things look good with AI assistance.

→ Find your setup below. Each path: ~2 minutes to first working artifact.

---

## Path 1 — I use Claude Code

```bash
# One-time setup
claude plugin marketplace add github:shrchauhan97/shaurya-design-toolkit
claude plugin install shaurya-design-toolkit

# Try it
/design-html "build me a hero section for a B2B SaaS landing page"
```

You now have access to all bundled skills natively in Claude Code. Browse [`skills/`](./skills/) in this repo to see what's available.

## Path 2 — I use Claude.ai

1. Open claude.ai → Settings → Skills → Add skills
2. Add marketplace URL: `github.com/shrchauhan97/shaurya-design-toolkit`
3. Browse and add the skills you want individually

For system prompts: create a Claude Project, paste any file from [`prompts/`](./prompts/) into the project's custom instructions.

## Path 3 — I use ChatGPT, Cursor, or anything else

You won't get the skills natively, but the patterns work anywhere:

1. Browse [`prompts/`](./prompts/) in this repo
2. Pick the prompt matching your task (`deck-architect.md`, `html-designer.md`, etc.)
3. Copy everything below the `---` divider in that file
4. Paste it as your system prompt / custom instructions in your tool of choice

---

## What's bundled

**Skills** (in [`skills/`](./skills/)) — 6 design-focused skills usable in Claude Code:
- `design-consultation`, `design-html`, `design-review`, `design-shotgun` — deck and visual design workflows
- `make-pdf` — markdown → publication-quality PDF
- `heygen-skills` — HeyGen avatar videos

**Prompts** (in [`prompts/`](./prompts/)) — 8 distilled system prompts for use anywhere:
- `deck-architect` — pitch decks, all-hands, customer-facing
- `html-designer` — landing pages, microsites, hero sections
- `brand-critic` — reviewing visual work against brand consistency
- `visual-reviewer` — catching AI-slop patterns, spacing, hierarchy
- `video-composer` — composition, transitions, captions, motion
- `design-system-thinker` — color, type, spacing systems
- `design-md-author` — generating a `DESIGN.md` file for AI coding agents *(v0.2)*
- `html-deck-author` — authoring HTML/CSS decks using the Stella Decks pattern *(v0.2)*

**Reference docs** (in [`docs/`](./docs/)):
- [`docs/frameworks/stella-decks-pattern.md`](./docs/frameworks/stella-decks-pattern.md) — full architecture of the HTML/CSS deck pattern *(v0.2)*
- [`docs/landscapes/ui-effects-libraries.md`](./docs/landscapes/ui-effects-libraries.md) — curated GitHub repos for 3D, liquid, gradient UI effects *(v0.2)*
- [`docs/SKILL_DECISIONS.md`](./docs/SKILL_DECISIONS.md), [`docs/architecture.md`](./docs/architecture.md), [`docs/how-to-add-a-skill.md`](./docs/how-to-add-a-skill.md)

## Recommended companions (not bundled — install from Anthropic's marketplace)

These skills aren't bundled here because Anthropic publishes them officially. Install separately:

- **Document formats**: `pptx`, `docx`, `xlsx`, `pdf`
- **Visual**: `theme-factory`, `canvas-design`, `algorithmic-art`
- **Misc**: `slack-gif-creator`, `doc-coauthoring`, `skill-creator`, `brand-guidelines`

## Adding your own skills

See [`docs/how-to-add-a-skill.md`](./docs/how-to-add-a-skill.md).

## Roadmap

- **v0.1** — skills + prompts (shipped)
- **v0.2** (current) — DESIGN.md pattern, UI effects library, Stella Decks reference
- **v0.3** — templates (deck shells, HTML starters, brand-kit reference)
- **v0.4+** — community contributions, additional prompts

## License

MIT. See [`LICENSE`](./LICENSE).
