# 🔄 Airtable Real-Time Backup Automation (n8n)

An optimized n8n workflow that automatically backs up Airtable 
records across bases using webhooks — in just 3–5 API calls.

## ⚙️ What It Does
- Triggers instantly on any Airtable record change (webhook)
- Syncs Products, Orders & Customers to a backup base
- Prevents duplicates using upsert logic
- Handles race conditions by acknowledging payloads immediately
- Waits 30s for users to finish filling fields before syncing

## 🛠️ Tools Used
- n8n (workflow automation)
- Airtable API
- Webhooks

## 🚀 How to Use
1. Import `airtable-backup-workflow.json` into your n8n instance
2. Replace the API token and Base/Table IDs in the Code node
3. Set up your Airtable webhook pointing to the n8n webhook URL
4. Activate the workflow

## 📌 Key Features
- ✅ 3–5 API calls only (highly optimized)
- ✅ Upsert logic — no duplicate records
- ✅ Parallel execution safe
- ✅ Works for multiple tables simultaneously
