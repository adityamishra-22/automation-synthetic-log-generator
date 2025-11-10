# Synthetic Log Generator

This n8n workflow generates **synthetic execution logs** and appends them to a Google Sheet, creating a realistic dataset for observability dashboards or workflow performance analytics.

---

## 🚀 How It Works
1. **Trigger:** Manual Trigger (run on demand to generate logs).
2. **Generate Logs:** Function node creates 30+ fake workflow runs with randomized:
   - Workflow IDs, run IDs, statuses (`Success`, `Failed`, `Partial`)
   - Durations (100–12,000 ms)
   - Attempts (1–3)
   - Optional error messages (`TimeoutError`, `AuthFailed`)
   - Synthetic payload summaries (like user email + fake company)
3. **Store Logs:** Google Sheets node appends the generated logs to a connected sheet named `AutomationLogs`.

---

## 🧩 Example Schema (`AutomationLogs`)
| Column | Description |
|--------|--------------|
| log_id | Unique UUID for each run |
| workflow_name | Name of the workflow being simulated |
| workflow_id | Random workflow identifier |
| run_id | Unique execution run ID |
| status | Success / Failed / Partial |
| start_time | Execution start timestamp |
| end_time | Execution end timestamp |
| duration_ms | Total execution duration |
| nodes_executed | Number of nodes executed |
| nodes_list | Example node names |
| error_message | Randomly injected errors |
| attempts | Number of retry attempts |
| payload_summary | Short summary of test payload |
| is_synthetic | Boolean flag (`true`) |
| note | Label for synthetic entries |

---
## 📈 Example Flow
[Manual Trigger] ➜ [Generate Synthetic Logs (Function)] ➜ [Append Row in Google Sheets]


---

## 🧠 Use Cases
- Generate fake operational data to **test observability dashboards**.
- Feed logs to Google Sheets, Retool, PowerBI, or Looker for **visualization and trend tracking**.
- Benchmark workflow runtimes or simulate failure conditions.

---

## ⚙️ Setup
1. Import `Synthetic Log Generator.json` into your n8n instance.
2. Connect your **Google Sheets (OAuth2)** credential.
3. Update the Google Sheet ID in the “Append Row” node to your own `AutomationLogs` sheet.
4. Run manually to populate your sheet with demo data.

---

## 📊 Example Dashboard Ideas
- **Success vs Failure** by workflow  
- **Average runtime** per workflow  
- **Error trends** (Timeouts, Auth errors)  
- **Daily execution volume**

---

## 📸 Demo
<img width="982" height="378" alt="image" src="https://github.com/user-attachments/assets/0e153515-5913-419c-ae17-e4b0c99dfd3f" />


---

## 📄 License
MIT © 2025 Aditya


