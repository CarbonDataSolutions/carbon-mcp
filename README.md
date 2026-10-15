# Carbon MCP connector

carbon.talent is a global data and AI talent platform. Verified data talent, ready to interview.

**Listing name:** Carbon  
**Product:** carbon.talent  
**Connector URL:** https://mcp.carbondatasolutions.com/mcp  
**Homepage:** https://www.carbondatasolutions.com/hire  
**App:** https://carbontalent.carbondatasolutions.com  
**Support:** talent@carbondatasolutions.com  
**Privacy:** https://www.carbondatasolutions.com/privacy

## One-line

Hire verified data and AI talent from ChatGPT, Claude, Cline, or any MCP host. Post your role free.

## What it does

Carbon connects carbon.talent to your AI assistant. Search the talent catalog, draft and post a role, review applicants, and move people through Applied, Screened, Interview, and Offer. Writes ask for your confirmation first. Post your role free.

## Features

- Search the talent catalog by skills, experience, and location (first name plus last initial)
- Open a talent profile without contact details, CV, rates, or scores
- Create a role draft and post it when you are ready (confirm on every write)
- List your roles and open any role for detail
- List applicants for a role and read an applicant summary (no contact details, CV, rates, or scores)
- Move an applicant to Applied, Screened, Interview, or Offer (never Hired via the connector)
- Sign in with OAuth; company-scoped data only; disconnect any time from your Carbon account or the host

## Tools

Static declarations for directory indexing also live in `server.json` and `server-card.json` (name plus description). Runtime tool schemas come from the live connector via `tools/list`.

| Tool | Access | Short description |
|------|--------|-------------------|
| `whoami` | read | Show the connected carbon.talent hiring account (name, email, company, verification) |
| `list_roles` | read | List your company's roles with status, location, and applicant counts |
| `get_role` | read | Get one of your roles in full, including applicants by stage |
| `create_role_draft` | write, confirm | Create a private role draft for your company |
| `post_role` | write, confirm | Submit a draft role for publishing |
| `list_applicants` | read | List applicants for one of your roles with stage and applied time |
| `get_applicant_summary` | read | Summarise one applicant without contact details, CV, rates, or scores |
| `move_applicant_stage` | write, confirm | Move an applicant to Applied, Screened, Interview, or Offer (never Hired via the connector) |
| `search_talent` | read | Search the talent catalog by skills, experience, location, or keywords (first name plus last initial) |
| `get_talent_profile` | read | Get one talent catalog profile by the id returned from search |

## Connect (any MCP host)

Use Streamable HTTP at:

`https://mcp.carbondatasolutions.com/mcp`

Sign in with OAuth to a carbon.talent company account. See [llms-install.md](./llms-install.md) for host-specific steps.

### Cline

**Remote Servers UI**

1. In the Cline panel, open **MCP Servers** → **Remote Servers**.
2. Server Name: `carbon`
3. Server URL: `https://mcp.carbondatasolutions.com/mcp`
4. Transport Type: **Streamable HTTP**
5. Add Server, then sign in when the OAuth window opens.

**Or edit `cline_mcp_settings.json`**

- CLI: `~/.cline/data/settings/cline_mcp_settings.json`
- IDE: MCP Servers → Configure → Configure MCP Servers

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

Keys match [Cline's MCP docs](https://docs.cline.bot/mcp/mcp-overview): `type` must be `"streamableHttp"` (omitting it falls back to legacy SSE). No secrets in this file — OAuth handles sign-in.

### Cursor / Open Plugins `.mcp.json`

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

## Offers

- Post your role free

## Honest claim rules

Do not say Carbon is live inside ChatGPT, Claude, Copilot, Gemini, or Cursor directories until that directory lists it. Safe today: the MCP endpoint is live and hosts can connect by URL where custom connectors are allowed.

## License

MIT — see [LICENSE](./LICENSE). This repo is connector metadata and install docs for the hosted server; the product itself stays on carbon.talent.
