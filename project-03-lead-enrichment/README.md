# Project 3 – Lead Enrichment Engine (Ollama + n8n + Airtable)

## 📌 Overview

This workflow automatically enriches incoming sales leads using a **local AI model (Ollama)**. When a lead message is sent to a webhook, the AI extracts structured fields (name, company, job title, email, industry, confidence score), and the enriched data is stored in an Airtable base – all without any API costs or cloud dependencies.

## 🔧 Technologies Used

- **n8n** – Workflow automation (self‑hosted via Docker)
- **Ollama** – Local LLM (llama3.2:3b) running on `host.docker.internal:11434`
- **Airtable** – Database for storing enriched leads
- **Postman** – (optional) for testing webhook calls

## 📁 Workflow File

- `project-03-lead-enrichment.json` – Import this file into your n8n instance.

## ⚙️ How It Works

1. **Webhook** (`POST /lead-enrichment`) receives a JSON payload with a `message` field.
2. **Ollama Chat Model** extracts lead information using a system prompt that returns strict JSON.
3. **Code Node (JavaScript)** parses the AI response and adds the original raw message.
4. **Airtable** creates a new record in the `Leads` table with the enriched fields.

### Example Input (POST body)

```json
{
  "message": "John Doe from Acme Corp, CTO interested in AI automation. john@acme.com"
}