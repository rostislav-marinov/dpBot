---
type: Concept
title: dpBot Memory and Dream
description: >
  Long-term memory and Dream consolidation for the dpBot nanobot fork.
tags:
  - nanobot
  - memory
  - dream
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:10:00Z
sources:
  - id: docs-memory
    resource: /projects/dpBot/docs/memory.md
    title: Memory (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# Memory and Dream

## Long-Term Memory

nanobot keeps long-term memory in the agent workspace:

- `SOUL.md` — Core principles and reply-style rules.
- `USER.md` — User profile and standing preferences.
- `memory/MEMORY.md` — Durable facts that persist across sessions.
- `memory/history.jsonl` — Append-only JSONL history log.

## Memory Flow

### Stage 1: Consolidator

When a conversation grows large, nanobot summarizes the conversation
covered by compaction and appends the result to `memory/history.jsonl`.
The model continues with the summary and any messages after it.

Compaction runs after a configured period of inactivity, or when you send
`/compact`. See [Auto Compact](../configuration.md#auto-compact).

### Stage 2: Dream

`Dream` is the slower, more thoughtful layer. It runs on a cron schedule
while the gateway is running and Dream is enabled, and can also be
triggered manually with `/dream`.

Dream reads:
- New entries from `memory/history.jsonl`
- The current `SOUL.md`
- The current `USER.md`
- The current `memory/MEMORY.md`

Then it edits the long-term files surgically in a single pass — making
the smallest honest change that keeps memory coherent.

## Memory Files

```
workspace/
├── .git/                # Version history for long-term memory files
├── SOUL.md              # The bot's long-term voice and communication style
├── USER.md              # Stable knowledge about the user
├── prompts/
│   ├── README.md        # Notes for memory guidance files
│   └── dream.md         # Optional instructions for how Dream organizes memory
└── memory/
    ├── MEMORY.md        # Project facts, decisions, and durable context
    ├── history.jsonl    # History summaries with bounded retention after Dream
    ├── .cursor          # Consolidator write cursor
    └── .dream_cursor    # Dream consumption cursor
```

A selected project may provide its own `AGENTS.md`, but project-local
`SOUL.md`, `USER.md`, and `memory/` do not replace the agent-owned files.

## Commands

| Command | What it does |
|---------|--------------|
| `/compact` | Summarize the current conversation context |
| `/dream` | Run Dream immediately |
| `/dream-log` | Show the latest Dream memory change |
| `/dream-restore` | List recent Dream memory versions |
| `/dream-prompt` | Show how Dream is being guided for memory |

## Related

- [Architecture](./architecture.md) — Memory storage in the runtime.
- [Configuration](./configuration.md) — Auto-compact and Dream settings.
- [Operations](./operations.md) — Cron jobs and monitoring.