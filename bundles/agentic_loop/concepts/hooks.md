---
type: Component
title: dpBot Hook System (Implementation)
description: >
  Hook system in dpBot — turn hooks, progress hooks, and hook specifications
  for channel-facing turn orchestration.
tags:
  - nanobot
  - agentic-loop
  - hooks
  - turn-hooks
  - progress-hook
  - runtime
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T20:00:00Z
sources:
  - id: dpbot-hook
    resource: /projects/dpBot/nanobot/agent/hook.py
    title: Hook (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
  - id: dpbot-turn-hooks
    resource: /projects/dpBot/nanobot/agent/turn_hooks.py
    title: Turn Hooks (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
  - id: dpbot-progress-hook
    resource: /projects/dpBot/nanobot/agent/progress_hook.py
    title: Progress Hook (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
---

# Hook System (Implementation)

The hook system in dpBot wires hooks, progress, and channel metadata into
the channel-facing turn orchestration.

## Turn Hooks

Turn hooks (`turn_hooks.py`) provide hooks that fire at various points in
the agent turn lifecycle:

- Before/after model requests
- Before/after tool execution
- Before/after turn completion

## Progress Hooks

Progress hooks (`progress_hook.py`) track and report progress during agent
turns:

- Tool call progress
- Streaming progress
- Turn completion status

## Hook Specification

`AgentTurnHookSpec` defines the hook specification interface:

- Hook registration
- Hook invocation
- Hook metadata

## Related

- [AgentLoop](./agentloop.md)
- [Core Flow](./core-flow.md)
- [dpBot Documentation bundle](../documentation/index.md)
