<p align="center"><img src="assets/logo.png" width="72" alt="OpsKitty logo"></p>

<h1 align="center">OpsKitty MCP</h1>

<p align="center">Uptime checks for sites and APIs, status pages, cron heartbeats, Lighthouse and SEO audits, run from your AI app.</p>

<p align="center">
  <a href="https://www.opskitty.com">Website</a> ·
  <a href="https://www.opskitty.com/docs">Docs</a> ·
  <a href="https://www.opskitty.com/pricing">Pricing</a> ·
  <a href="https://registry.modelcontextprotocol.io/v0.1/servers?search=com.opskitty">MCP Registry</a>
</p>

<p align="center">
  <a href="https://cursor.com/en/install-mcp?name=opskitty&config=eyJ1cmwiOiJodHRwczovL21jcC5vcHNraXR0eS5jb20vbWNwIn0="><img src="https://cursor.com/deeplink/mcp-install-dark.svg" alt="Add OpsKitty to Cursor" height="32"></a>
  <a href="https://vscode.dev/redirect/mcp/install?name=opskitty&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.opskitty.com%2Fmcp%22%7D"><img src="https://img.shields.io/badge/VS_Code-Install_server-0098FF?style=for-the-badge&logo=visualstudiocode&logoColor=white" alt="Install OpsKitty in VS Code" height="32"></a>
</p>

OpsKitty is a hosted MCP server at `https://mcp.opskitty.com/mcp`. Connect it to Claude, ChatGPT, Cursor or any MCP client and set up monitoring by asking for it, instead of clicking through a dashboard.

This repo holds the install files for Claude Code, Codex, Cursor and other clients. The server itself is hosted by OpsKitty, so there is nothing to run.

## What you can ask

- "Monitor https://example.com and its /api/health endpoint every minute, and alert me on Slack if either goes down."
- "Create a public status page for my API with the checkout and login endpoints on it."
- "Set up a heartbeat for my nightly backup job and tell me the URL to ping."
- "Run Lighthouse on my homepage and list the three fixes that would help most."
- "Audit the SEO of my pricing page and submit the new blog URLs for indexing."

## Install

### Claude Code

```bash
claude plugin marketplace add capaxelabs/plugins
claude plugin install opskitty@capaxe
```

Then run `/mcp` in Claude Code, pick **opskitty** and sign in to OpsKitty.

Prefer a plain MCP server over a plugin:

```bash
claude mcp add --transport http opskitty https://mcp.opskitty.com/mcp
```

### Claude.ai and Claude Desktop

1. Open **Settings > Connectors** and select **Add custom connector**.
2. Name it **OpsKitty** and paste `https://mcp.opskitty.com/mcp`.
3. Select **Connect** and sign in.

### ChatGPT

1. Open **Settings > Apps & Connectors > Advanced settings** and turn on **Developer mode**.
2. In **Apps & Connectors**, select **Create**.
3. Name it **OpsKitty**, paste `https://mcp.opskitty.com/mcp` and choose **OAuth**.

### Codex

```bash
codex plugin marketplace add capaxelabs/plugins
codex plugin add opskitty@capaxe
```

Or add it as a plain MCP server:

```bash
codex mcp add opskitty --url https://mcp.opskitty.com/mcp
```

### Cursor

Use the **Add to Cursor** button above, or add to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "opskitty": { "url": "https://mcp.opskitty.com/mcp" }
  }
}
```

### VS Code

Use the **Install** button above, or add to `.vscode/mcp.json`:

```json
{
  "servers": {
    "opskitty": { "type": "http", "url": "https://mcp.opskitty.com/mcp" }
  }
}
```

### Any other MCP client

| Setting | Value |
| --- | --- |
| URL | `https://mcp.opskitty.com/mcp` |
| Transport | Streamable HTTP |
| Auth | OAuth |

## Tools

About 100 tools, grouped by what they cover:

| Area | Examples |
| --- | --- |
| Websites and endpoints | `create_website`, `create_endpoint`, `test_endpoint`, `get_endpoint_monitoring`, `get_monitoring_stats` |
| Alerts and integrations | `create_alert`, `create_integration`, `test_integration`, `list_alert_events` |
| Status pages and incidents | `create_status_page`, `create_status_component`, `create_status_incident`, `post_status_incident_update` |
| Cron heartbeats | `create_heartbeat`, `get_heartbeat`, `rotate_heartbeat_url` |
| Performance and SEO | `run_lighthouse`, `run_seo_check`, `run_site_seo_audit`, `audit_page_seo` |
| Search indexing and AI visibility | `submit_urls_for_indexing`, `check_index_status`, `run_ai_visibility_test` |
| Team and billing | `list_organizations`, `invite_member`, `get_billing`, `list_plans` |

Tools that change or delete things are marked as such, so your AI app asks before it runs them.

## Links

- Website: https://www.opskitty.com
- Docs: https://www.opskitty.com/docs
- Pricing: https://www.opskitty.com/pricing
- Privacy: https://www.opskitty.com/pages/privacy
- Terms: https://www.opskitty.com/pages/tos
- Support: https://www.opskitty.com/contact

## Files in this repo

| File | Read by |
| --- | --- |
| `.claude-plugin/plugin.json`, `.mcp.json` | Claude Code |
| `plugin.json`, `mcp.json` | Codex and other [Agent Plugins](https://agent-plugins.org) clients |
| `.cursor-plugin/plugin.json` | Cursor |
| `server.json` | [Official MCP Registry](https://registry.modelcontextprotocol.io) |
| `glama.json` | [Glama](https://glama.ai/mcp/servers) |

## License

The files in this repo are MIT licensed. Use of the OpsKitty service is covered by its [terms](https://www.opskitty.com/pages/tos).
