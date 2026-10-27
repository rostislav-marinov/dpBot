---
type: Component
title: dpBot AgentLoop (Implementation)
description: >
  The AgentLoop class in dpBot implements the channel-facing turn orchestration
  for the agentic loop, managing session scope, context building, hooks,
  progress, and outbound delivery.
type: Component
tags:
  - nanobot
  - agentic-loop
  - agentloop
  - implementation
  - runtime
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:20:00Z
sources:
  - id: dpbot-agent-loop
    resource: /projects/dpBot/nanobot/agent/loop.py
    title: AgentLoop (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
---

# AgentLoop (Implementation)

The `AgentLoop` class in dpBot implements the channel-facing turn orchestration
for the agentic loop.

## Core Responsibilities

- **Inbound message handling**: Receives messages from the bus via `run()` and `_dispatch_inbound()`
- **Session and workspace scope**: Determines effective session and workspace scope via `_effective_session_key()`
- **Context building**: Builds context via `ContextBuilder` and `ContextBuilder.prepare_prompt()`
- **Hooks and progress**: Wires hooks, progress, and channel metadata via `AgentTurnHookSpec`
- **Outbound delivery**: Publishes outbound messages via `TurnDelivery`

## Key Methods

### `run()`
Main event loop that consumes inbound messages and dispatches them to session workers.

### `_dispatch_inbound()`
Routes one input through command and session admission.

### `_process_message()`
Processes a single inbound message and returns the response.

### `_run_session_queue()`
Runs the sole worker for a session until its inbox is empty.

## Source Files

- `nanobot/agent/loop.py` — Main AgentLoop implementation
- `nanobot/agent/context.py` — Context building
- `nanobot/agent/tools/registry.py` — Tool registry
- `nanobot/agent/runner.py` — AgentRunner (model-facing loop)

## Related

- [Core Flow](./core-flow.md)
- [AgentRunner](./agentrunner.md)
- [Providers](./providers.md)
- [Channels](./channels.md)
- [Tools](./tools.md)
- [Memory and Sessions](./memory-sessions.md)
- [Context](./context.md)
- [MessageBus](./bus.md)
- [Hook System](./hooks.md)
- [Session Storage](./session-storage.md)
- [Templates](./templates.md)
- [dpBot Documentation bundle](../documentation/index.md)
- [dpBot Documentation bundle](../documentation/index.md)