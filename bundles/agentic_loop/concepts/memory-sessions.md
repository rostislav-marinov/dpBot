---
type: Component
title: dpBot Memory and Sessions (Implementation)
description: >
  Session replay, long-term memory, and Dream consolidation in dpBot,
  including SQLite session storage and memory management.
type: Component
tags:
  - nanobot
  - agentic-loop
  - memory
  - sessions
  - runtime
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:20:00Z
sources:
  - id: dpbot-session-manager
    resource: /projects/dpBot/nanobot/session/manager.py
    title: Session Manager (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
  - id: dpbot-session-sqlite
    resource: /projects/dpBot/nanobot/session/sqlite_store.py
    title: SQLite Store (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
  - id: dpbot-agent-memory
    resource: /projects/dpBot/nanobot/agent/memory.py
    title: Memory (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
---

# Memory and Sessions (Implementation)

Session replay, long-term memory, and Dream consolidation in dpBot.

## Session Management

Session history is the near-term conversation replay stored in SQLite:

- **Store**: `<config-dir>/sessions/<workspace-id>/sessions.sqlite3`
- **Purpose**: Recent conversation turns replayed into context

## Long-Term Memory

Long-term memory is the longer-term workspace state:

- **Memory**: `<workspace>/memory/MEMORY.md` and `<workspace>/memory/history.jsonl`
- **Purpose**: Durable facts and consolidated history

## Dream Consolidation

`Dream` is a periodic consolidation job implemented in `nanobot/agent/memory.py`.

## Key Components

### `nanobot/session/manager.py`
Session management and lifecycle.

### `nanobot/session/sqlite_store.py`
SQLite session storage implementation.

### `nanobot/agent/memory.py`
Dream consolidation and memory management.

## Related

- [Core Flow](./core-flow.md)
- [dpBot Documentation bundle](../documentation/index.md)
- [Configuration](./configuration.md)
- [Context](./context.md)
- [Session Storage](./session-storage.md)
- [Templates](./templates.md)