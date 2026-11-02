# Car Industry Prospecting Automation

This project automates finding people working in the automotive industry, collecting their data with Apify, and organizing it in Airtable through n8n.

## Overview

The workflow follows this logic:

1. A form is submitted
2. n8n triggers the automation
3. An Apify Actor runs to collect lead data
4. n8n waits for the dataset to finish
5. JavaScript cleans and maps data fields
6. Airtable creates a new record

## Included workflow

The repository includes a starter workflow template for n8n based on the image provided:

- `n8n/car-industry-prospecting-workflow.json`

## Recommended stack

- n8n
- Apify
- Airtable

## Typical use case

- Search for automotive companies or professionals
- Pull contact and company details
- Enrich data with job title, company, website, LinkedIn, location
- Save candidates in Airtable for outreach

## Suggested Airtable fields

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

## Example workflow logic

```text
Form Trigger
  -> Run Apify Actor
  -> Wait for dataset
  -> JavaScript normalization
  -> Airtable create record
```

## Setup steps

1. Import the workflow JSON file into n8n.
2. Configure your Apify API token and actor.
3. Set Airtable credentials and base ID.
4. Update the JavaScript mapping node to match your scraped output.
5. Test with one lead.
6. Scale to a form or schedule.

## Environment variables

Example variables:

```bash
APIFY_API_TOKEN=your_apify_token
AIRTABLE_BASE_ID=appXXXXXXXXXXXX
AIRTABLE_API_KEY=your_airtable_key
```

## Project structure

```text
.
├── README.md
├── docs/
│   └── airtable-schema.md
├── n8n/
│   └── car-industry-prospecting-workflow.json
└── .gitignore
```

## Notes

This is a starter implementation. You can adapt the Apify actor and JavaScript node to your actual data source, platform, and lead qualification logic.

## License

This repository is provided as a starter project for automation workflows.
