# 📊 Sales Data Pipeline (n8n)

An automated ETL-style pipeline built in **n8n** that pulls raw sales order data from an API, transforms it, generates regional analysis, and delivers a CSV report — all without manual intervention.

<img width="1069" height="448" alt="image" src="https://github.com/user-attachments/assets/96edb983-4dc0-4cb1-86c9-8575d462b8ad" />
<img width="716" height="414" alt="image" src="https://github.com/user-attachments/assets/508c0134-e9ee-4170-9ee5-7dfbeee14bda" />


## 🧠 What it does

This workflow simulates a real-world sales operations pipeline:

1. **Fetch** — Pulls raw order data from an API.
2. **Transform** — Splits the batch into individual orders and calculates each order's total (quantity × unit price).
3. **Aggregate & send** — Combines all processed orders and sends them to a downstream endpoint.
4. **Filter & analyze** — Filters only *delivered* orders, then summarizes total, count, and average order value **by region**.
5. **Report generation** — Converts the regional analysis into a CSV file, attaches metadata (timestamp), and sends the final report as a downloadable file.

## 🏗️ Pipeline flow

```
Manual Trigger
   → Get Sales Data (API)
   → Split Orders
   → Calculate Order Totals
   ├── Aggregate All Orders → Send Orders
   └── Filter: Delivered Only
        → Summarize by Region (sum / count / average)
        → Rename Fields
        ├── Aggregate Regions → Send Analysis
        └── Add Report Metadata
             → Convert to CSV
             → Send Report
```

## 🛠️ Tech stack

| Component | Tool used |
|---|---|
| Workflow engine | [n8n](https://n8n.io) |
| Data transformation | n8n Set, Split Out, Aggregate, Summarize nodes |
| Output format | CSV (via Convert to File) |
| Delivery | HTTP Request (webhook-based) |

## 📦 Setup

1. Import `workflow.json` into your n8n instance.
2. Replace the API endpoint URLs and authentication headers with your own data source.
3. Run the workflow manually, or attach a schedule trigger for automated daily/weekly reports.

## 📌 Why this project

Built as part of n8n Academy's *Essentials: Your First Workflows* course — a hands-on exercise in building a real data pipeline: fetching, transforming, branching logic, aggregation, and file-based reporting.

---

