# How to add a skill

A skill is a folder under `skills/` containing a `SKILL.md` (the skill's manifest) and any supporting files.

## Minimum viable skill

```
skills/<your-skill-name>/
└── SKILL.md
```

`SKILL.md` needs frontmatter:

```markdown
---
name: your-skill-name
description: One-sentence description of what triggers this skill.
---

# What this skill does

The body of the skill — instructions, examples, decision flow.
```

## Adding to the marketplace

After dropping in your skill folder:

1. Bump `version` in `.claude-plugin/plugin.json` (patch for additions, minor for new categories)
2. Add a line to README's "What's bundled" section (if you want it discoverable)
3. Commit and push

Users running `claude plugin update shaurya-design-toolkit` will pull your skill on next refresh.

## Conventions

- **Hygiene**: don't include client names, account-tied credentials, or personally-identifying content. The repo is public.
- **Licensing**: only bundle skills you have the right to redistribute. If unsure, link from README instead.
- **Scope**: skills in this toolkit are design-adjacent (decks, HTML, video, brand). Off-topic skills don't belong here.

## Pull requests

External contributions welcome via PR. Review turnaround: best-effort, no SLA.
