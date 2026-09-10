# Victaulic SpoolTracker

SpoolTracker is a smartphone solution that enables Installation Engineers to digitally trace and track spool installation status using QR codes, replacing manual tracking processes. It includes mobile apps for Android and iOS, a web dashboard for project administration, and integration with Victaulic Tools for Revit (VTFR).

---

## Mobile App

Guides for the SpoolTracker mobile application on Android and iOS.

- [PWA-Installation](mobile-app/pwa-install.md) - Instructions for installing Spooltracker's PWA on various devices
- [App User Guide](mobile-app/pwa-userguide.md) — Day-to-day usage: logging in, scanning spools, working offline, and finding past scans
- [Getting Started](mobile-app/getting-started.md) — Introduction, user roles, features, assumptions, and offline usage
- [Login & Dashboard](mobile-app/login-and-dashboard.md) — Login flow, code suggestions, scan history, filtering, settings, and logout
- [Scan Details](mobile-app/scan-details.md) — Viewing single and multiple scan records, adding manual scans
- [New Scan](mobile-app/new-scan.md) — Permissions, QR scanning, scan form, timer, photos, and confirm/cancel

## Web Dashboard

Guides for the SpoolTracker web dashboard at [spooltracker.victaulic.com](https://spooltracker.victaulic.com/).

- [Getting Started](dashboard/getting-started.md) — Account creation, first login, project access, and overview
- [Project Settings](dashboard/project-settings.md) — Configuring scan types (non-timed, timed, repeat) and display ordering

## VTFR Integration

Setting up SpoolTracker within Victaulic Tools for Revit.

- [SpoolTracker Setup](vtfr-integration/spooltracker-setup.md) — Creating projects in VTFR and uploading spools
- [Label Export](vtfr-integration/label-export.md) — Exporting CSV for label printing with Avery templates
- [ACC Connection](vtfr-integration/acc-connection.md) — Autodesk Platform Services app creation, ACC custom integration, and dashboard linking

## Developer API

Read-only programmatic access to your organization's data via API keys.

- [Overview](developer-api/README.md) — What the Developer API is, how to get a key, and what data is exposed
- [Authentication](developer-api/authentication.md) — OAuth client_credentials flow with curl, Python, and Node.js examples
- [Examples](developer-api/examples.md) — REST and GraphQL queries against projects, spools, scans, and bill of materials

## MCP Server

Connect an AI assistant (such as Claude) directly to your SpoolTracker data.

- [Overview](mcp-server/README.md) — What the MCP server does, how to connect, how permissions work, and troubleshooting
