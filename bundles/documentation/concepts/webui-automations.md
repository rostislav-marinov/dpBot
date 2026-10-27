---
type: Concept
title: dpBot WebUI Automations View
description: >
  WebUI Automations view — reviewing, searching, running, pausing, editing,
  and deleting scheduled and local-trigger agent turns.
tags:
  - nanobot
  - dpbot
  - webui
  - automations
  - cron
  - triggers
  - heartbeat
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

# WebUI Automations View

Open **Automations** to review, search, run, pause, edit, and delete scheduled
and local-trigger agent turns.

## Features

- Filter by all, active, paused, needs-attention, or system jobs
- Search by task name, message, trigger command, linked topic, schedule, or
  status
- Sort by next run, last run, updated time, or name
- Run scheduled automations now
- Pause/resume, rename, or delete user-created automations
- Copy the CLI command for local triggers
- Inspect protected system automations without changing them

## Search

Search accepts plain text and field filters such as `name:backup`,
`chat:WeChat`, `schedule:09:30`, `cron:"0 23 * * *"`, `trigger`, and
`status:paused`.

## Limitations

- An automation without a linked topic cannot be enabled or run from the
  WebUI, because nanobot would not know where to deliver the scheduled turn
- Local triggers do not have a WebUI "Run now" action because each run needs
  a message. Use the copied `nanobot trigger ...` command and replace
  `"message"` with the content that should be delivered

## Related

- [WebUI Topics](./webui-topics.md) — Topic management
- [WebUI Workspace](./webui-workspace.md) — Workspace and access
- [WebUI Composer](./webui-composer.md) — Composer, mentions
- [Automations](./automations-scheduled.md) — Automations, cron, heartbeat, triggers
- [CLI Channels](./cli-channels.md) — Channel CLI commands