---
type: Component
title: dpBot Tools (Implementation)
description: >
  Tool discovery, execution, and safety in dpBot, including built-in tools
  and plugin tool management.
type: Component
tags:
  - nanobot
  - agentic-loop
  - tools
  - runtime
  - execution
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:20:00Z
sources:
  - id: dpbot-tools-registry
    resource: /projects/dpBot/nanobot/agent/tools/registry.py
    title: Tool Registry (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
  - id: dpbot-tools-execution
    resource: /projects/dpBot/nanobot/agent/tools/execution.py
    title: Tool Execution (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
  - id: dpbot-tools-base
    resource: /projects/dpBot/nanobot/agent/tools/base.py
    title: Tool Base (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
---

# Tools (Implementation)

Tool discovery, execution, and safety in dpBot.

## Tool Discovery

Tools are discovered from `nanobot/agent/tools/` and plugin entry points.

## Key Components

### `nanobot/agent/tools/registry.py`
Tool registry for discovering and managing tools.

### `nanobot/agent/tools/execution.py`
Tool execution engine with concurrent tool support.

### `nanobot/agent/tools/base.py`
Tool base and schema definitions.

## Built-in Tool Categories

- **Filesystem tools**: File read/write/edit and patching
- **Shell execution**: Shell execution with configurable sandboxing
- **Web search/fetch**: Web search and web fetch with SSRF checks
- **MCP tools**: Model Context Protocol integration
- **Cron**: Cron reminders, local triggers, and heartbeat tasks
- **Image generation**: Image generation capabilities
- **Runtime self-inspection**: Agent runtime introspection

## Safety Controls

Security-sensitive controls live in `configuration.md#security`.

## Related

- [dpBot Documentation bundle](../documentation/index.md)
- [Configuration](./configuration.md)
- [AgentLoop](./agentloop.md)
- [AgentRunner](./agentrunner.md)
- [Context](./context.md)