---
type: Concept
title: dpBot MCP Local Presets
description: >
  Local MCP server presets catalogue — servers that run on the gateway
  computer with local runtime requirements.
tags:
  - nanobot
  - dpbot
  - mcp
  - local
  - presets
  - runtime
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:30:00Z
sources:
  - id: docs-mcp-presets
    resource: /projects/dpBot/docs/mcp-presets.md
    title: MCP presets (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# MCP Local Presets

Local MCP servers run on the gateway computer. Install the runtime or
application listed for each service.

## Local Server Catalog

| Service | Requirements | Setup |
|---|---|---|
| Playwright | Node.js and npx | [Server guide](https://playwright.dev/docs/getting-started-mcp) |
| Context7 | Node.js, npx, optional API key | [Server guide](https://context7.com/docs/resources/all-clients) |
| AWS Documentation | uvx | [Server guide](https://awslabs.github.io/mcp/servers/aws-documentation-mcp-server/) |
| Brave Search | Node.js, npx, Brave Search API key | [Server guide](https://www.npmjs.com/package/@brave/brave-search-mcp-server) |
| Postman | Node.js, npx, Postman API key | [Server guide](https://learning.postman.com/docs/developer/postman-api/postman-mcp-server/postman-mcp-local-server) |
| Figma | Figma desktop app with MCP enabled | [Server guide](https://help.figma.com/hc/en-us/articles/32132100833559-Guide-to-the-Figma-MCP-server) |
| GitHub | Docker and GitHub token | [Server guide](https://github.com/github/github-mcp-server) |
| Supabase | Node.js, npx, Supabase access token | [Server guide](https://supabase.com/docs/guides/ai-tools/mcp) |
| Firebase | Node.js, npx, Firebase CLI sign-in | [Server guide](https://firebase.google.com/docs/ai-assistance/mcp-server) |
| MongoDB | Node.js, npx, MongoDB connection string | [Server guide](https://www.mongodb.com/docs/mcp-server/local-mcp/security-best-practices/) |
| ClickHouse | uvx and ClickHouse connection credentials | [Server guide](https://github.com/ClickHouse/mcp-clickhouse) |
| Redis | uvx and Redis connection URL | [Server guide](https://github.com/redis/mcp-redis) |
| dbt | uvx and dbt account with a static subdomain | [Server guide](https://docs.getdbt.com/docs/dbt-ai/setup-local-mcp) |
| Google Workspace | uvx and Google Cloud OAuth app | [Server guide](https://github.com/taylorwilsdon/google_workspace_mcp) |
| Microsoft 365 | Node.js, npx, Microsoft work or school account | [Server guide](https://github.com/Softeria/ms-365-mcp-server) |
| Adobe Express Developer | Node.js and npx | [Server guide](https://developer.adobe.com/express/add-ons/docs/guides/getting-started/local-development/mcp-server) |
| Azure | Node.js, npx, Azure CLI, Azure sign-in | [Server guide](https://github.com/microsoft/mcp/tree/main/servers/Azure.Mcp.Server) |
| Tableau | Node.js 22.7.5+, npx, Tableau personal access token | [Server guide](https://github.com/tableau/tableau-mcp) |
| BigQuery | Node.js, npx, Google Application Default Credentials | [Server guide](https://docs.cloud.google.com/bigquery/docs/pre-built-tools-with-mcp-toolbox) |
| Salesforce DX | Node.js, npx, Salesforce CLI, authorized default target org | [Server guide](https://developer.salesforce.com/docs/platform/sfdx-dev/guide/sfdx-dev-mcp-server.html) |
| Shopify Developer | Node.js 18+, npx | [Server guide](https://shopify.dev/docs/apps/build/ai-toolkit) |
| AWS | uvx, AWS CLI, IAM credentials | [Server guide](https://docs.aws.amazon.com/agent-toolkit/latest/userguide/getting-started-aws-mcp-server.html) |
| Alation | uvx and Alation service-account integration | [Server guide](https://github.com/Alation/alation-ai-agent-sdk/tree/main/python/dist-mcp) |
| Expedia Travel Recommendations | uvx and Expedia Travel Recommendations API key | [Server guide](https://github.com/ExpediaGroup/expedia-travel-recommendations-mcp) |

## Authentication Notes

- Google Workspace uses the community `workspace-mcp` server. Create a Google
  Cloud OAuth app, enable the APIs you need, and follow the server's sign-in
  instructions.
- Microsoft 365 uses Softeria's community server for work or school accounts.
- Firebase uses your Firebase CLI sign-in.
- dbt server completes its own browser sign-in and requires an account with a
  static subdomain.
- MongoDB starts with `--readOnly`.
- Redis takes a connection URL such as
  `rediss://default:password@your-redis-host:6379/0`.
- Azure uses your Azure CLI sign-in.
- BigQuery uses Google Application Default Credentials.
- Salesforce DX uses your authorized default target org.
- AWS uses the official SigV4 proxy with your IAM credentials.
- Alation uses a service-account integration.
- Tableau uses a personal access token and requires a site name for Tableau Cloud.

## Related

- [MCP Local](./mcp-local.md) — Configured local MCP servers
- [MCP Presets](./mcp-presets.md) — Hosted MCP service presets
- [MCP Configuration](./mcp-config.md) — MCP configuration
- [MCP Tools](./mcp-tools.md) — Tool discovery and safety
