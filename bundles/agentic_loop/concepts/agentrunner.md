---
type: Component
title: dpBot AgentRunner (Implementation)
description: >
  The AgentRunner class in dpBot implements the model-facing loop for the
  agentic loop, handling provider calls, streaming, tool execution, and
  termination conditions.
type: Component
tags:
  - nanobot
  - agentic-loop
  - agentrunner
  - implementation
  - runtime
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:20:00Z
sources:
  - id: dpbot-agent-runner
    resource: /projects/dpBot/nanobot/agent/runner.py
    title: AgentRunner (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
---

# AgentRunner (Implementation)

The `AgentRunner` class in dpBot implements the model-facing loop for the
agentic loop.

## Core Responsibilities

- **Provider calls**: Sends messages to the selected provider via `_request_model()`
- **Streaming**: Handles streaming deltas and reasoning blocks via `_request_model()`
- **Tool execution**: Executes tool calls via `execute_tool_calls()`
- **Tool result feedback**: Feeds tool results back into the model
- **Termination conditions**: Stops when a final answer is produced or runtime limits are hit

## Key Methods

### `run()`
Main execution loop that orchestrates the tool-capable LLM loop.

### `_run_core()`
Core execution logic that handles model requests, tool calls, and streaming.

### `_request_model()`
Makes provider calls with streaming support and error handling.

### `_try_drain_injections()`
Handles mid-turn injections and continuations.

## Source Files

- `nanobot/agent/runner.py` — Main AgentRunner implementation
- `nanobot/agent/context_governance.py` — Context governance
- `nanobot/agent/tools/execution.py` — Tool execution
- `nanobot/agent/loop.py` — AgentLoop (channel-facing)

## Related

- [Core Flow](./core-flow.md)
- [AgentLoop](./agentloop.md)
- [Context](./context.md)
- [Tools](./tools.md)
- [Providers](./providers.md)
- [dpBot Documentation bundle](../documentation/index.md)