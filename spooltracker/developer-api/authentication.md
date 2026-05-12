# Authentication

The Developer API uses **OAuth 2.0 client credentials** — a standard two-step flow:

1. Exchange your `client_id` + `client_secret` for an access token at the token endpoint
2. Send that token in the `Authorization` header on every API request

Tokens are JWTs valid for **1 hour**. Cache and reuse them — do not request a new token on every API call.

## Endpoints

| Purpose | URL (production) |
|---|---|
| Token endpoint | `https://spooltracker.victaulic.com/connect/token` |
| API base URL | `https://spooltracker-api.victaulic.com` |

> **The token endpoint is on the dashboard host, not the API host.** This is intentional — the dashboard runs the OAuth server; the API host just validates the tokens it issues.

For UAT, substitute `spooltracker-uat.victaulic.com` and `spooltracker-api-uat.victaulic.com`.

## Step 1 — Get a token

### curl

```bash
curl -X POST https://spooltracker.victaulic.com/connect/token \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "grant_type=client_credentials" \
  -d "client_id=stk_live_YOUR_CLIENT_ID" \
  -d "client_secret=YOUR_CLIENT_SECRET" \
  -d "scope=api"
```

Response:

```json
{
  "access_token": "eyJhbGciOiJSUzI1NiIsInR5cCI6ImF0K2p3dCIsImtpZCI6Ii4uLiJ9...",
  "token_type": "Bearer",
  "expires_in": 3600
}
```

### Python

```python
import os
import requests

resp = requests.post(
    "https://spooltracker.victaulic.com/connect/token",
    data={
        "grant_type": "client_credentials",
        "client_id": os.environ["SPOOLTRACKER_CLIENT_ID"],
        "client_secret": os.environ["SPOOLTRACKER_CLIENT_SECRET"],
        "scope": "api",
    },
)
resp.raise_for_status()
token = resp.json()["access_token"]
```

### Node.js

```javascript
const params = new URLSearchParams({
  grant_type: "client_credentials",
  client_id: process.env.SPOOLTRACKER_CLIENT_ID,
  client_secret: process.env.SPOOLTRACKER_CLIENT_SECRET,
  scope: "api",
});

const resp = await fetch("https://spooltracker.victaulic.com/connect/token", {
  method: "POST",
  headers: { "Content-Type": "application/x-www-form-urlencoded" },
  body: params,
});
const { access_token } = await resp.json();
```

## Step 2 — Call the API

Attach the token to every request:

```bash
curl https://spooltracker-api.victaulic.com/api/Project \
  -H "Authorization: Bearer eyJhbGciOiJSUzI1NiIs..."
```

See [Examples](examples.md) for concrete query patterns.

## Token lifetime and caching

Tokens are valid for **1 hour** (`expires_in: 3600`). Do **not** request a new token per request — you will hit rate limits.

Recommended pattern: cache the token in memory and refresh when it has less than ~5 minutes remaining.

```python
import time

_token = None
_token_expires_at = 0

def get_token():
    global _token, _token_expires_at
    if _token and _token_expires_at - time.time() > 300:
        return _token

    resp = requests.post(
        "https://spooltracker.victaulic.com/connect/token",
        data={
            "grant_type": "client_credentials",
            "client_id": os.environ["SPOOLTRACKER_CLIENT_ID"],
            "client_secret": os.environ["SPOOLTRACKER_CLIENT_SECRET"],
            "scope": "api",
        },
    )
    resp.raise_for_status()
    body = resp.json()
    _token = body["access_token"]
    _token_expires_at = time.time() + body["expires_in"]
    return _token
```

## What's in the token

The access token is a signed JWT. You can decode it (without verifying — the API host does that for you) to inspect its claims:

| Claim | Value |
|---|---|
| `iss` | The dashboard host that issued it |
| `aud` | `spooltracker-api` |
| `sub` | An internal service account ID tied to your API key |
| `scope` | `api` |
| `role` | `ApiKey` |
| `exp` | Unix timestamp when the token expires |

You do not need to inspect the token to use it — just pass it through to the API.

## Data scope and row-level security

The token's `sub` claim identifies a service account that represents your API key. When the API processes your request, row-level security (RLS) filters every query against the projects and organization that key is provisioned for.

In practical terms: a query for `/api/Project` returns **every project in your organization** — not other organizations' projects, not projects you have not been given access to. No client-side filtering is required for safety.

## Errors

| Status | Meaning | Common cause |
|---|---|---|
| `400` | Bad request format | Missing `grant_type` parameter or malformed body |
| `401` | Invalid or expired token | Token is older than 1 hour, or signature does not validate |
| `403` | Authorization failure | Missing `Authorization` header, or the API key was revoked |

If the token endpoint returns `400 invalid_client`, double-check the `client_id` and `client_secret` — they are case-sensitive.

## Revoking a key

If a key is compromised:

1. Sign in to the dashboard as an organization Admin
2. Go to **Organization Settings → API Keys**
3. Click the trash icon next to the affected key

The key is revoked immediately on the server. Any tokens already issued will continue to work until they expire (up to 1 hour) — there is currently no way to revoke individual access tokens before expiry. Plan accordingly: if you suspect a leak, rotate the key *and* understand there may be a one-hour window where the leaked token still functions.
