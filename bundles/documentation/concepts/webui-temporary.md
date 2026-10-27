---
type: Concept
title: dpBot WebUI Temporary Chats
description: >
  WebUI temporary chats — conversations that are not added to topic history
  or long-term memory.
tags:
  - nanobot
  - dpbot
  - webui
  - temporary
  - chats
  - ephemeral
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

# WebUI Temporary Chats

Use a temporary chat for a conversation that should not be added to topic
history or long-term memory:

1. Select **New topic**
2. Select the **Temporary chat** control in the page header
3. Send the first message

## Behavior

- You can keep more than one temporary chat open and switch between them
  under **Temporary chats** in the sidebar while the current WebUI connection
  remains open
- Reloading or closing the page, restarting the gateway, or losing the
  WebSocket connection ends all of them
- They cannot be recovered afterward

## Limitations

- Temporary chats do not create saved files for oversized text tool results;
  these stay in memory and are truncated to the configured tool-result limit
- Tool-call arguments and execution-error details are hidden from the built-in
  tool logs, while tool activity remains visible in the current chat
- Temporary chats always use the default workspace in Restricted mode; the
  project picker and Full Access are unavailable
- Commands and tools that create durable goals, automations, or subagent work
  are also unavailable

## Warning

Temporary does not mean consequence-free. Requests still go to the configured
model provider, and tools can still change files, run commands, or affect
external services. Files and image artifacts created or exported by tools
(including images returned by MCP tools) are not erased when the chat closes.

## Related

- [WebUI Topics](./webui-topics.md) — Persistent topics
- [WebUI Workspace](./webui-workspace.md) — Workspace and access
- [Subagents](./subagents.md) — Subagent delegation
- [Configuration](./configuration.md) — Config file and schema