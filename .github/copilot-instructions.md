# Capstone Project Context

## Project

- **Name:** Threat Intelligence Feed Dashboard

- **Team:**
  - Jesus Alvarez — Component 1: Feed Collector
  - Harry Yachimba — Component 2: AI Summarizer & IOC Extractor
  - Julian Silva-Erazo — Component 3: Relevance Scorer
  - Safayet Safin — Component 4: Integration, Testing & Presentation

- **What it does:**
  This project automates the collection, summarization, IOC extraction, and prioritization of cybersecurity threat intelligence using AI. Threat data is collected, processed through Flowise and AI models, stored in Airtable, and analyzed to help security analysts focus on high-priority threats.

- **Project Type:**
  AI Threat Intelligence Dashboard

---

## Architecture

- **Ingestion:**
  n8n workflows collect threat intelligence feeds and store records in Airtable.

- **AI Core:**
  Flowise LLM chains using Groq models summarize articles and classify threat data.

- **Specialist:**
  IOC extraction and relevance scoring identify malware names, IP addresses, domains, CVEs, and attack severity.

- **Integration:**
  n8n connects all components together and manages automation between Airtable and Flowise.

---

## Tech Stack

- n8n Cloud
- Flowise Cloud
- Groq API
- Hugging Face API
- Airtable
- GitHub
- VS Code
- GitHub Copilot
- JSON APIs

---

## Airtable Schema

### Threat Intelligence Table

| Field | Type | Written By | Status Values |
|---|---|---|---|
| input_text | Long Text | Component 1 | |
| summary | Long Text | Component 2 | |
| severity | Single Select | Component 2 | critical, high, medium, low |
| attack_type | Text | Component 2 | |
| indicators | Long Text | Component 2 | |
| recommendations | Long Text | Component 2 | |
| relevance_score | Number | Component 3 | |
| tested_at | Date | Component 4 | |

### Conventions

- Field names: snake_case
- Status values: lowercase
- AI responses must return valid JSON
- Use POST requests for Flowise prediction endpoints

---

## Current State

## Current State

- **What's working:** Component 2 AI Threat Enrichment is now working. The n8n workflow searches Airtable for records where `Enriched = false` and `Raw Summary` is populated, sends the record to the Groq API, parses the structured JSON response, and updates Airtable with enriched fields including severity, affected software, attack type, IOCs, enriched timestamp, and model attribution.

- **What's in progress:** Full end-to-end confirmation across all four components is still in progress. Component 2 is working, but handoffs into Specialist/Relevance Scorer and final dashboard visibility still need confirmation.

- **Known issues:** The imported n8n workflow initially failed because the Groq authorization header was not formatted correctly. The issue was fixed by using `Authorization: Bearer <Groq API key>`. The workflow also needs continued validation for field-name consistency across components.

- **Next milestone:** Complete Checkpoint 2 by documenting the test results, confirming component handoffs, and addressing any field mapping or automation gaps.
---

## Repository Structure

```text
.
├── .github/
│   └── copilot-instructions.md
├── docs/
│   ├── architecture.png
│   └── proposal.md
├── week-07/
├── week-08-prompt-engineering-&-copilot/
├── screenshots/
└── README.md