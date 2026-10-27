---
type: Concept
title: dpBot WebUI Activity and Context Usage
description: >
  WebUI activity tracking — message timeline, agent activity, model failures,
  and delegated work.
tags:
  - nanobot
  - dpbot
  - webui
  - activity
  - context
  - model-failures
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

# WebUI Activity and Context Usage

The message timeline shows replies and agent activity. Expand the **Worked
for** section to inspect the reasoning and tool activity for a completed turn.

## Loading Earlier Messages

To load earlier messages, scroll past the oldest loaded message, or pull down
far enough and release on touch devices. The muted loading indicator settles
into view while the request runs.

## Context Usage

Open the context indicator beside the composer model badge to see how much of
the model's context window is in use. The **Recent rounds** chart shows input
tokens for each logical model round, including tool-call rounds.

## Model Failures

After a model request fails and automatic retries stop, the WebUI shows the
failure category. Use **Continue** to resume from the saved conversation, or
open model settings to change the model or correct its authorization.

## Related

- [WebUI Topics](./webui-topics.md) — Topic management
- [WebUI Temporary](./webui-temporary.md) — Temporary chats
- [WebUI Delegated Work](./webui-delegated.md) — Subagent delegation
- [Configuration](./configuration.md) — Model settings