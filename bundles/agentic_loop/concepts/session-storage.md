---
type: Component
title: dpBot Session Storage (Implementation)
description: >
  Session storage in dpBot — SQLite session store, session manager, session
  activity, and session delivery.
tags:
  - nanobot
  - agentic-loop
  - sessions
  - sqlite
  - storage
  - runtime
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T20:00:00Z
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
  - id: dpbot-session-activity
    resource: /projects/dpBot/nanobot/agent/session_activity.py
    title: Session Activity (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
---

# Session Storage (Implementation)

Session storage in dpBot handles near-term conversation replay and session
lifecycle management.

## Session Manager

The `SessionManager` handles session management and lifecycle:

- Session creation and retrieval
- Session state management
- Session compaction

## SQLite Store

The SQLite store (`sqlite_store.py`) persists session history:

- Location: `<config-dir>/sessions/<workspace-id>/sessions.sqlite3`
- Stores recent conversation turns replayed into context
- Session history is outside the agent-accessible workspace

## Session Activity

Session activity tracking (`session_activity.py`) records:

- Turn activity
- Tool call activity
- File edit activity
- Completion statistics

## Session Delivery

Session delivery (`session_delivery.py`) handles:

- Delivery of session messages to channels
- Session turn management
- Session state persistence

## Related

- [Memory and Sessions](./memory-sessions.md)
- [Core Flow](./core-flow.md)
- [dpBot Documentation bundle](../documentation/index.md)
