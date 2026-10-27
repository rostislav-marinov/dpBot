---
type: Concept
title: dpBot Update Protocol
description: >
  Update and release procedures for dpBot — version management, update
  channels, recovery, and installation-specific routes.
tags:
  - nanobot
  - dpbot
  - update
  - release
  - versioning
  - recovery
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:30:00Z
sources:
  - id: docs-updating
    resource: /projects/dpBot/docs/updating.md
    title: Updating (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
  - id: docs-releasing
    resource: /projects/dpBot/docs/releasing.md
    title: Releasing (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# Update Protocol

dpBot includes update and release procedures for keeping the installation
current and recovering from failed updates.

## Update Channels

| Channel | Description |
|---|---|
| `stable` | Latest stable PyPI release |
| `preview` | Preview subscription releases |

## Update Commands

```bash
nanobot update --check       # Check the latest stable PyPI release; do not install
nanobot update               # Install it in an ordinary Python venv
nanobot update --dev         # Update source and prepare its matching interfaces
nanobot update --plan        # Save an exact review; do not install or restart
```

The first two commands target stable PyPI releases, not the saved Preview
subscription. `--dev` (`--update-dev`) selects source, not Preview.

## Recovery

In-place CLI updates have no automatic rollback. A failed or interrupted
installation leaves an incomplete-update marker under `~/.nanobot/run/`.
Stop dpBot and retry the same update from that environment.

Downgrading requires `--allow-downgrade` and compatible data; back up before
using it.

## Installation-Specific Routes

Use the original installation-specific route for uv, pipx, containers, system
packages, and Desktop; do not overwrite a manager-owned environment with pip.

Source updates require Git. Existing editable checkouts fast-forward their
current branch to its upstream; resolve local changes, detached HEADs and
divergence manually.

## WebUI Update Flow

The WebUI's **Settings → About** uses a separate reviewed update-and-restart
flow for supported installations and shows owner-specific instructions for
others.

## Related

- [CLI Reference](./cli.md) — Update commands
- [Operations](./operations.md) — Deployment and monitoring
- [Architecture](./architecture.md) — Source ownership
