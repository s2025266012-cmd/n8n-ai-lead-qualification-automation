# Nexa AI - Automated Lead Qualification & Outreach Pipeline

An end-to-end AI automation workflow built in **n8n** that captures incoming leads from Google Sheets, evaluates and scores them using **Google Gemini**, routes them based on qualification criteria, sends personalized emails via **Gmail**, and logs structured insights back to the CRM sheet.

![Workflow Diagram](./Screenshot%202026-11-23%20165518.png)

## How It Works
1. **Lead Capture (`Google Sheets Trigger`):** Monitors incoming lead submissions in real time.
2. **AI Lead Scoring (`Google Gemini`):** Analyzes budget, timeline, company details, and project scope using structured JSON output.
3. **Data Parsing (`Edit Fields`):** Extracts `lead_score`, `category`, `reason`, and `recommended_action` into clean variables.
4. **Smart Conditional Routing (`If` / `If1`):**
   - **Qualified Leads:** Automatically sends a tailored outreach email via **Gmail** and updates the sheet status to `Qualified - Email Sent`.
   - **Unqualified / Low-Priority Leads:** Marks the lead as `Not Qualified` without sending unnecessary emails.
5. **CRM Logging (`Google Sheets`):** Writes back the final status, numeric `Lead Score`, and `AI Reason` for full sales team visibility.

## Tech Stack
* **Orchestration:** n8n (Self-hosted via Docker)
* **AI Model:** Google Gemini (`gemini-3-flash-preview` with JSON output)
* **CRM & Storage:** Google Sheets API
* **Email Automation:** Gmail OAuth2 API

## Setup Instructions
1. Download `Nexa AI - Lead Qualification Automation.json` from this repository.
2. In your n8n instance, create a new workflow, click `•••` > **Import from File**, and select the JSON file.
3. Connect your **Google Sheets**, **Google Gemini**, and **Gmail** credentials.
4. Publish and activate the workflow.
