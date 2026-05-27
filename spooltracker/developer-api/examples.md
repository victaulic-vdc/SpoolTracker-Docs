# Examples

This page walks through realistic queries using both the REST and GraphQL surfaces. All examples assume you have a valid access token — see [Authentication](authentication.md) if you do not.

For brevity, `$TOKEN` below stands for the access token from your token-exchange step. The base URL `$API` is `https://spooltracker-api.victaulic.com`.

## Entities at a glance

The API exposes these entities. Most have plural REST paths under `/api/<Entity>` (singular noun) and plural GraphQL fields (camelCase plural).

| Entity | Description |
|---|---|
| `Organization` | The top-level customer entity |
| `Project` | A project within an organization |
| `Spool` | A single fabricated piping spool |
| `Scan` | A scan event recorded against a spool (status update, QC check, etc.) |
| `ScanImage` | Images attached to a scan |
| `BillOfMaterial` | A component/part within a spool's BOM |
| `ProjectScanType` | A project's configured workflow steps (e.g. "Fabrication", "Shipped") |
| `Revision` | A revision of a project's 3D model |
| `SpoolGroup` | A user-defined grouping of spools |
| `SpoolGroupMapping` | Junction between `SpoolGroup` and `Spool` |
| `ProjectCloud` | Link from a project to an Autodesk cloud model |
| `ThreeDSpoolFile` | A 3D file linked to a spool |
| `SpoolLink` | External links attached to a spool |

## REST examples

### List all projects you can see

```bash
curl "$API/api/Project" \
  -H "Authorization: Bearer $TOKEN"
```

Response shape:

```json
{
  "value": [
    {
      "projectId": 7,
      "projectName": "Sands Casino",
      "projectCode": "boT09m3R",
      "projectNumber": "123456789",
      "organizationId": 1,
      "CreatedAt": "2025-01-30T15:25:53",
      "ModifiedAt": "2026-03-25T21:51:41"
    }
  ]
}
```

### Filter spools by project (OData `$filter`)

```bash
curl "$API/api/Spool?\$filter=projectId%20eq%207&\$first=10" \
  -H "Authorization: Bearer $TOKEN"
```

### Select only the fields you need

```bash
curl "$API/api/Spool?\$select=spoolId,spoolName,area,level&\$first=5" \
  -H "Authorization: Bearer $TOKEN"
```

### Most recent scans, newest first

```bash
curl "$API/api/Scan?\$orderby=timestamp%20desc&\$first=20" \
  -H "Authorization: Bearer $TOKEN"
```

### Combining filters

OData supports `and`, `or`, `contains()`, `startswith()`, `endswith()`:

```bash
# Active spools (BIT = 1) in Level 1
curl "$API/api/Spool?\$filter=active%20eq%201%20and%20level%20eq%20'Level%201'&\$first=20" \
  -H "Authorization: Bearer $TOKEN"

# Spool name contains "CHRS"
curl "$API/api/Spool?\$filter=contains(spoolName,'CHRS')" \
  -H "Authorization: Bearer $TOKEN"
```

> **BIT columns are integers in REST.** Filter with `active eq 1`, not `active eq true` — REST treats SQL BIT columns as `Edm.Int32`. GraphQL treats them as booleans (see below).

### Pagination

REST returns 100 records per page by default. Use `$first` to cap (max 1000) and follow the `nextLink` if present:

```json
{
  "value": [ /* up to 100 records */ ],
  "nextLink": "https://spooltracker-api.victaulic.com/api/Spool?$first=100&$after=..."
}
```

## GraphQL examples

The GraphQL endpoint is `POST $API/graphql`. Set:

- `Content-Type: application/json`
- `Authorization: Bearer $TOKEN`

The body is JSON: `{"query": "...", "variables": {...}}`.

### List projects with their spool names in one round trip

```graphql
{
  projects(first: 5) {
    items {
      projectId
      projectName
      spools(first: 10) {
        items {
          spoolId
          spoolName
        }
      }
    }
  }
}
```

### Filter by a specific field

GraphQL supports rich filter operators: `eq`, `neq`, `gt`, `gte`, `lt`, `lte`, `contains`, `notContains`, `startsWith`, `endsWith`, `in`, `isNull`.

```graphql
{
  spools(filter: { spoolName: { eq: "CHRS-02" } }) {
    items {
      spoolId
      spoolName
      area
      level
      scans(first: 5, orderBy: { timestamp: DESC }) {
        items {
          scanId
          timestamp
          notes
          deviceName
        }
      }
    }
  }
}
```

### Combine filters with `and` / `or`

```graphql
{
  spools(filter: {
    and: [
      { projectId: { eq: 7 } },
      { active: { eq: true } }
    ]
  }) {
    items { spoolId spoolName }
  }
}
```

> **BIT columns are booleans in GraphQL.** Inside a `filter`, write `{ active: { eq: true } }`. In response payloads, `active` is `true` or `false`. (REST uses `1`/`0` for the same column — protocol-dependent behavior.)

### Project + spool BOM in one query

A particularly useful GraphQL pattern: traverse from a project down through spools to their bill of materials, all in one request.

```graphql
{
  projects(filter: { projectId: { eq: 7 } }) {
    items {
      projectName
      spools(first: 50) {
        items {
          spoolName
          billOfMaterials {
            items {
              itemDescription
              itemSize
              manufacturer
              partNumber
              itemCount
            }
          }
        }
      }
    }
  }
}
```

### Curl

```bash
curl -X POST "$API/graphql" \
  -H "Authorization: Bearer $TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"query":"{ projects(first:1) { items { projectId projectName } } }"}'
```

### Python (`requests`)

```python
import requests

resp = requests.post(
    "https://spooltracker-api.victaulic.com/graphql",
    headers={"Authorization": f"Bearer {token}", "Content-Type": "application/json"},
    json={
        "query": """
        {
          projects(first: 5) {
            items { projectId projectName }
          }
        }
        """
    },
)
resp.raise_for_status()
data = resp.json()["data"]["projects"]["items"]
```

## Field naming reference

The schema preserves SQL column casing, so different fields use different conventions:

| Pattern | Example fields |
|---|---|
| **camelCase** | `spoolId`, `projectId`, `spoolName`, `organizationId`, `cloudProjectId` |
| **PascalCase** | `CreatedAt`, `ModifiedAt` (audit timestamps) |
| **PascalCase with underscore** | `Settings_EnableThreeDSpools`, `Settings_DisableCodeAccess` |

Field names are **case-sensitive** in both REST `$filter` and GraphQL. `CreatedAt` will work; `createdAt` will return a "field not found" error.

To discover the exact fields on an entity, use GraphQL introspection:

```graphql
{ __type(name: "Spool") { fields { name type { name } } } }
```

Or fetch the auto-generated OpenAPI document at `$API/api/openapi` and inspect the `components.schemas` section.

## Error responses

### REST errors

```json
{
  "error": {
    "code": "AuthorizationCheckFailed",
    "message": "Authorization Failure: Access Not Allowed.",
    "status": 403
  }
}
```

Common cases:

- `401 Unauthorized` — missing or expired bearer token
- `403 Forbidden` — token is valid but the API key was revoked, or you attempted a write operation (the API is read-only)
- `400 BadRequest` — malformed `$filter` (most common: case-sensitive field names, type mismatches like `active eq true` on an integer column)

### GraphQL errors

GraphQL always returns HTTP 200 but with an `errors` array:

```json
{
  "errors": [
    {
      "message": "The field `name` does not exist on the type `Spool`.",
      "extensions": { "code": "..." }
    }
  ],
  "data": null
}
```

When you see a "field does not exist" error, double-check casing first — it is the most common cause.

## What's next

- Review [Authentication](authentication.md) if you have not already
- Browse the auto-generated OpenAPI spec at `$API/api/openapi` for the complete REST entity reference
- For GraphQL, the schema is introspectable — point any GraphQL client (Postman, Insomnia, Apollo Studio) at `$API/graphql` with a valid bearer token to explore interactively
