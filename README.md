# 🇵🇰 DAY-13 — Citizen Complaint Management System

An AI-powered complaint intake and triage system built for Pakistani citizens to report civic issues (water, electricity, gas, sanitation, roads, etc.) and get an instant, AI-generated analysis — category, priority, recommended action, and estimated resolution time — with every complaint automatically logged for the relevant department.

Part of my **30-Day n8n Automation Challenge**.

**Repo:** https://github.com/JunaidZulfiqar07/DAY-13-CITIZEN-COMPLAINT-SYSTEM
**Workflow:** Built entirely in [n8n](https://n8n.io)

---

## ✨ Features

- 📝 **Bilingual-ready complaint form** — captures name, contact info, category, location, subject, and description
- 🤖 **AI-powered triage** — an LLM agent analyzes each complaint and returns:
  - Category classification
  - Priority level (LOW / MEDIUM / HIGH / CRITICAL)
  - A clear, human-readable summary
  - A recommended administrative action
  - An estimated resolution timeframe
- 🆔 **Auto-generated Complaint ID** (`CMP-YYYY-XXXXX`) for tracking
- 📊 **Automatic logging** to Google Sheets for departmental record-keeping
- ⚡ **Instant results** — no page reload, results render directly on the same page
- 🔒 Clean, government-style UI built with vanilla HTML/CSS/JS — no frameworks required

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, JavaScript (vanilla) |
| Automation / Backend | [n8n](https://n8n.io) (Cloud) |
| AI Analysis | LLM Agent node (OpenAI-compatible chat model) |
| Data Storage | Google Sheets |
| Frontend Hosting | Local / any static host |

---

## ⚙️ How It Works

1. Citizen submits the complaint form on the frontend.
2. The form POSTs a JSON payload to an **n8n Webhook**.
3. A **Code node** extracts the form fields and generates a unique Complaint ID.
4. An **AI Agent node** analyzes the complaint text and returns a structured JSON verdict (category, priority, summary, recommended action, estimated resolution).
5. A **Code node** merges the AI output with the original complaint data.
6. The complete record is **appended to a Google Sheet** for departmental tracking.
7. A **Respond to Webhook** node sends the structured result back to the frontend, which renders it instantly for the citizen.

```
Citizen Form → n8n Webhook → Extract & ID → AI Agent → Merge Results → Google Sheets → Respond to Frontend
```

---

## 🚀 Setup / Local Use

1. Clone this repo:
   ```bash
   git clone https://github.com/JunaidZulfiqar07/DAY-13-CITIZEN-COMPLAINT-SYSTEM.git
   ```
2. Import `workflow.json` into your n8n instance (n8n Cloud or self-hosted).
3. Connect your own:
   - Google Sheets account (for logging)
   - OpenAI-compatible model credentials (for the AI Agent node)
4. Activate the workflow and copy the **Production Webhook URL**.
5. Open `index.html`, replace the `N8N_WEBHOOK_URL` constant with your webhook URL.
6. Open `index.html` directly in your browser to use it locally (or host it on any static server of your choice).

---

## 📌 Notes

- This is a portfolio/demo project — for real-world government deployment it would need role-based access control, audit logging, and input validation hardening.
- Built as part of a 30-day n8n automation challenge.

---

## 👤 Author

**Junaid Zulfiqar**
Computer Engineering Student, UET Taxila
Building AI automation systems with n8n — [Fiverr](#) • [LinkedIn](#)
