# Plan: remove CLI Apps support, keep MCP

Status: ready. The three decisions are recorded. The plan stays in `.agent/plans/todo/` until Rosko starts the work.

## Goal

dpBot drops the CLI Apps feature and keeps MCP support. The gateway keeps MCP servers from the config file, MCP presets, MCP OAuth, and custom MCP servers.

After the change the gateway has no CLI app catalog, no CLI app installer, no `run_cli_app` tool, no Agent Plugin loader, and no CLI app surface in the WebUI or the TUI.

## Terms

- CLI Apps: the CLI-Anything and nanobot-extension registry adapters in `nanobot/apps/cli/`, the `run_cli_app` agent tool, the CLI app settings API, and the CLI app surfaces in the WebUI and the TUI.
- MCP: `nanobot/agent/tools/mcp.py`, `MCPServerConfig` in the config schema, MCP presets, MCP OAuth, and the MCP settings surfaces.
- Agent Plugins: packages under `workspace/plugins/<name>/` that provide skills and MCP servers. The CLI app installer was the only in-tree producer of these packages. The plugin loader goes with the apps.

## Decisions

D1 — Agent Plugins: keep or remove. Decided on 2026-10-22: remove. A plugin package is an app plus the handling for that app. With the apps gone, nothing produces plugin packages, so the loader has no input. The MCP surface keeps the config file servers, the presets, and the custom servers. The channel plugins in `nanobot/channels/registry.py` are a different mechanism and stay.

D2 — WebUI section name: rename the "Apps" settings section to "MCP", or keep the section key and change only the visible text. Decided on 2026-10-22: rename. The section key `apps` becomes `mcp`, the route `/apps` becomes `/mcp`, and the sidebar label becomes MCP. The locales already carry the unused keys `settings.nav.mcp` and `settings.sections.mcp`. Reuse them instead of adding new keys.

D3 — Manifest schema value. `nanobot/apps/protocol.py` defines `APP_PROTOCOL_SCHEMA = "agent-app.v1"`, and the MCP preset payload embeds that manifest. Decided on 2026-10-22: rename the value. The new value is `mcp.v1`, because the manifest describes an MCP integration with the sources `mcp-preset` and `mcp-custom`. The WebUI type `AppManifest.schema` in `webui/src/lib/types.ts` and the two assertions in `tests/webui/test_mcp_presets_api.py` change with it.

## Scope

### Delete, Python gateway

- `nanobot/apps/` — the whole package. It holds `protocol.py`, `cli/service.py` (the registry adapters, the install state, and the CLI runner), `cli/utils.py` (the runtime context lines and the session extra), and `cli/__init__.py`.
- `nanobot/agent/tools/cli_apps.py` — the `run_cli_app` tool.
- `nanobot/agent/tools/cli_apps_config.py` — the `CliAppsToolConfig` model.
- `nanobot/webui/cli_apps_api.py` — the CLI app settings API.
- `nanobot/agent/plugins.py` — the Agent Plugin loader. The file holds the package discovery, the manifest validation, the enable marker, the plugin skills, and the plugin MCP servers.

### Edit, Python gateway

- `nanobot/config/schema.py` — remove the `cli_apps` field from `ToolsConfig` and the `CliAppsToolConfig` import.
- `nanobot/agent/context.py` — remove the `cli_app_utils.session_extra` call and the import of `nanobot.apps.cli.utils`.
- `nanobot/agent/skills.py` — remove `_skill_aliases`, the `aliases` field of `_SkillSnapshot`, the `CliAppManager` import, and the alias lookups. The aliases map legacy CLI app skill names to plugin skill names, so they have no purpose after the removal. Remove the plugin skill discovery, the `plugin` skill source, and the "Agent Plugin skills" group in `_build_skills_summary`.
- `nanobot/agent/tools/mcp.py` — remove the `agent_plugin_mcp_servers` merge in `_configured_servers`. The configured MCP servers come from the config file alone.
- `nanobot/agent/tools/filesystem.py` — remove the plugin skill dirs from the extra read roots in `_resolve_read`.
- `nanobot/session/manager.py` — remove the "CLI App Attachment" breadcrumb block.
- `nanobot/data_access.py` — remove `cli-apps/installed.json` from `_DATA_STORES`.
- `nanobot/webui/settings_routes.py` — remove the `/api/settings/cli-apps` routes, the route names, the restart behavior map entries, and the `cli_apps_payload` and `cli_apps_action` wiring.
- `nanobot/webui/settings_system.py` — remove the `cli_apps_payload` and `cli_apps_action` operations and the `_cli_apps` and `_cli_apps_action` handlers.
- `nanobot/webui/settings_runtime.py` — remove the `tools.cli_apps.*` entries from the runtime config allowlist.
- `nanobot/webui/ws_http.py` — remove the `settings.cli_app.*` action map entries.
- `nanobot/webui/history.py` — remove `cli_apps` from the stored content keys.
- `nanobot/webui/transcript.py` — remove the `cli_apps` projection, the event field, and the inbound message field.
- `nanobot/webui/inbound_commands.py` — remove the `cli_apps` metadata and body fields and the `normalize_cli_app_mentions` call.
- `nanobot/webui/mcp_presets_api.py` — change the import of the manifest helpers to the new module. Remove `_agent_plugin_payload`, the plugin rows in the payload, the `plugin-` branch in the action handler, and the `AgentPlugin`, `discover_agent_plugins`, and `set_agent_plugin_enabled` imports.

### Add, Python gateway

- `nanobot/webui/mcp_manifest.py` — hold `MCP_MANIFEST_SCHEMA = "mcp.v1"`, `app_manifest`, and `compact_dict`, moved from `nanobot/apps/protocol.py`. The WebUI MCP preset payload is the only consumer left.

### Edit, WebUI

- `webui/src/lib/cli-app-events.ts` — delete the file.
- `webui/src/lib/api.ts` — remove `fetchCliApps`, `fetchInstalledCliApps`, and `runCliAppAction`, and the `cli_apps` branch in the event parser.
- `webui/src/lib/types.ts` — remove `CliAppInfo`, `CliAppsPayload`, `UICliAppAttachment`, and the `cliApps` fields. Keep `AppManifest`, because the MCP payload carries it. Change its `schema` literal from `agent-app.v1` to `mcp.v1`.
- `webui/src/lib/composer-mention-text.ts` — remove the `cli` segment kind.
- `webui/src/lib/thread-event-projection.ts` — remove the `cli_apps` event field.
- `webui/src/lib/nanobot-client.ts` — remove the `cliApps` send option.
- `webui/src/hooks/useNanobotStream.ts` — remove the CLI app stream handling.
- `webui/src/components/CliAppMentionText.tsx` — drop the CLI branch and rename the file to `webui/src/components/CapabilityMentionText.tsx`.
- `webui/src/components/MessageBubble.tsx`, `webui/src/components/UserMessageText.tsx`, `webui/src/components/thread/ThreadMessages.tsx`, `webui/src/components/thread/ThreadViewport.tsx` — drop the `cliApps` props.
- `webui/src/components/thread/ThreadComposer.tsx` — remove the CLI app mention candidates, the CLI mention rendering, and the CLI app mention payload.
- `webui/src/components/thread/ThreadShell.tsx` — remove `fetchInstalledCliApps` and the `CLI_APPS_CHANGED_EVENT` subscription.
- `webui/src/components/thread/AgentActivityCluster.tsx` — remove the CLI run rows and the CLI run tool names.
- `webui/src/components/thread/activity/generic-tool-model.ts` — remove the `run_cli_app` exclusion.
- `webui/src/components/settings/system/AppsSettings.tsx` — rewrite as an MCP only catalog, drop the "ready" and "cli" filters, drop the agent plugin rows and the "Plugins" filter, and rename the file to `webui/src/components/settings/system/McpSettings.tsx`.
- `webui/src/lib/mcp-preset-events.ts` — remove the `source !== "agent-plugin"` filter.
- `webui/src/components/settings/system/useSystemSettingsState.ts`, `webui/src/components/settings/system/useSystemSettingsEffects.ts`, `webui/src/components/settings/system/createSystemSettingsActions.ts` — drop the CLI app state, the CLI app fetch, and the CLI app actions.
- `webui/src/components/settings/system/runtime-config-fields.ts` — drop the `cli` group and the `tools.cli_apps.*` fields.
- `webui/src/components/settings/contracts.ts` — change the section key `apps` to `mcp`.
- `webui/src/components/settings/SettingsPage.tsx`, `webui/src/components/settings/SettingsSidebar.tsx` — use the MCP section and title.
- `webui/src/App.tsx` — change the `apps` shell view, the route, and the sidebar entry to `mcp`.
- `webui/src/components/Sidebar.tsx` — point the sidebar entry at MCP.
- `webui/src/dev/gallery/shell.tsx`, `webui/browser/fixture.tsx`, `webui/browser/skeleton-fixture.tsx`, `webui/browser/skeleton-additions-fixture.tsx` — drop the CLI app fixtures.
- `webui/src/i18n/locales/<locale>/common.json` for the ten locales `en`, `zh-CN`, `zh-TW`, `fr`, `ja`, `ko`, `es`, `pt-BR`, `vi`, `id` — delete the CLI only keys, delete the `settings.apps.filterPlugins` key, update the labels that speak about apps, and use `settings.nav.mcp` and `settings.sections.mcp` for the renamed section. Change every locale in the same commit.
- `webui/src/dev/gallery/locales/previews/<locale>.json` for the ten locales — update the mention text that lists the `cli` segment kind.

### Edit, TUI

- `tui/src/client/api.ts` — remove the CLI app fetch.
- `tui/src/client/types.ts` — remove the `cli` mention kind.
- `tui/src/client/nanobot-client.ts` — remove the `cliApps` send option.
- `tui/src/menus/mention-menu.ts` — remove the `cli` filter entry.

### Edit, scripts

- `scripts/check_import_boundaries.py` — remove `nanobot.agent.tools.cli_apps_config` from `_TOOL_CONFIG_MODULES`, remove `nanobot.webui.cli_apps_api` from the websocket transport rule, and remove `nanobot.apps` from the forbidden target lists of the configuration contracts, the tool configuration contracts, and the shared primitives rules.
- `scripts/ci_scope.py` — remove `nanobot/webui/cli_apps_api.py` from the shared backend client protocol group.

### Delete, tests

- `tests/cli_apps/` — the directory holds `test_service.py`, `test_tool.py`, and `test_utils.py`.
- `tests/agent/test_agent_plugins.py` — the Agent Plugin loader tests.
- `tests/apps/test_cli_subprocess_env.py`.
- `tests/webui/test_cli_apps_api.py`.

### Edit, tests

- `tests/config/test_tool_config_boundaries.py` — remove the `cli_apps` entry and the `nanobot.apps` module in the allowed import list.
- `tests/architecture/test_import_boundaries.py` — remove the CLI app boundary expectations.
- `tests/agent/test_context_builder.py` — remove the CLI app runtime context expectations.
- `tests/agent/test_session_manager_history.py` — remove the CLI app breadcrumb expectations.
- `tests/agent/test_workspace_scope.py` — remove the CLI app scope test.
- `tests/tools/test_tool_loader.py` — remove the CLI app tool expectations.
- `tests/webui/fixtures/runtime-config-keys.json` — remove the `tools.cli_apps.*` keys.
- `tests/webui/test_mcp_presets_api.py` — change the two manifest schema assertions from `agent-app.v1` to `mcp.v1`. Remove the plugin import, the `_write_agent_plugin` helper, and the plugin test.
- `tests/webui/test_skills_api.py` — remove the plugin skill case.
- `nanobot/channels/websocket/tests/test_websocket_channel.py`, `nanobot/channels/websocket/tests/test_websocket_envelope_media.py`, `nanobot/channels/websocket/tests/test_websocket_http_routes.py` — remove the CLI app metadata and route expectations.
- `webui/src/tests/thread-composer.test.tsx`, `webui/src/tests/thread-shell.test.tsx`, `webui/src/tests/agent-activity-cluster.test.tsx`, `webui/src/tests/message-bubble.test.tsx`, `webui/src/tests/api.test.ts`, `webui/src/tests/useNanobotStream.test.tsx`, `webui/src/tests/settings-apps-oauth.test.tsx`, `webui/src/tests/settings-channels.test.tsx`, `webui/src/tests/settings-models.test.tsx`, `webui/src/tests/settings-providers.test.tsx`, `webui/src/tests/settings-system.test.tsx`, `webui/src/tests/settings-capabilities.test.tsx`, `webui/src/tests/settings-overview.test.tsx`, `webui/src/tests/settings-runtime-config.test.tsx`, `webui/src/tests/catalog-loading.test.tsx`, `webui/src/tests/app-layout.test.tsx`, `webui/src/tests/composer-mention-text.test.ts`, `webui/src/tests/generic-tool-model.test.ts`, `webui/src/tests/thread-event-projection.test.ts`, `webui/src/tests/nanobot-client.test.ts`, `webui/src/tests/i18n.test.tsx` — update or drop the CLI app cases.
- `tui/src/client/client.test.ts`, `tui/src/menus/mention-menu.test.ts`, `tui/src/app/composer.test.ts` — update the CLI app cases.

### Edit, docs

- `README.md`, `docs/README.md`, `docs/architecture.md`, `docs/concepts.md`, `docs/configuration.md`, `docs/webui.md` — remove the CLI Apps documentation, remove the Agent Plugin documentation, describe the MCP only surface, and correct the `tools.cliApps` configuration block.
- `docs/release-archive.md` — keep the CLI App mentions. The file records the release history.

## Config and data compatibility

- The `tools.cliApps` block in an existing config file: `ToolsConfig` ignores unknown keys, so the gateway starts with the old block present. `nanobot/config/loader.py::_migrate_config` removes the block on the next load, and the next `save_config` writes the model without it. No manual edit is needed on dpSrvA. Confirm this in the config test update.
- The runtime data store `cli-apps/installed.json` is listed in `nanobot/data_access.py`. After the change nothing reads it. Delete `~/.nanobot/runtime/cli-apps` on dpSrvA by hand.
- The workspace packages under `workspace/plugins/<name>/` that an earlier CLI app install wrote stop loading. The dpSrvA workspace has no `plugins` directory, so nothing changes there. Delete a `plugins` folder by hand if one appears later.
- The network calls stop. The catalog fetched `https://hkuds.github.io/CLI-Anything/registry.json` and `https://raw.githubusercontent.com/Re-bin/nanobot-extension/main/registry.json` on demand.
- The model behavior changes in every session, because the `run_cli_app` tool leaves the tool set. The templates under `nanobot/templates/` carry no CLI app text. The workspace skills must be checked.

## Work steps

1. The decisions D1, D2, and D3 are recorded above. The file moves to `.agent/plans/progress/` on Rosko's word.
2. Remove the Python gateway code: the `nanobot/apps/` package, the tool, the tool config, the settings API, and the gateway edits above. Add `nanobot/webui/mcp_manifest.py` and point `nanobot/webui/mcp_presets_api.py` at it. Run `python -m scripts.check_import_boundaries` and the Python test suite.
3. Remove the Agent Plugin support: delete `nanobot/agent/plugins.py`, drop the plugin skills, the plugin MCP servers, and the plugin rows. Run the Python test suite.
4. Update the boundary scripts and the Python tests. Delete the CLI app tests and the Agent Plugin tests. Run the Python test suite again.
5. Remove the CLI app surface from the WebUI, rename the settings section to MCP per D2, drop the plugin rows, and update the locales for all ten locales in the same commit. Run the WebUI type check, the WebUI tests, the lint, and the import check.
6. Remove the CLI app surface from the TUI. Run the TUI tests and the TUI checks.
7. Update the docs.
8. Run the full verification set below.
9. Move this file to `.agent/plans/done/` and record the outcome in `.agent/requirments.md`.

## Verification

- `/app/.venv/bin/python -m scripts.check_import_boundaries`
- `/app/.venv/bin/python -m pytest tests nanobot/channels -q`
- In `webui/`: `bun run typecheck`, `bun test`, `bun run lint`, `bun run check:imports`
- In `tui/`: `bun test`, `bun run check`, `bun run check:imports`

The container holds no `bun` and no `node_modules`, so the WebUI and the TUI checks run outside this container, on the host or in CI.

## Risks

- An older WebUI client that sends a `cli_apps` mention list keeps working, because the server drops the unknown key and the mention is lost. A newer client against an older gateway behaves the same way.
- The transcript event `cli_apps` disappears. Clients must tolerate the missing key.
- The tool set change alters the model behavior in every session.
- The skills under `workspace/plugins/<name>/skills/` stop loading, and the file tool no longer reads files under `workspace/plugins/`. The workspace skills under `workspace/skills/` are not affected.
- The MCP page loses the plugin rows. The remaining rows are the presets, the custom servers, and the config file servers.
- The settings section rename changes the WebUI route. A bookmark to `/apps` lands on another view. Add a redirect from `/apps` to `/mcp` when the router allows it.

## Out of scope

- The MCP client, the MCP presets, and the MCP OAuth.
- The channel plugins in `nanobot/channels/registry.py` and the `nanobot plugins` CLI that manages them.
- The ClawHub skills and the skills marketplace.
- The workspace skills that use MCP.
