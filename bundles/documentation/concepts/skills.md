---
type: Concept
title: dpBot Skills
description: >
  The skills system in dpBot — workflow guidance loaded progressively or
  invoked with $skill-name, including built-in, workspace, and marketplace skills.
tags:
  - nanobot
  - dpbot
  - skills
  - workflow
  - guidance
  - marketplace
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

# Skills

Skills are workflow guidance loaded progressively or invoked with
`$skill-name`. They provide structured instructions for specific tasks and
domains.

## Skill Types

### Built-in Skills

Built-in skills live under `nanobot/skills/` in the source tree. They are
packaged with the nanobot distribution and include:

- **image-generation** — Generate and edit images
- **nanobot-document** — Answer nanobot usage, configuration, and troubleshooting questions
- **clawhub** — Search and install agent skills from ClawHub
- **memory** — Search past conversations in history log
- **skill-creator** — Create, update, or package agent skills
- **update-setup** — Set up or reconfigure nanobot's upgrade skill
- **my** — Inspect or troubleshoot runtime state
- **cron** — Schedule reminders and recurring tasks
- **weather** — Get current weather and forecasts

### Workspace Skills

Workspace skills live under `<workspace>/skills/` in the agent workspace.
They are user-provided and can be customized or extended.

### Marketplace Skills

Skills can be discovered and installed from:

- **skills.sh** — Requires Node.js with `npx`
- **SkillHub** — Does not require Node.js

Marketplace skills are third-party instructions and may include executable
scripts. Review the source and instructions before installing one, and enable
only skills you trust with the same files, tools, and credentials available to
your agent.

## Skill Structure

Each skill has a `SKILL.md` file with frontmatter and instructions:

```markdown
---
name: skill-name
description: What this skill does
---

# Skill Name

Instructions for using this skill...
```

## Skill Discovery and Invocation

Skills are discovered from:

1. Built-in skills under `nanobot/skills/`
2. Workspace skills under `<workspace>/skills/`
3. Plugin-provided skills from Agent Plugins

Skills can be invoked with `$skill-name` in conversation.

## WebUI Management

Open **Skills → Installed** to review built-in and workspace-provided skills.
You can search and filter them, inspect their instructions and setup
requirements, enable or disable them, and delete workspace skills you no
longer want.

Open **Skills → Discover** to browse or search skills from skills.sh and
SkillHub. A marketplace skill is copied into the active agent workspace after
you confirm the installation.

## Skill Loading

Skills are loaded progressively — they are available when needed but do not
consume resources until invoked. The skill system integrates with the agent's
context builder to include relevant skill instructions when appropriate.

## Related

- [Skills Built-in](./skills-builtin.md) — Built-in skills overview
- [Skills Marketplace](./skills-marketplace.md) — Marketplace skills
- [WebUI Skills](./webui-skills.md) — Skills management in browser
- [Architecture](./architecture.md) — Source ownership