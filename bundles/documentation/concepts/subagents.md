---
type: Concept
title: dpBot Subagents
description: >
  Subagents in dpBot — delegating parts of a request to background tasks
  while remaining responsible for the final answer.
tags:
  - nanobot
  - dpbot
  - subagents
  - delegation
  - background-tasks
  - runtime
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

# Subagents

Nanobot can delegate parts of a request to subagents while remaining
responsible for the final answer.

## Background Tasks

Background tasks return their results to the conversation that started them.
Single-turn CLI and SDK calls wait for results when background delivery is
unavailable. Tasks that reach their iteration limit are marked incomplete;
cancelled, failed, and incomplete tasks retain available partial results.

Use `/stop` to stop the current session and its subagents. Other sessions are
unaffected. Some operations may take time to stop, and cancellation does not
undo file changes or other actions already taken.

## Subagent Lifecycle

Subagents belong to their original conversation. They do not appear as
separate topics or in general conversation searches.

- Deleting the conversation stops its subagents and removes their saved
  history
- Forking a conversation does not copy its subagents

Saved task history and results remain available after a gateway restart.
Unfinished tasks are marked interrupted, with saved partial results when
available. Nanobot does not automatically resume them or resend completion
notifications; ask it to start a new task to continue the work.

## WebUI Delegated Work

When dpBot delegates work to subagents, a work group appears under the
request that started it. Progress continues to update after the main reply
finishes. Completed tasks stay available for inspection, and refreshing or
reopening the WebUI restores saved progress and results without restarting
the work.

Work groups follow the browser's **Activity details** preference:

- **Auto** — Opens running work and folds it when all tasks finish
- **Expanded** — Keeps it open by default

You can also expand or fold a group manually to check individual outcomes,
including failures and partial results.

Select a task to open its read-only conversation on the right, or across the
screen on mobile. Read its messages, tool activity, file edits, and results,
including formatted Markdown. Closing the details leaves the task running; its
stop button cancels only that task. Give follow-up instructions to dpBot in
the main conversation.

## Temporary Chats and Subagents

WebUI temporary chats do not support subagents. SDK calls with
`ephemeral=True` wait for delegated results without saving the temporary
conversation or its subagent history.

## Related

- [WebUI](./webui.md) — Delegated work view
- [CLI Reference](./cli.md) — `nanobot agent` command
- [Configuration](./configuration.md) — Config file and schema
- [Architecture](./architecture.md) — Source ownership