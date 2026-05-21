# Shaurya Design Toolkit — Design Spec

**Date:** 2026-05-21
**Author:** Shaurya (with Claude)
**Status:** Approved, ready for implementation planning
**Audience:** Matt and Jamie at Manaos (primary); broader public (secondary, since repo is public)

---

> **Editor's note (v0.1):** This document describes the full vision. The v0.1 release ships `skills/` and `prompts/` only — `templates/` is planned for v0.2 (see §3 and §5 for the templates spec, and the project roadmap in README.md). The toolkit's three-folder structure, marketplace integration, and onboarding paths are all live in v0.1.

---

## 1. Purpose

Package Shaurya's design-related Claude skills, system prompts, and ready-to-fork artifacts into a single public GitHub repo that works across **every AI tool Matt and Jamie might use** (Claude Code, Claude.ai, ChatGPT, Cursor) and is also useful to non-AI users who just want polished templates.

The toolkit covers deck-making, HTML/landing-page design, brand systems, video composition (HyperFrames), and the underlying patterns Shaurya uses when generating any of these with AI assistance.

## 2. Source vs scope (what gets drawn from, what gets shipped)

The ask is to extract and package the **design-relevant subset** of Shaurya's setup — skills, system prompts, ready-to-use artifacts. The Obsidian wiki vaults are not the artifact being shared; they're personal reference material on Shaurya's machine that we **draw from during curation** to identify which patterns, tool notes, and skills are worth packaging.

### Source material (lives on Shaurya's machine, not shipped)
- Personal Obsidian knowledge vaults (kept local)
- Shaurya's accumulated patterns, workflows, and design preferences

### Explicit exclusions (skills that exist in Shaurya's setup but don't belong in this toolkit)
- Business-specific custom skills (tied to private client and business work) — not for redistribution
- Personal-account skills (`linkedin`, `notion:*`, `readwise:*`, `telegram:*`) — tied to Shaurya's accounts
- Engineering/ops skills (`gstack`, `gstack-*`, `qa`, `babysit-pr`, `railway:*`, `vercel:*`, `supabase:*`, `sentry:*`) — not design
- Domain-mismatched skills (`legal:*`, `small-business:*`)
- Wiki-management plumbing (`ingest`, `wiki-lint`, `wiki-sort`) — Shaurya's local toolchain

### Project scope (what actually gets shipped)
**Tools + artifacts** — `skills/` + `prompts/` + `templates/`. No `wiki/` folder. The toolkit is a design stack, not a knowledge base.

## 3. Repository structure

```
shaurya-design-toolkit/                 GitHub repo, public, MIT licensed
├── README.md                           Four onboarding paths (see §5)
├── LICENSE                             MIT
├── .claude-plugin/
│   └── plugin.json                     Makes the repo a Claude Code marketplace
├── skills/                             Bundled Claude skills (Claude Code + Claude.ai installable)
│   ├── design-consultation/
│   ├── design-html/
│   ├── design-review/
│   ├── design-shotgun/
│   ├── hyperframes/
│   ├── hyperframes-cli/
│   ├── hyperframes-registry/
│   ├── heygen-skills/
│   ├── make-pdf/
│   ├── defuddle/
│   ├── brand-guidelines/               (generic — not business-specific custom skills)
│   ├── doc-coauthoring/
│   ├── skill-creator/
│   └── gsap/
├── prompts/                            Standalone system prompts for ChatGPT/Cursor/Claude.ai Projects
│   ├── README.md                       How to use these prompts
│   ├── deck-architect.md
│   ├── html-designer.md
│   ├── brand-critic.md
│   ├── visual-reviewer.md
│   ├── video-composer.md
│   └── design-system-thinker.md
├── templates/                          Ready-to-fork artifacts
│   ├── decks/                          .pptx shells
│   │   ├── pitch-deck.pptx
│   │   ├── all-hands.pptx
│   │   ├── customer-deck.pptx
│   │   ├── investor-update.pptx
│   │   └── product-launch.pptx
│   ├── html/                           Tailwind landing-page starters
│   │   ├── hero-plus-features/
│   │   ├── investor-microsite/
│   │   └── product-launch/
│   ├── brand-kit/                      Generic brand-kit template
│   │   ├── colors.json
│   │   ├── typography.md
│   │   └── logo-usage.md
│   └── hyperframes-examples/           Working HyperFrames compositions
│       ├── intro-title-card/
│       ├── audio-reactive-demo/
│       └── caption-overlay-example/
└── docs/
    ├── how-to-add-a-skill.md
    └── architecture.md                 This spec (mirrored here for repo discoverability)
```

### Design choices

- **Three top-level content folders** (`skills/`, `prompts/`, `templates/`) — each serves a different consumption mode. No `wiki/`.
- **`.claude-plugin/plugin.json` at repo root** is the single file that makes the same repo function as a Claude Code marketplace. Skills in `skills/` are installable natively; the same folder is browsable on Claude.ai's Skills page and on GitHub. Three consumption modes from one source tree.
- **Templates are artifact-based, not skill-based** — `.pptx` and HTML files Matt/Jamie can open and edit without invoking anything. This is the highest-leverage piece for non-technical use.

## 4. Curation policy

### Skills — bundled vs linked

**Bundled** (~10–14 skills, final count decided at implementation time): Skills that meet **all three** of these criteria are bundled:
1. Shaurya has the right to redistribute (skill is his own work, or its license explicitly permits redistribution — MIT, Apache 2.0, CC-BY, public domain, etc.)
2. No canonical public marketplace already hosts it
3. The skill is design / deck / video / brand related (matches toolkit scope)

The §3 skills list is the initial proposal — each skill is re-checked against these criteria during implementation. Borderline cases (`skill-creator`, `doc-coauthoring`, `brand-guidelines`) get evaluated at that point and moved to the linked list if an Anthropic-official version exists.

**Linked from README, not bundled**: skills with a clean public marketplace home. README points users to install them separately:
- Anthropic official: `pptx`, `docx`, `xlsx`, `pdf`, `theme-factory`, `canvas-design`, `algorithmic-art`, `slack-gif-creator`
- Design family: `design:design-critique`, `design:design-system`, `design:ux-copy`, `design:accessibility-review`

**Bundling principle**: prefer linking when an official source exists; bundle when the skill is Shaurya's customization, an extension of an existing tool (e.g., `make-pdf` vs the generic `pdf`), or has no public canonical home.

### Prompts

~6 distilled system prompts extracted from skills that have a clear "act as X" pattern. Each ~200–400 words, ready to paste into any tool's custom-instructions or system-prompt field. Examples: deck-architect, html-designer, brand-critic, visual-reviewer, video-composer, design-system-thinker.

### Templates

Concrete artifact counts for v0.1: 5 deck shells, 3 HTML starters, 1 brand-kit template, 3 HyperFrames examples. Sourced from Shaurya's existing work, scrubbed of private client/business branding before publication.

## 5. README onboarding paths

The README routes users by setup before exposing structure. Four self-contained paths:

### Path 1 — Claude Code users
```
claude plugin marketplace add github:shaurya/shaurya-design-toolkit
claude plugin install design-toolkit
```
First-artifact target: ~30 seconds. They get all bundled skills natively.

### Path 2 — Claude.ai users
1. Open claude.ai → Settings → Skills → Add skills
2. Add marketplace URL: `github.com/shaurya/shaurya-design-toolkit`
3. Browse and add the skills they want individually
4. For system prompts: paste `prompts/*.md` into a Claude Project's custom instructions

### Path 3 — ChatGPT / Cursor / other tools
1. Browse `prompts/` on GitHub
2. Pick the prompt matching the task
3. Paste as system prompt / custom instructions
4. Templates in `templates/` work in any tool (PPTX, HTML, JSON files)

### Path 4 — Non-AI users
Skip the skills entirely. Go straight to `templates/`:
- `templates/decks/` — open in PowerPoint/Keynote/Google Slides
- `templates/html/` — clone, edit content, deploy to Vercel/Netlify
- `templates/brand-kit/` — colors, typography, logo-usage reference

### README header
```
# Shaurya Design Toolkit
Decks, HTML, video, brand — Shaurya's design stack, originally packaged for the Manaos team,
open-sourced for anyone making things look good with AI assistance.

→ Find your setup below. Each path: ~2 minutes to first working artifact.
```

## 6. Maintenance & lifecycle

### Update propagation
- **Claude Code**: `claude plugin update design-toolkit` after a push
- **Claude.ai**: marketplace re-fetches on a schedule; new skills auto-appear
- **ChatGPT/Cursor**: `git pull` if cloned, or re-visit GitHub
- **Template users**: re-download specific files

### Versioning
- Semver on `.claude-plugin/plugin.json` (`version` field)
- Patch for fixes, minor for new skills/templates, major for breaking renames
- Repo git tags match plugin.json versions (`v0.1.0`, `v0.2.0`, etc.) so users can pin

### Adding new content (Shaurya solo, default mode)
1. Drop new skill into `skills/<name>/` following Anthropic's SKILL.md format
2. Or add template to `templates/<category>/`
3. Update README's skill list
4. Bump `plugin.json` version
5. Git push, tag the release

### Community contributions (optional, deferred)
- Start with PR-only review flow
- If Matt/Jamie are actively contributing, open a `community/` folder for skills outside the auto-installed marketplace
- No CI / no test suite / no CONTRIBUTING.md in v0.1 — the audience is two trusted people. Add process only if usage grows beyond that.

### Deprecation
- Skill deprecated → keep folder, add `deprecated: true` in frontmatter. Marketplace stops surfacing; old installs keep working.
- Template replaced → move old to `templates/<category>/_archive/`, new takes the canonical filename.
- Skill renamed → leave a redirect stub for one minor version, then remove.

## 7. Privacy & hygiene (one-time launch pass)

Before the v0.1 push to public GitHub, scrub everything bundled for:
- Client and business names (any private or named-client identifiers)
- Personal-business-specific branding, NDA language, proposal templates
- Personal handles, email addresses, internal URLs
- API keys, tokens, credentials (defensive: even though none should exist)
- References to Shaurya's private knowledge vaults, internal database IDs, memory system IDs

This is a single review pass before v0.1, not ongoing work. Future skills authored cleanly from the start don't need re-scrubbing.

## 8. Success criteria

v0.1 is successful when:
1. Matt and Jamie can each install the toolkit in their preferred environment in under 2 minutes
2. They each produce at least one usable artifact (deck, landing page, or video segment) using a bundled skill or template within the first week
3. The repo's README is comprehensible to a stranger landing on the GitHub page cold
4. Nothing client-confidential or personally-identifying is exposed in the public repo

Long-term success (v0.3+) is measured by:
- Whether Matt or Jamie has submitted at least one PR adding their own skill or improving a template
- Whether the toolkit shows up unprompted in Shaurya's portfolio / external conversations as a piece of public work

## 9. Open questions deferred to implementation

- **Exact list of templates to ship in v0.1** — depends on which existing decks/HTML files Shaurya has that can be scrubbed and templatized. Discovery happens during implementation.
- **Whether to write the 6 prompts from scratch or extract from skill READMEs** — extract-and-edit is faster; from-scratch is cleaner. Default to extract-and-edit unless a skill's prompt logic is too tangled with the skill's tooling.
- **HyperFrames examples** — need to pick 3 representative compositions from Shaurya's existing work. Implementation-time decision.

## 10. Non-goals

- Shipping a knowledge base (`wiki/`) — out of scope from the start; Shaurya's wiki vaults stay local as reference material
- Replicating Anthropic's official skills — link, don't duplicate
- Building CI, tests, or contribution infrastructure — premature for a 2-person audience
- Auto-syncing updates with users' local installs without their action — marketplace-update is a deliberate command, not background sync
- Including any client-specific or business-specific content — full exclusion list in §2
