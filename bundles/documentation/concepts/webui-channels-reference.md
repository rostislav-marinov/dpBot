---
type: Concept
title: dpBot WebUI Channels Reference
description: >
  WebUI channel management — connecting chat platforms, validating
  connections, and managing channel setup.
tags:
  - nanobot
  - dpbot
  - webui
  - channels
  - chat
  - platform
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

# WebUI Channels Reference

Open **Channels** to connect chat apps without assembling JSON by hand. Search
for a platform, open its setup panel, and follow the fields or QR flow shown
for that channel.

## Channel Setup

The guided setup can:

- Install missing optional channel support when the WebUI is running locally
- Collect platform credentials while preserving previously saved values
- Handle supported QR-based login flows
- Validate the connection and show actionable setup errors
- Tell you when the gateway needs to restart

## Test a new channel

Test a new channel with a private DM. When a supported channel sends a
pairing code, the WebUI surfaces the pending request so you can approve the
sender. Keep access narrow; do not use a wildcard allowlist unless public
access is intentional.

## Related

- [WebUI Topics](./webui-topics.md) — Topic management
- [WebUI Workspace](./webui-workspace.md) — Workspace and access
- [WebUI Composer](./webui-composer.md) — Composer, mentions
- [WebUI Apps](./webui-apps.md) — Apps management
- [Architecture](./architecture.md) — Channel discovery
- [CLI Channels](./cli-channels.md) — Channel CLI commands