---
type: Concept
title: dpBot WebUI Delegated Work Reference
description: >
  WebUI delegated work — subagent work groups, progress tracking, and
  task inspection.
tags:
  - nanobot
  - dpbot
  - webui
  - delegated-work
  - subagents
  - progress
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:30:00Z
sources:
  - id: docs-webui
    resource: /projects/dpBot/docs/webui.md
    title: WebUI (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# WebUI Delegated Work Reference

When dpBot delegates work to subagents, a work group appears under the
request that started it. Progress continues to update after the main reply
finishes. Completed tasks stay available for inspection, and refreshing or
reopening the WebUI restores saved progress and results without restarting
the work.

## Work Group Preferences

Work groups follow the browser's **Activity details** preference:

- **Auto** — Opens running work and folds it when all tasks finish
- **Expanded** — Keeps it open by default

You can also expand or fold a group manually to check individual outcomes,
including failures and partial results.

## Task Inspection

Select a task to open its read-only conversation on the right, or across the
screen on mobile. Read its messages, tool activity, file edits, and results,
including formatted Markdown. Closing the details leaves the task running;
its stop button cancels only that task. Give follow-up instructions to dpBot
in the main conversation.

## Related

- [WebUI Activity](./webui-activity.md) — Activity and context usage
- [Subagents](./subagents.md) — Subagent delegation
- [WebUI Topics](./webui-topics.md) — Topic management