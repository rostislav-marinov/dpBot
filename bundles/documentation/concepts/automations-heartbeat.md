---
type: Concept
title: dpBot Automations Heartbeat
description: >
  Heartbeat in dpBot — protected system schedule for quiet recurring checks
  that only report useful results.
tags:
  - nanobot
  - dpbot
  - automations
  - heartbeat
  - background
  - checks
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:30:00Z
sources:
  - id: docs-automations
    resource: /projects/dpBot/docs/automations.md
    title: Automations (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# Automations Heartbeat

## Overview

Protected system schedule for quiet recurring checks that should only report useful results. Reads `<workspace>/HEARTBEAT.md` and executes active tasks.

## Use Cases

Use heartbeat for checks such as:

- "Watch this repo for important failures"
- "Periodically inspect this workspace and only tell me when action is needed"

## Related

- [Automations Scheduled](./automations-scheduled.md) — Scheduled automations
- [Automations Triggers](./automations-triggers.md) — Local triggers
- [WebUI Automations](./webui-automations.md) — Automations view
- [Configuration](./configuration.md) — Gateway heartbeat settings