---
type: Concept
title: dpBot WebUI Workspace and Access Reference
description: >
  WebUI workspace picker — project selection, workspace vs agent workspace,
  and access control modes.
tags:
  - nanobot
  - dpbot
  - webui
  - workspace
  - project
  - access-control
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

# WebUI Workspace and Access Reference

Use the workspace picker to browse folders on the connected dpBot host, enter
an absolute path, or return to recent and starred projects.

## Project vs Agent Workspace

Selecting a project does not replace the configured agent workspace:

| Selected project provides | Agent workspace continues to provide |
|---|---|
| Project `AGENTS.md` | `SOUL.md` and `USER.md` |
| Relative file paths and shell working directory | Long-term memory and history |
| Normal read/write boundary in Restricted mode | Custom skills and instance state |

A new topic separates conversation history; a project selection changes the
file working directory. Neither creates a separate long-term memory store.
Project switching can therefore carry preferences and facts learned in other
topics into the new project.

Project-local `SOUL.md` and `USER.md` files are ignored, and the agent
workspace's `AGENTS.md` is not inherited by a separately selected project.
When the selected project is the configured agent workspace, both roles
naturally use the same directory.

## Access Control

The access control in the composer controls the local capability level for
the chat. It does not bypass your gateway, provider, shell sandbox, or
operating system configuration; it only selects among the capabilities that
are already available to the current topic.

### Restricted Mode

Ordinary file and shell work stays inside the selected project. To preserve
agent continuity, filesystem/search tools receive narrow, read-only access to
built-in skills, custom skills in the agent workspace, and the exact agent
`memory/history.jsonl` file. This does not grant access to neighboring memory
or profile files, and it does not allow writes outside the selected project.
These tool exceptions do not broaden the browser's file preview boundary.

### Full Access

Can preview files outside the workspace when allowed by the gateway.

## Related

- [WebUI Topics](./webui-topics.md) — Topic management
- [WebUI Temporary](./webui-temporary.md) — Temporary chats
- [WebUI Composer](./webui-composer.md) — Composer, mentions
- [Configuration](./configuration.md) — Workspace settings
- [Security](./security.md) — Security boundaries