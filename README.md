# Airtable Real-Time Backup Automation (n8n)

Real-time, webhook-triggered backup of Airtable records to a secondary
base — optimized to run in 3–5 API calls per sync, with race-condition
handling and duplicate prevention.

## How It Works
Airtable record change
↓
Webhook fires instantly to n8n
↓
Payload acknowledged immediately (prevents race conditions)
↓
30s debounce — waits for user to finish editing all fields
↓
Upsert logic — checks backup base for existing record
↓
Record synced to backup base (Products / Orders / Customers)
## Engineering Decisions

- **Immediate payload acknowledgment** — Airtable webhooks can fire
  multiple times for a single edit session; acknowledging immediately
  and debouncing downstream avoids dropped or duplicate triggers
- **30-second debounce window** — prevents syncing a record mid-edit,
  when only some fields have been filled in
- **Upsert over insert** — avoids duplicate records when the same
  change triggers multiple webhook events
- **3–5 API call budget** — deliberately optimized against Airtable's
  rate limits rather than calling the API per field or per table naively

## Tech Stack

n8n · Airtable API · Webhooks

## Setup

1. Import `workflow.json` into n8n
2. Replace API token and Base/Table IDs in the Code node
3. Point an Airtable webhook to the n8n webhook URL
4. Activate the workflow

## Tables Synced

Products · Orders · Customers — extendable to additional tables by
duplicating the sync branch in the workflow.
