---
type: Concept
title: dpBot Architecture
description: >
  Source ownership and architecture overview for dpBot.
tags:
  - nanobot
  - dpbot
  - architecture
  - source-ownership
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:30:00Z
sources:
  - id: docs-concepts
    resource: /projects/dpBot/docs/concepts.md
    title: Concepts (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# Architecture

## Source Ownership

| Area | Source | Maintainer |
|---|---|---|
| Built-in skills | `nanobot/skills/` | nanobot core team |
| Workspace skills | `<workspace>/skills/` | user |
| MCP configuration | `/opt/nanobot-data/config.json` | dpBot admin |
| WebUI | `webui/src/` | dpBot frontend team |
| TUI | `tui/` | dpBot CLI team |
| Documentation | `bundles/` | dpBot docs team |
| Plans and requirements | `.agent/plans/` | dpBot admin |
| OKF bundles | `bundles/` | dpBot docs team |

## Key Paths

- `/projects/dpBot/` — Project root
- `.agent/` — Agent conventions and requirements
- `bundles/` — OKF knowledge bundles
- `docs/` — Source documentation
- `skills/` — Skill definitions

## Related

- [Architecture Runtime Flow](./architecture-runtime.md) — Runtime flow, source ownership, extension points
- [Built-in Skills Catalog](./skills-builtin-catalog.md) — Bundled skills
- [Workspace Skills](./skills-workspace.md) — User-provided skills
- [Skills Marketplace](./skills-marketplace.md) — Marketplace skills
- [WebUI Skills](./webui-skills.md) — Skills management in browser
