# n8n-amazon-automation

N8N workflows for Amazon SP-API integration, built as part of a team project at WWTradeGroup LLC.

## What this does

Amazon's SP-API doesn't return reports instantly — you request a report, then wait for it to be generated, then download it. These workflows handle that full cycle automatically on a schedule.

**Three workflows included:**

| File | Description |
|---|---|
| `amazon-reports-sync.json` | Requests Amazon reports, waits for readiness, downloads and saves to PostgreSQL |
| `inventory-sync.json` | Syncs FBA inventory data across multiple marketplaces (USA, Canada) |
| `shipments-ingest.json` | Ingests shipment updates from an internal API into PostgreSQL |

## Key features

- Scheduled triggers — runs automatically, no manual intervention
- Error handling — stops gracefully on API errors (404, timeouts, fatal status)
- Multi-marketplace support — separate branches for USA and Canada
- PostgreSQL integration — data goes straight into the database after download

## How to use

1. Import the JSON file into your N8N instance
2. Replace all `YOUR_*` placeholders with your actual credentials:
   - `YOUR_POSTGRES_CREDENTIAL_ID` — your PostgreSQL connection in N8N
   - `YOUR_API_AUTH_CREDENTIAL_ID` — your API authentication credential
   - `YOUR_REDIS_CREDENTIAL_ID` — your Redis connection (used for queue management)
   - `YOUR_N8N_INSTANCE_ID` — your N8N instance identifier
3. Adjust schedule triggers to your preferred times
4. Activate the workflow

## Stack

- [N8N](https://n8n.io) — workflow automation
- PostgreSQL — data storage
- Amazon SP-API — data source

## Screenshots
![WF-1 — [KPI] ACOS, TACOS, LTFS, Overhead Postgre](https://github.com/FelAnalyst/n8n-amazon-automation/blob/main/screenshots/WF-1.jpg)
![WF-2 — Report sync workflow](https://github.com/FelAnalyst/n8n-amazon-automation/blob/main/screenshots/WF-2.jpg)
![WF-3 — Shipments ingest workflow](https://github.com/FelAnalyst/n8n-amazon-automation/blob/main/screenshots/WF-3.jpg)

---

*Part of a larger e-commerce analytics system. Sensitive values (API keys, URLs, account IDs) have been replaced with placeholders.*
