# BrightGauge-Grafana / Mgmt Scorecard

Pund-IT management meeting scorecard — Grafana dashboard + n8n workflows.

## Components

| Component | ID | Schedule |
|---|---|---|
| Grafana Dashboard | `mgmt-scorecard` | — |
| Financial Sheet Sync | `cPhrqQQuQvXIZl6b` | Every 4h |
| CW Weekly Sync | `2jpjxYKlgLaToXPk` | Daily 6AM EST |
| Goals Dashboard | `DDPjO4wACkqA27mW` | Hourly |
| Dispatch Dashboard | `heUxpzPiV2FopIJy` | Every 15min |

## Infrastructure

- **Grafana:** 10.255.71.48:3000 (HTTPS, self-signed)
- **n8n:** 10.255.71.46:5678
- **Postgres:** Datasource ID 19 (`efepewosiqxvkd`)
- **Google Sheet (Financials):** `18oYjZymWCYG_sZfOj8iwTgwyYUaMjbx3ijw1a8h_G_M`

## Fix Log

### 2026-03-31 — Dashboard Overhaul (Fixes 1–15)
1. Financial panel — dynamic date headers (replaced hardcoded dates)
2. Financial Sheet Sync — auto-updates Grafana Financial panel headers after sync
3. All week_start/week_date shifted Sunday → Tuesday (meeting day) in DB
4. CW Weekly Sync — Tuesday-start date calculation
5. Projects data preservation (was wiping historical data each run)
6. All 4 panels pivoted with dynamic Tuesday date headers
7. CW Weekly Sync — auto-updates Sales/CS/Projects panel headers after sync
8. SQL syntax fix in 3 weekly panels (CASE/WHEN comma issue)
9. n8n Code node template fix for correct SQL generation
10. Replaced Code node HTTP calls with HTTP Request nodes (Code nodes can't fetch)
11. Removed hanging Grafana update Code nodes
12. Panel SQL made fully dynamic (generic col aliases)
13. Organize field transformations for column labels
14. HTTP Request nodes for Grafana API in both workflows
15. Hairpin NAT fix — extra_hosts in n8n docker-compose, then switched to direct internal HTTPS (https://10.255.71.48:3000)

### Stale Days Bug (Client Liaison)
- Right-side "Days" column overwritten by Notes assignment (row[11] used twice)
- Fixed in both `nOwmwOC6M2dXraXs` and `3jqoWy4dE0jK81cM`
