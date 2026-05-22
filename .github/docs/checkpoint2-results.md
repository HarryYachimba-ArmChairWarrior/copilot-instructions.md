# Checkpoint 2 Results
## Component Name
AI Threat Enrichment
## Objective
This workflow enriches cybersecurity threat intelligence records using AI analysis through the Groq API and updates Airtable automatically.
## Technologies Used
- n8n
- Airtable
- Groq API
- Llama 3.1 8B Instant
## Workflow Process
1. Search for unenriched threat records in Airtable
2. Loop through each threat item
3. Send threat summary to Groq AI model
4. Parse returned JSON response
5. Extract severity, attack type, affected software, and IOCs
6. Update Airtable records with enriched threat intelligence
## Test Performed
A test threat record titled “Suspicious PowerShell Activity” was added to Airtable. The workflow successfully:
- analyzed the threat summary
- classified severity as Medium
- identified PowerShell as affected software
- labeled the attack type as Lateral Movement
- updated Airtable automatically
## Result
The workflow executed successfully and updated Airtable with AI-enriched cybersecurity threat intelligence data.
## GitHub Repository
[UGR-277-Labs Repository](https://github.com/HarryYachimba-ArmChairWarrior/UGR-277-Labs)