---
type: Concept
title: dpBot WebUI Skills Management Reference
description: >
  WebUI skills management — reviewing, installing, enabling, and disabling
  built-in and workspace skills.
tags:
  - nanobot
  - dpbot
  - webui
  - skills
  - marketplace
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:30:00Z
sources:
  - id: docs-webui
    resource: /projects/dpBot/docs/webui.md
    title: WebUI (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# WebUI Skills Management Reference

Open **Skills → Installed** to review built-in and workspace-provided skills.
You can search and filter them, inspect their instructions and setup
requirements, enable or disable them, and delete workspace skills you no
longer want.

## Discovering Skills

Open **Skills → Discover** to browse or search skills from skills.sh and
SkillHub. A marketplace skill is copied into the active agent workspace after
you confirm the installation.

skills.sh installation requires Node.js with `npx`; SkillHub installation
does not.

## Safety

Marketplace skills are third-party instructions and may include executable
scripts. Review the source and instructions before installing one, and enable
only skills you trust with the same files, tools, and credentials available to
your agent.

## Related

- [WebUI Topics](./webui-topics.md) — Topic management
- [WebUI Workspace](./webui-workspace.md) — Workspace and access
- [WebUI Composer](./webui-composer.md) — Composer, mentions
- [WebUI Apps](./webui-apps.md) — Apps management
- [Skills](./skills.md) — Skills system
- [CLI Plugins](./cli-plugins.md) — Plugin CLI commands