# Requirements

## R-001 — Keep MCP support, drop CLI Apps support

Status: proposed. Plan: `.agent/plans/todo/remove-cli-apps-keep-mcp.md`.

Statement: dpBot must keep MCP support and must not ship CLI Apps support.

Acceptance criteria:

- The gateway has no CLI app catalog, no CLI app installer, no `run_cli_app` tool, and no Agent Plugin loader.
- MCP servers from the config file, MCP presets, MCP OAuth, and custom MCP servers keep working.
- The WebUI and the TUI show no CLI app surface. The WebUI settings section is named MCP and the route is `/mcp`.
- The skills load only from `workspace/skills/` and from the built-in skills.
- An old `tools.cliApps` block in the config file does not break the startup.
- The Python tests, the WebUI checks, and the TUI checks pass.

## R-002 — Per-cron model preset selection (extended: three job types)

Status: proposed. Plan: `.agent/plans/todo/per-cron-model-preset-extended.md`.

Statement: dpBot must allow each scheduled task, automation, or cron job to specify its own model preset, independent of the session default, and must support three execution modes: contexted AI, contextless AI, and pure shell.

Acceptance criteria:

- A cron job definition can reference a model preset by name.
- The gateway resolves the preset at job start and uses it for that job's session.
- If no preset is specified, the job falls back to the session default.
- The WebUI and TUI show the preset field when editing a cron job.
- The Python tests, the WebUI checks, and the TUI checks pass.

### R-002.1 — Contextless AI cron jobs

A cron job with a model preset different from the parent session runs in a new session with that preset, then joins the outcome back to the parent session.

### R-002.2 — Pure shell cron jobs

A cron job with `model_preset: None` executes a shell command directly with no LLM call, attaches output to the parent session, and returns an error code on failure.

> R-003 (pure shell option) is folded into R-002.2. The original R-003 requirement is superseded by the extended R-002 design.

## R-004 — WebUI as installable Progressive Web App

Status: proposed. Plan: not yet created.

Statement: dpBot WebUI must be installable as a Progressive Web App (PWA).

Acceptance criteria:

- The WebUI serves a valid Web App Manifest.
- The WebUI registers a service worker for offline caching.
- The WebUI meets the installability criteria (HTTPS, manifest, service worker, icons).
- Users can install the WebUI from the browser to their device home screen or desktop.
- The Python tests, the WebUI checks, and the TUI checks pass.

## R-005 — Title model preset selection

Status: proposed. Plan: `.agent/plans/todo/title-model-preset.md`.

Statement: dpBot must allow users to specify a model preset for generating session titles (chat topic names), independent of the agent's default model preset.

Acceptance criteria:

- Users can set a `title_model_preset` in the agent defaults configuration
- When generating a session title, the system uses the specified `title_model_preset` if set, otherwise falls back to the agent's default model preset
- The WebUI shows the title model preset setting in the AI settings section
- The TUI shows the title model preset setting in the model configuration
- Existing sessions continue to work without the `title_model_preset` field (backward compatible)
- The Python tests, the WebUI checks, and the TUI checks pass
