# SpoolTracker Developer API

The SpoolTracker Developer API gives third-party applications **read-only programmatic access** to your organization's spool tracking data — projects, spools, scans, bill of materials, revisions, and 3D model file references.

Typical use cases:

- Pull scan progress into a BI dashboard
- Sync spool status into an ERP or fabrication scheduling system
- Build custom reports across projects within an organization

> **Read-only by design.** The Developer API exposes data you can already see in the web dashboard — it does not allow creating, updating, or deleting records. Spool creation and scan recording remain in VTFR and the mobile app.

## Quick links

- [Authentication](authentication.md) — how to mint a token from your API key
- [Examples](examples.md) — concrete REST and GraphQL queries

## Base URL

| Environment | Host |
|---|---|
| Production | `https://spooltracker-api.victaulic.com` |
| UAT | `https://spooltracker-api-uat.victaulic.com` |

The token endpoint lives on the main dashboard host (`https://spooltracker.victaulic.com/connect/token` for production), not the API host. See [Authentication](authentication.md).

## Two query styles

The same data is exposed through two protocols. Use whichever fits your stack.

- **REST** at `/api/<Entity>` — paginated, filterable with OData syntax (`$filter`, `$orderby`, `$first`, `$select`). Best for simple single-entity queries.
- **GraphQL** at `/graphql` — single endpoint, query nested relationships in one round trip. Best for fetching a project plus its spools plus their scans in one request.

Both surfaces expose the same entities (`Project`, `Spool`, `Scan`, `BillOfMaterial`, `Revision`, `ProjectScanType`, `SpoolGroup`, `ProjectCloud`, `ScanImage`, `ThreeDSpoolFile`, `SpoolLink`, `SpoolGroupMapping`, `Organization`). See [Examples](examples.md) for both styles.

## Data scope

API keys are minted at the **organization** level. A key returns only data from projects the issuing organization has access to — the filtering is enforced at the database level via row-level security, so there is no way to accidentally see another organization's projects.

If you have access to multiple organizations and need to query across them, you currently need one key per organization.

## Getting a key

1. Sign in to the dashboard as an organization Admin
2. Navigate to **Organization Settings → API Keys**
3. Click **Create API Key**, give it a descriptive name (e.g. "ERP sync — production")
4. **Copy the client secret immediately** — it is shown once and cannot be recovered. Store it somewhere safe (a secrets manager, environment variable, etc.).

You will receive a `client_id` (looks like `stk_live_XXXXXXXX`) and a `client_secret`. The next page, [Authentication](authentication.md), shows how to exchange them for an access token.

## Rate limits and token lifetime

- Access tokens are valid for **1 hour** after issue.
- The token endpoint is rate-limited — request a new token at most a few times per hour, not per request. Cache and reuse the token until it nears expiry.
- The API itself has standard pagination caps: REST returns 100 records per page by default, 1000 maximum (`$first=1000`).

## Support

If you hit a `401`, `403`, or unexpected `500`, double-check:

1. The `Authorization: Bearer <token>` header is set
2. The token is less than 1 hour old
3. The entity name and field casing match (the schema preserves SQL casing — `spoolId` is camelCase, `CreatedAt` is PascalCase)

If you are still stuck, contact Victaulic VDC with your `client_id` (never the secret) and a sample request.
