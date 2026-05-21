# Skill Bundling Decisions — v0.1

For each candidate skill from spec §3, this document records the source, license, and bundle-vs-link decision. Researched on 2026-05-21.

## Decision matrix

| Skill | Source location | Parent plugin / origin | License | Decision | Notes |
|---|---|---|---|---|---|
| design-consultation | `~/.claude/skills/design-consultation/` (real dir, installed from `~/.claude/skills/gstack/design/design-consultation/`) | gstack (Garry Tan) | MIT (Copyright © 2026 Garry Tan, `~/.claude/skills/gstack/LICENSE`) | bundle | Subskill of gstack monorepo; MIT license applies to all content in that repo. No Anthropic-official equivalent. |
| design-html | `~/.claude/skills/design-html/` (installed from `~/.claude/skills/gstack/design/design-html/`) | gstack (Garry Tan) | MIT (Copyright © 2026 Garry Tan) | bundle | Same MIT provenance as design-consultation. |
| design-review | `~/.claude/skills/design-review/` (installed from `~/.claude/skills/gstack/design/design-review/`) | gstack (Garry Tan) | MIT (Copyright © 2026 Garry Tan) | bundle | Same MIT provenance as design-consultation. |
| design-shotgun | `~/.claude/skills/design-shotgun/` (installed from `~/.claude/skills/gstack/design/design-shotgun/`) | gstack (Garry Tan) | MIT (Copyright © 2026 Garry Tan) | bundle | Same MIT provenance as design-consultation. |
| hyperframes | `~/.claude/skills/hyperframes/` | standalone (installed 2026-04-26, no parent plugin.json found) | unclear — no LICENSE file present | deferred | No LICENSE file in skill dir or any discoverable parent. Cannot confirm redistribution rights without contacting author. |
| hyperframes-cli | `~/.claude/skills/hyperframes-cli/` | standalone (installed 2026-04-26, same origin as hyperframes) | unclear — no LICENSE file present | deferred | Same license gap as hyperframes; both were installed together on the same date. |
| hyperframes-registry | `~/.claude/skills/hyperframes-registry/` | standalone (installed 2026-04-26, same origin as hyperframes) | unclear — no LICENSE file present | deferred | Same license gap as hyperframes; all three hyperframes skills share the same origin and install date. |
| heygen-skills | `~/.claude/skills/heygen-skills/` | heygen-com/skills GitHub repo (CHANGELOG + CODEOWNERS confirm `github.com/heygen-com/skills`) | MIT (Copyright © 2026 HeyGen, `~/.claude/skills/heygen-skills/LICENSE`) | bundle | Explicit MIT LICENSE file. Vendor-published open skill; no Anthropic-official equivalent. |
| make-pdf | `~/.claude/skills/make-pdf/` (installed from `~/.claude/skills/gstack/make-pdf/`) | gstack (Garry Tan) | MIT (Copyright © 2026 Garry Tan) | bundle | Subskill of gstack monorepo; MIT license confirmed. No Anthropic-official equivalent. |
| defuddle | `~/.claude/skills/defuddle/` | standalone (installed 2026-04-10, no parent plugin.json) | unclear — no LICENSE file present | deferred | Single-file SKILL.md with no license declaration. Wraps the `defuddle` npm CLI tool but skill content has no stated license. |
| brand-guidelines | `~/.claude/skills/brand-guidelines/` | Anthropic (description says "Applies Anthropic's official brand colors"; LICENSE.txt is Apache 2.0) | Apache 2.0 (`~/.claude/skills/brand-guidelines/LICENSE.txt`) | link | `anthropic-skills:brand-guidelines` exists as official Anthropic plugin. Prefer the official channel over bundling our local copy. |
| doc-coauthoring | `~/.claude/skills/doc-coauthoring/` | Anthropic (no LICENSE file; `anthropic-skills:doc-coauthoring` is in official plugin registry) | unclear locally — no LICENSE file | link | `anthropic-skills:doc-coauthoring` is available via official Anthropic plugin. Default to link per rule for Anthropic-official names, regardless of local license status. |
| skill-creator | `~/.claude/skills/skill-creator/` (empty dir; canonical copy at `~/.claude/plugins/cache/claude-plugins-official/skill-creator/unknown/`) | Anthropic (claude-plugins-official plugin cache) | Apache 2.0 (`plugins/cache/claude-plugins-official/skill-creator/unknown/LICENSE`) | link | `anthropic-skills:skill-creator` is the official Anthropic version. Local skills/ dir is empty. Default to link. |
| gsap | `~/.claude/skills/gsap/` | companion skill to hyperframes (installed 2026-04-26, same date as hyperframes cluster) | unclear — no LICENSE file present | deferred | No LICENSE file. Closely coupled to hyperframes (referenced throughout hyperframes/SKILL.md); deferring with the hyperframes cluster until that license is resolved. |

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

- **hyperframes** — no LICENSE file; contact author or locate upstream repo to confirm redistribution rights
- **hyperframes-cli** — no LICENSE file; same provenance as hyperframes
- **hyperframes-registry** — no LICENSE file; same provenance as hyperframes
- **defuddle** — no LICENSE file; single SKILL.md wrapper for the defuddle npm CLI; needs author clarification
- **gsap** — no LICENSE file; companion to hyperframes cluster, deferring together

## Skills missing on disk

(none — all 14 candidates were found on disk)

## Judgment call notes

1. **gstack MIT coverage**: The `~/.claude/skills/gstack/` directory is the canonical gstack monorepo with an MIT License at its root (Copyright © 2026 Garry Tan). The subskills (design-consultation, design-html, design-review, design-shotgun, make-pdf) are subdirectories of that monorepo installed as copies to `~/.claude/skills/`. They carry no standalone LICENSE files, but the MIT license at the monorepo root covers all content within it. This was treated as sufficient for bundling. If you want belt-and-suspenders certainty, copy the gstack LICENSE file alongside each bundled skill.

2. **heygen-skills**: Has an explicit MIT LICENSE file signed by HeyGen (not a third party), and the CHANGELOG confirms it lives at `github.com/heygen-com/skills`. This is the most clearly licensable skill in the set.

3. **hyperframes cluster + gsap**: Installed on the same date (2026-04-26) with no LICENSE files anywhere in the skill directories or any discoverable parent plugin.json. These are treated as deferred rather than missing — the skills exist and are high-value, but redistribution rights are not established. Resolution path: find the upstream GitHub repo (likely `@hyperframes/core` or similar) and check its license.

4. **brand-guidelines Apache 2.0**: The license permits redistribution, but `anthropic-skills:brand-guidelines` is the official channel. Bundling a copy would create a maintenance fork of Anthropic's brand assets. Linking is both legally and practically cleaner.

## Summary

- Bundle count: **6**
- Link count: **3**
- Deferred count: **5**
- Missing count: **0**
