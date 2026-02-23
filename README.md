# 🤖 AI-Powered CRM Automation (n8n Workflow)

Automated customer message classification and routing system built with n8n + LLM + Google Workspace.

## 📌 Overview

This project implements an intelligent CRM workflow that receives customer messages via Webhook, classifies their priority using AI, routes them dynamically, escalates urgent cases automatically, logs interactions in Google Sheets, and sends automated email responses when required.

The objective of this system is to reduce manual triage, improve response times, and ensure that high-risk customer situations are escalated immediately.

## 🏗 Architecture

The workflow follows this logic:

1. Webhook Trigger  
The system receives a POST request with the following JSON structure:

{
  "nombre": "string",
  "email": "string",
  "mensaje": "string"
}

2. AI Classification Layer  
A language model analyzes the message and classifies it into one of three priorities:

- Alta (High Priority)
- Media (Medium Priority)
- Baja (Low Priority)

Classification criteria:

Alta → Angry client, repeated complaint, legal threat, urgent issue.  
Media → Operational question, purchase inquiry, shipping or payment doubt.  
Baja → Greeting, confirmation, informational or low urgency message.

3. Intelligent Routing (Switch Node)

Alta:
- Internal alert email sent
- Customer receives acknowledgment
- Escalation logic triggered

Media:
- Automated professional response generated
- Email sent to customer

Baja:
- Logged into Google Sheets
- No automatic email sent

## 🛠 Tech Stack

- n8n
- Google Gemini (LLM)
- Gmail API
- Google Sheets API
- JavaScript (Code Node)

## 📂 Repository Structure

crm-ai-workflow/
├── README.md
├── workflow-export.json
└── docs/ (optional)

## 🚀 How to Use

1. Import workflow-export.json into n8n.
2. Configure credentials for:
   - Google Gemini API
   - Gmail OAuth2
   - Google Sheets OAuth2
3. Update the Spreadsheet ID.
4. Activate the workflow.
5. Send a POST request to the webhook endpoint.

## 🧪 Example Test (PowerShell)

Invoke-RestMethod -Uri "http://localhost:5678/webhook-test/crm-ia-public" `
-Method Post `
-ContentType "application/json" `
-Body '{
  "nombre": "Test User",
  "email": "test@email.com",
  "mensaje": "Estoy muy molesto porque ya escribí antes y nadie responde."
}'

## 🔐 Security Notes

- No credentials are stored in the public repository.
- Spreadsheet IDs and email addresses are placeholders.
- The workflow is exported with "active": false.
- API keys must be configured locally inside n8n.

## 📈 Possible Improvements

- Slack or Microsoft Teams integration
- Database integration (PostgreSQL)
- Sentiment scoring dashboard
- Retry and error handling layer
- Rate limiting and abuse protection

## 📊 Business Value

- Reduces manual workload
- Faster critical-case escalation
- Structured interaction tracking
- Scalable customer triage system
- AI-driven prioritization

- <img width="1306" height="552" alt="image" src="https://github.com/user-attachments/assets/77ea414f-7e13-4879-912d-644e553be10e" />
<img width="1306" height="552" alt="image" src="https://github.com/user-attachments/assets/77ea414f-7e13-4879-912d-644e553be10e" />


## 👨‍💻 Author

Elias Lado
