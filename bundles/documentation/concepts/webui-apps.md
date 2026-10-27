---
type: Concept
title: dpBot WebUI Apps
description: >
  WebUI Apps section in dpBot — MCP support, CLI Apps dropped.
tags:
  - nanobot
  - dpbot
  - webui
  - apps
  - mcp
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

# WebUI Apps

## Overview

The WebUI Apps section was replaced by MCP support in dpBot.

## Changes

| Item | Before | After |
|------|--------|-------|
| Section key | `apps` | `mcp` |
| Route | `/apps` | `/mcp` |
| Sidebar label | Apps | MCP |
| Locale keys | `settings.nav.apps`, `settings.sections.apps` | `settings.nav.mcp`, `settings.sections.mcp` |
| Manifest schema value | `agent-app.v1` | `mcp.v1` |

## Related

- [WebUI Apps Management](./webui-apps-management.md) — Apps management
- [WebUI Skills](./webui-skills.md) — Skills management in browser
- [Architecture](./architecture.md) — Source ownership