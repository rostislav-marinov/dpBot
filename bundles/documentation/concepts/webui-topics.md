---
type: Concept
title: dpBot WebUI Topics and Panes
description: >
  WebUI topic management — persistent topics, conversation groups, panes,
  and topic workspace.
tags:
  - nanobot
  - dpbot
  - webui
  - topics
  - panes
  - conversation-groups
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

# WebUI Topics and Panes

The WebUI sidebar is the topic switcher. Each topic keeps its own history,
title, workspace selection, and linked automations.

## Conversation Groups and Panes

- Open a topic's sidebar action menu and choose **Create group** to turn it
  into a conversation group
- Use **Add pane** in the workbench header to start another topic alongside it
- A group holds up to four panes
- Use **Pane layout** to choose columns, rows, a grid, BSP, or a main pane
  with a stack
- Drag a divider to resize panes
- Group membership and layout persist across refreshes

## Related

- [WebUI Activity](./webui-activity.md) — Activity, context usage, model failures
- [WebUI Temporary](./webui-temporary.md) — Temporary chats
- [WebUI Workspace](./webui-workspace.md) — Workspace picker, access control
- [WebUI Composer](./webui-composer.md) — Composer, mentions
- [CLI WebUI](./cli-webui.md) — WebUI CLI commands
- [Configuration](./configuration.md) — Config file and schema