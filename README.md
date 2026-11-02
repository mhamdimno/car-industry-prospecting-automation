# Car Industry Prospecting Automation

Automation project for finding automotive industry leads, collecting their data with Apify, and saving them into Airtable using n8n.

## What this project does

This workflow:

1. Receives a lead search request from a form
2. Runs an Apify Actor to collect automotive-related contacts or company data
3. Waits for the scraper to finish
4. Normalizes and cleans the results with JavaScript
5. Creates records in Airtable

## Stack

- n8n
- Apify
- Airtable
- JavaScript for data transformation

## Repository structure

```text
.
├── README.md
├── .env.example
├── docs/
│   └── automation-flow.md
├── n8n/
│   └── car-industry-prospecting-workflow.json
└── .gitignore
```

## Workflow logic

```text
Form Trigger
  -> Run Apify Actor
  -> Wait for completion
  -> JavaScript data normalization
  -> Airtable create record
```

## Typical fields collected

- Name
- Company
- Job Title
- Email
- Phone
- Website
- LinkedIn
- Country
- City
- Industry
- Source
- Lead Status
- Notes
- Created At

## Recommended Airtable table

Table name: `Prospects`

Suggested columns:

- Name
- Company
- Job Title
- Email
- Phone
- Website
- LinkedIn
- Country
- City
- Industry
- Source
- Lead Status
- Notes
- Created At

## Sample data mapping

```javascript
const rows = Array.isArray($json) ? $json : ($json.data || $json.dataset || []);

return rows.map((item) => ({
  name: item.name || item.fullName || '',
  company: item.company || item.companyName || '',
  jobTitle: item.jobTitle || item.position || item.role || '',
  email: item.email || '',
  phone: item.phone || item.mobile || '',
  website: item.website || item.companyWebsite || '',
  linkedin: item.linkedin || item.linkedinUrl || '',
  country: item.country || '',
  city: item.city || '',
  industry: item.industry || 'Automotive',
  source: 'Apify + n8n',
  leadStatus: 'New',
  notes: item.notes || '',
  createdAt: new Date().toISOString(),
}));
```

## Environment variables

Create a `.env` file using `.env.example`:

```bash
APIFY_API_TOKEN=your_apify_token
APIFY_ACTOR_ID=your_apify_actor
AIRTABLE_API_KEY=your_airtable_key
AIRTABLE_BASE_ID=appxxxxxxxxxxxxx
```

## Setup instructions

1. Import `n8n/car-industry-prospecting-workflow.json` into n8n.
2. Configure the Form Trigger or replace it with your own trigger.
3. Add your Apify credentials and actor ID.
4. Add Airtable credentials and base ID.
5. Adjust the JavaScript node to match your Apify output.
6. Run a test submission.
7. Review data in Airtable and refine filtering.

## Notes

This is a starter workflow. In production you may want to add:

- duplicate detection
- lead qualification rules
- follow-up reminders
- enrichment steps using Clearbit, email validation, or search APIs
- scheduled scraping jobs

## Goal

This project is designed to help automate automotive lead generation and lead organization for outreach campaigns.
