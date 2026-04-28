# N8N Connection Guide

## Working API Access

| Setting | Value |
|---------|-------|
| **Base URL** | `https://n8n.pund-it.ca` |
| **API Version** | `/api/v1/` |
| **Full URL** | `https://n8n.pund-it.ca/api/v1/` |
| **API Key** | Stored in `/root/.openclaw/secrets/n8n-api-key` |
| **Header** | `X-N8N-API-KEY: <token>` |

## How to Connect

```bash
# Set the API key
N8N_API_KEY=$(cat /root/.openclaw/secrets/n8n-api-key)

# List all workflows
curl -s "https://n8n.pund-it.ca/api/v1/workflows" \
  -H "X-N8N-API-KEY: $N8N_API_KEY" | jq '.'

# Get specific workflow
curl -s "https://n8n.pund-it.ca/api/v1/workflows/WORKFLOW_ID" \
  -H "X-N8N-API-KEY: $N8N_API_KEY" | jq '.'

# Get workflow execution history
curl -s "https://n8n.pund-it.ca/api/v1/executions?workflowId=WORKFLOW_ID" \
  -H "X-N8N-API-KEY: $N8N_API_KEY" | jq '.'
```

## Important Notes

- **Endpoint:** Must use `/api/v1/` not `/rest/`
- **Previous attempts failed** because we used wrong endpoints (`/rest/workflows`)
- **Working verified:** 2026-04-26

## Related Workflows for BrightGauge-Grafana

| Workflow Name | ID | Schedule |
|--------------|-----|----------|
| Mgmt Scorecard - Financial Sheet Sync | `cPhrqQQuQvXIZl6b` | Every 4h |
| Mgmt Scorecard - CW Weekly Sync | `2jpjxYKlgLaToXPk` | Daily 6AM EST |

---
*Last updated: 2026-04-26*
