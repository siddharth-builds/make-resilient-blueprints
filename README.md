# Resilient Lead Enrichment Pipeline (Make.com) ⚙️

This blueprint automates the research and drafting phase of B2B cold outreach. It catches inbound payloads, routes data through an LLM for structured business analysis, and logs the output to a database. 

### Architecture & Fault Tolerance
Unlike standard linear automations, this pipeline is engineered for reliability:
* **Custom Webhook Catcher:** Instantly accepts JSON payloads from CRMs, Postman, or web forms.
* **Immediate 200 OK Handshake:** Prevents API timeouts by immediately resolving the HTTP request before processing heavy AI tasks.
* **Strict JSON Parsing:** Forces the LLM (GPT/Gemini) to output machine-readable JSON, stripping out conversational AI fluff to prevent database mapping errors.
* **Automated Retry Error Handling:** If the destination database (Google Sheets/Airtable) experiences downtime, the sequence breaks to a retry queue (3 attempts, 15-minute intervals) to ensure zero lead data is lost.

### Files Included
* `lead-enrichment-blueprint.json` (Import directly into Make.com)
* Canvas Architecture Screenshot
