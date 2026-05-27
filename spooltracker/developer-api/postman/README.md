# Postman collection

A ready-to-import Postman collection and environments for the SpoolTracker Developer API.

## Files

| File | What it is |
|---|---|
| `SpoolTracker-Developer-API.postman_collection.json` | The collection — folders for Auth, REST, and GraphQL, plus a pre-request script that fetches and caches an access token automatically. |
| `SpoolTracker-Production.postman_environment.json` | Pre-filled URLs for production (`spooltracker-api.victaulic.com`). |

## Setup (60 seconds)

1. In Postman: **File → Import** and drop both JSON files in.
2. Top-right environment dropdown → pick **SpoolTracker Production**.
3. Click the environment name → **Edit** → paste your `client_id` and `client_secret` into the `clientId` and `clientSecret` variables. Save.
4. Open any request under **REST** and hit **Send**. The pre-request script will fetch a token, cache it, and attach it as `Authorization: Bearer …` automatically.

The cached token is reused until it has under 60 seconds of life remaining, then auto-refreshed. You should not need to touch the `accessToken` or `tokenExpiresAt` variables by hand.

## Sharing with developers

Both environment files ship with `clientId` and `clientSecret` **blank**, and `clientSecret` is marked as a `secret`-type variable so Postman masks it in the UI. It is safe to commit these files to a repo or share them through Slack — developers fill in their own credentials after import.

> **Do not** export your environment after filling in the secret and re-share that file. Postman will warn you, but the export still contains the value in the `current value` field.

## Regenerating the entity list

DAB serves an auto-generated OpenAPI 3.0 spec at:

```
GET {{baseUrl}}/api/openapi
```

To regenerate a request stub for every entity (handy after adding new entities to `dab-config.json`):

1. In Postman: **File → Import → Link**
2. Paste `https://spooltracker-api.victaulic.com/api/openapi`
3. Postman generates a new collection with one folder per entity. Copy the requests you want into the maintained collection.

The OpenAPI spec covers REST only — the GraphQL surface is documented via introspection at `{{baseUrl}}/graphql` (introspection is enabled in all environments).
