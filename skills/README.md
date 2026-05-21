# Skills

Claude Code skills installable via the `shaurya-design-toolkit` marketplace. Each subfolder is a self-contained skill with its own `SKILL.md` and `LICENSE`.

## What's here

| Skill | What it does | Origin |
|---|---|---|
| [`design-consultation`](./design-consultation/) | Brand and design-system discovery; generates DESIGN.md | gstack (MIT) |
| [`design-html`](./design-html/) | HTML/Tailwind landing page generation | gstack (MIT) |
| [`design-review`](./design-review/) | Visual QA — finds inconsistencies, AI-slop patterns | gstack (MIT) |
| [`design-shotgun`](./design-shotgun/) | Generates multiple design variants for side-by-side comparison | gstack (MIT) |
| [`make-pdf`](./make-pdf/) | Markdown → publication-quality PDF with proper margins, page breaks, TOC | gstack (MIT) |
| [`heygen-skills`](./heygen-skills/) | HeyGen avatar video generation (api.heygen.com) | HeyGen (MIT) |

## Installing

```bash
claude plugin marketplace add github:shrchauhan97/shaurya-design-toolkit
claude plugin install shaurya-design-toolkit
```

After install, each skill is invokable in Claude Code by name (e.g., `/design-html`, `/make-pdf`).

## Using outside Claude Code

These skills are designed for Claude Code's `/skill-name` invocation pattern. For ChatGPT, Cursor, or other tools, the equivalent patterns live in [`../prompts/`](../prompts/) as standalone system prompts.

## Adding your own

See [`../docs/how-to-add-a-skill.md`](../docs/how-to-add-a-skill.md).

## Roadmap

v0.2 will likely add: `hyperframes`, `hyperframes-cli`, `defuddle`, `gsap` (currently deferred pending license confirmation — see [`../docs/SKILL_DECISIONS.md`](../docs/SKILL_DECISIONS.md)).
