# Install carbon.talent MCP (remote)

carbon.talent is a global data and AI talent platform. Verified data talent, ready to interview.

This repository documents a **hosted remote MCP server**. There is no local install and no dependencies. You connect over Streamable HTTP and sign in with OAuth to a carbon.talent company account.

## Endpoint

- **URL:** `https://mcp.carbondatasolutions.com/mcp`
- **Transport:** Streamable HTTP
- **Auth:** OAuth (browser sign-in to a carbon.talent company account)

## Cline

### Option A — Remote Servers UI

1. In the Cline panel, open **MCP Servers**.
2. Open the **Remote Servers** tab.
3. Enter **Server Name:** `carbon`
4. Enter **Server URL:** `https://mcp.carbondatasolutions.com/mcp`
5. Choose **Transport Type:** Streamable HTTP
6. Click **Add Server**.
7. Sign in when Cline opens the OAuth window.

### Option B — `cline_mcp_settings.json`

Edit your MCP settings file:

- **CLI:** `~/.cline/data/settings/cline_mcp_settings.json` (or `CLINE_MCP_SETTINGS_PATH`)
- **IDE:** MCP Servers → Configure → **Configure MCP Servers**

```json
{
  "mcpServers": {
    "carbon": {
      "type": "streamableHttp",
      "url": "https://mcp.carbondatasolutions.com/mcp",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

Keys (`type`, `url`, `disabled`, `autoApprove`) match [Cline MCP docs](https://docs.cline.bot/mcp/mcp-overview). Use `"type": "streamableHttp"` (camelCase). Omitting `type` defaults to legacy SSE.

Sign in when Cline opens the OAuth window. No API keys or secrets go in this file.

### CLI

```bash
cline mcp add carbon https://mcp.carbondatasolutions.com/mcp --transport http --yes
```

Then authorize if prompted (`Authorize OAuth` in `cline mcp`).

## Cursor / Open Plugins

`.mcp.json` (note Cursor uses `streamable-http`, not Cline's `streamableHttp`):

```json
{
  "mcpServers": {
    "carbon": {
      "type": "streamable-http",
      "url": "https://mcp.carbondatasolutions.com/mcp"
    }
  }
}
```

## Any MCP host

Connect to `https://mcp.carbondatasolutions.com/mcp` with Streamable HTTP and complete OAuth for a carbon.talent company account.

## Links

- Hire: https://www.carbondatasolutions.com/hire
- App: https://carbontalent.carbondatasolutions.com
- Privacy: https://www.carbondatasolutions.com/privacy
- Support: talent@carbondatasolutions.com
