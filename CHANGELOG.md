# Changelog

All notable changes to the Shaurya Design Toolkit are documented here. Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versioning follows [SemVer](https://semver.org/).

## [0.2.0] — 2026-05-21

Differentiated additions distilled from the wiki. Pointer-only (no upstream code redistribution); all three additions credit and link to source.

### Added

- **`prompts/design-md-author.md`** — System prompt for generating `DESIGN.md` files. Codifies the eight required sections (brand identity, color, typography, spacing, components, visual rules, brand voice, references) so AI coding agents can apply a brand's design system instead of guessing. Pattern by Noah ([@noohelhadedy](https://twitter.com/noohelhadedy)); reference repo: [Awesome DESIGN.md](https://github.com/VoltAgent/awesome-design-md).
- **`prompts/html-deck-author.md`** — System prompt for building HTML/CSS presentation decks using the Stella Decks three-file harness (CLAUDE.md + DESIGN.md + BRIEF.md). Pattern by Ryan Sarver; upstream at [github.com/rsarver/stella-decks](https://github.com/rsarver/stella-decks).
- **`docs/frameworks/stella-decks-pattern.md`** — Full architectural reference for the Stella Decks pattern: three-file harness rationale, repo structure, why HTML beats PPTX for LLM workflows, how it composes with this toolkit's existing skills.
- **`docs/landscapes/ui-effects-libraries.md`** — Curated reference for four free GitHub repos delivering production-grade UI effects: ShaderGradient, liquid-logo, liquid-glass-js, react-three-fiber. Each entry includes use cases, gotchas, and license notes.

### Changed

- `README.md` — Prompts table now lists 8 entries (was 6). New "Reference docs" section points to `docs/frameworks/` and `docs/landscapes/`. Roadmap updated to reflect v0.2 contents.
- `prompts/README.md` — Added entries for `design-md-author` and `html-deck-author`.
- `.claude-plugin/plugin.json` and `.claude-plugin/marketplace.json` — Version `0.1.0` → `0.2.0`.

### Notes

- All v0.2 additions are pointer-only — no upstream code (Stella Decks files, UI effects repos, DESIGN.md generator implementations) is redistributed. Patterns are taught and sources are linked.
- Skills bundle (`skills/`) is unchanged from v0.1.

## [0.1.0] — 2026-05-21

Initial public release.

### Added

- 6 bundled skills: `design-consultation`, `design-html`, `design-review`, `design-shotgun`, `make-pdf`, `heygen-skills`.
- 6 distilled system prompts: `deck-architect`, `html-designer`, `brand-critic`, `visual-reviewer`, `video-composer`, `design-system-thinker`.
- `README.md` with three onboarding paths (Claude Code, Claude.ai, ChatGPT/Cursor).
- `docs/SKILL_DECISIONS.md`, `docs/architecture.md`, `docs/how-to-add-a-skill.md`.
- `.claude-plugin/plugin.json` and `.claude-plugin/marketplace.json` for plugin installation.
- MIT license.
