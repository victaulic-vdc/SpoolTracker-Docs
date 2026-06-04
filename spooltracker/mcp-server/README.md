# SpoolTracker MCP Server

The SpoolTracker MCP Server connects AI assistants — such as Claude — directly to your SpoolTracker fabrication data. Instead of clicking through the dashboard, you ask questions in plain language ("which spools in this project still haven't been welded?") and the assistant queries your projects, spools, bills of material, scans, and 3D models on your behalf.

It is built on the [Model Context Protocol](https://modelcontextprotocol.io) (MCP), an open standard for connecting AI assistants to external tools and data.

> **You only ever see your own data.** The MCP server uses the *same login and the same permissions* as the SpoolTracker web dashboard. It cannot see projects or organizations you don't already have access to, and row-level security is enforced at the database level.

## What it can do

Once connected, your assistant can:

- **Answer questions about your data** — query projects, spools, bills of material, scans, revisions, and 3D model references by traversing the relationships between them.
- **Know what you're looking at** — it reads your current project and dashboard page, so "show me the spools on *this* project" just works.
- **Switch projects** — move the active project to pull data from somewhere else, the same way you would in the sidebar.
- **Drive the 3D viewer** — highlight, isolate, hide, zoom, explode, or recolor specific spools and components in the model viewer.
- **Navigate the dashboard** — open the spool list, scan history, overview charts, or a specific spool's detail page in your browser.
- **Send you notifications** — pop a toast in the dashboard to confirm an action or flag a result.

> **Read-first by design.** Day-to-day use is querying and viewing data you can already see in the dashboard. Spool creation and scan recording still happen in VTFR and the mobile app. Some administrative API actions are available, but only to users who already hold the Admin role — the server enforces this.

## Setup

The MCP server runs in production at:

| Environment | MCP endpoint |
|---|---|
| Production | `https://spooltracker-mcp.victaulic.com/mcp` |

You connect to it from an MCP-capable client. The exact steps depend on the client, but the shape is always the same: add the endpoint above as an HTTP/streamable MCP server, then sign in.

### Claude (Desktop, Code, or claude.ai)

1. Open your client's connector / MCP settings.
2. Add a new connector pointing at `https://spooltracker-mcp.victaulic.com/mcp`.
3. A browser window opens to **sign in with your SpoolTracker account** — the same credentials you use for the web dashboard.
4. Approve the requested access. You're connected.

There are **no API keys, client IDs, or secrets to copy.** Authentication uses OAuth 2.0 with Dynamic Client Registration and PKCE — your client registers itself automatically and signs you in through SpoolTracker's normal login page. SpoolTracker never sees your client, and your AI client never sees your password.

> Looking for **key-based, non-interactive access** for an ERP sync or BI dashboard instead of an AI assistant? That's the [Developer API](../developer-api/README.md), not the MCP server.

## How permissions work

- You authenticate as **yourself**. Every query runs with your identity and your access rights.
- Data is **project-scoped**. Spools, BOM, scans, and 3D models all belong to a project, so the assistant works against your *current* project unless you ask it to switch.
- **Row-level security** at the database level guarantees you can only ever read data from projects your organization has access to — there is no way for the assistant to "see around" your permissions.
- **Admin-only actions** (such as direct API calls) are rejected by the server unless your account already holds the Admin role.

## Troubleshooting

**The sign-in window doesn't appear, or login fails.**
Make sure you can log in to [spooltracker.victaulic.com](https://spooltracker.victaulic.com/) in a normal browser first. The MCP server uses the same identity provider — if dashboard login works and MCP login doesn't, disconnect and re-add the connector to restart the OAuth flow.

**"Session expired" or sudden `401` errors after a while.**
Access tokens are short-lived. A well-behaved MCP client refreshes them automatically; if yours doesn't, simply reconnect to sign in again.

**The assistant says it can't find a spool or project.**
It is almost always scoped to the wrong project. Ask it to switch to the correct project by name or code, then retry. Check the project shown in your dashboard sidebar matches what you expect.

**The assistant returns data from the wrong project.**
Same cause — confirm the active project and ask it to switch. All spool/BOM/scan/3D data is project-scoped.

**The 3D viewer doesn't react.**
The viewer must be open in your SpoolTracker browser session for highlight/isolate/explode actions to take effect. Open the `/viewer` page and try again.

## Support

If you're still stuck:

1. Confirm you can sign in to the [web dashboard](https://spooltracker.victaulic.com/).
2. Note which client you're using (Claude Desktop, Claude Code, claude.ai, etc.) and the exact wording of any error.
3. Contact **Victaulic VDC** with those details. **Never share passwords or tokens** in a support request.
