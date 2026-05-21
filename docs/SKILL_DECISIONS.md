# Skill Bundling Decisions — v0.1

For each candidate skill from spec §3, this document records the source, license, and bundle-vs-link decision. Researched on 2026-05-21.

## Decision matrix

| Skill | Origin | License | Decision |
|---|---|---|---|
| design-consultation | gstack (Garry Tan) | MIT | bundle |
| design-html | gstack (Garry Tan) | MIT | bundle |
| design-review | gstack (Garry Tan) | MIT | bundle |
| design-shotgun | gstack (Garry Tan) | MIT | bundle |
| hyperframes | standalone — no parent plugin.json | unclear | deferred |
| hyperframes-cli | standalone — same origin as hyperframes | unclear | deferred |
| hyperframes-registry | standalone — same origin as hyperframes | unclear | deferred |
| heygen-skills | heygen-com/skills (GitHub) | MIT | bundle |
| make-pdf | gstack (Garry Tan) | MIT | bundle |
| defuddle | standalone — wraps `defuddle` npm CLI | unclear | deferred |
| brand-guidelines | Anthropic (claude-plugins-official) | Apache 2.0 | link |
| doc-coauthoring | Anthropic (official plugin registry) | unclear locally | link |
| skill-creator | Anthropic (claude-plugins-official) | Apache 2.0 | link |
| gsap | companion to hyperframes cluster | unclear | deferred |

### Source paths (full detail)

- **design-consultation** — `~/.claude/skills/design-consultation/` (installed from `~/.claude/skills/gstack/design/design-consultation/`); MIT at `~/.claude/skills/gstack/LICENSE`
- **design-html** — `~/.claude/skills/design-html/` (from `gstack/design/design-html/`)
- **design-review** — `~/.claude/skills/design-review/` (from `gstack/design/design-review/`)
- **design-shotgun** — `~/.claude/skills/design-shotgun/` (from `gstack/design/design-shotgun/`)
- **heygen-skills** — `~/.claude/skills/heygen-skills/`; MIT at `~/.claude/skills/heygen-skills/LICENSE`; confirmed `github.com/heygen-com/skills`
- **make-pdf** — `~/.claude/skills/make-pdf/` (from `gstack/make-pdf/`)
- **brand-guidelines** — `~/.claude/skills/brand-guidelines/`; Apache 2.0 at `~/.claude/skills/brand-guidelines/LICENSE.txt`
- **skill-creator** — `~/.claude/plugins/cache/claude-plugins-official/skill-creator/unknown/`; Apache 2.0 at that path's `LICENSE`
- **hyperframes / hyperframes-cli / hyperframes-registry / gsap** — `~/.claude/skills/{skill-name}/`; no LICENSE file in any of these dirs

## Skills bundled in v0.1

- **design-consultation** — gstack MIT (Garry Tan)
- **design-html** — gstack MIT (Garry Tan)
- **design-review** — gstack MIT (Garry Tan)
- **design-shotgun** — gstack MIT (Garry Tan)
- **heygen-skills** — heygen-com MIT
- **make-pdf** — gstack MIT (Garry Tan)

## Skills linked from README (not bundled)

**Anthropic-official (available via official plugin, prefer not to duplicate):**
- **brand-guidelines** — `anthropic-skills:brand-guidelines` (Apache 2.0, Anthropic)
- **doc-coauthoring** — `anthropic-skills:doc-coauthoring` (Anthropic)
- **skill-creator** — `anthropic-skills:skill-creator` (Apache 2.0, Anthropic)

## Skills deferred (license unclear; revisit in v0.2)

> **v0.2 target.** Owner: Shaurya. Blocker on each: upstream LICENSE confirmation.

- **hyperframes** — no LICENSE file. The skill uses `npx hyperframes` and references the `@hyperframes/*` npm scope (e.g., `@hyperframes/shader-transitions`). **Suggested upstream**: `github.com/hyperframes` org or search npm for `@hyperframes/core`. **Next step**: open the npm page for `hyperframes` (https://www.npmjs.com/package/hyperframes), follow the repository link, and check for a LICENSE file there.
- **hyperframes-cli** — no LICENSE file; same provenance and install date (2026-04-26) as hyperframes. **Suggested upstream**: same as hyperframes above — the CLI is likely in the same monorepo. **Next step**: resolve hyperframes upstream first; this is the same repo.
- **hyperframes-registry** — no LICENSE file; same origin as the hyperframes cluster. **Suggested upstream**: same hyperframes monorepo. **Next step**: resolve together with hyperframes and hyperframes-cli.
- **defuddle** — no LICENSE file; single SKILL.md wrapper for the `defuddle` npm CLI tool. **Suggested upstream**: `github.com/kepano/defuddle` (Steph Ango / Obsidian's defuddle package, which has an MIT license). **Next step**: confirm the skill's SKILL.md content is derived from that repo, then verify LICENSE applies to skill redistribution; if yes, can likely upgrade to "bundle".
- **gsap** — no LICENSE file; companion skill to hyperframes (the hyperframes SKILL.md loads GSAP via CDN). The skill documents the GSAP API (GreenSock). **Suggested upstream**: `github.com/greensock/GSAP` — GSAP itself is Apache 2.0 for non-commercial use; GreenSock has a custom "No Charge" license for most uses. **Next step**: confirm whether the skill file is original content (in which case, check who authored it) or derivative of GSAP docs (in which case, check GreenSock's content license). If it was authored as part of the hyperframes cluster, resolve with that upstream.

## Judgment call notes

1. **gstack MIT coverage**: The `~/.claude/skills/gstack/` directory is the canonical gstack monorepo with an MIT License at its root (Copyright © 2026 Garry Tan). The subskills (design-consultation, design-html, design-review, design-shotgun, make-pdf) are subdirectories of that monorepo installed as copies to `~/.claude/skills/`. They carry no standalone LICENSE files, but the MIT license at the monorepo root covers all content within it. This was treated as sufficient for bundling. If you want belt-and-suspenders certainty, copy the gstack LICENSE file alongside each bundled skill.

2. **heygen-skills**: Has an explicit MIT LICENSE file signed by HeyGen (not a third party), and the CHANGELOG confirms it lives at `github.com/heygen-com/skills`. This is the most clearly licensable skill in the set.

3. **hyperframes cluster + gsap**: Installed on the same date (2026-04-26) with no LICENSE files anywhere in the skill directories or any discoverable parent plugin.json. These are treated as deferred rather than missing — the skills exist and are high-value, but redistribution rights are not established. Resolution path: find the upstream GitHub repo via the `@hyperframes` npm scope and check its license.

4. **brand-guidelines Apache 2.0**: The license permits redistribution, but `anthropic-skills:brand-guidelines` is the official channel. Bundling a copy would create a maintenance fork of Anthropic's brand assets. Linking is both legally and practically cleaner.

## Summary

- Bundle count: **6**
- Link count: **3**
- Deferred count: **5**
- All 14 candidates found on disk; none missing.
