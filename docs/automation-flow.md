# Car Prospecting Automation Flow

This document explains how the workflow works in practice.

## 1. Form trigger

The workflow starts when a user submits a form or request.

Typical request fields:

- industry
- country
- city
- keyword
- website or company type

## 2. Apify Actor call

The workflow calls an Apify Actor with requested search parameters.

Example payload:

```json
{
  "keyword": "car dealership",
  "country": "Saudi Arabia",
  "city": "Riyadh",
  "industry": "Automotive"
}
```

The actor can scrape from:

- LinkedIn
- business directories
- company websites
- Google Maps or local listings
- custom automation sources

## 3. Wait step

The Wait node pauses the workflow while the scraper runs.

This prevents unnecessary retries or duplicate attempts before the dataset is ready.

## 4. JavaScript normalization

The Code node transforms raw Apify output into Airtable-friendly rows.

Important actions:

- remove empty values
- normalize field names
- set default values
- standardize country, state, and city names
- assign lead status

## 5. Airtable record creation

The final node creates a record in Airtable.

Example Airtable record:

```json
{
  "Name": "Mohamed Ali",
  "Company": "Elite Motors",
  "Job Title": "Sales Manager",
  "Email": "m.ali@elitemotors.com",
  "Phone": "+966500000000",
  "Website": "https://elitemotors.com",
  "LinkedIn": "https://linkedin.com/in/mohamedali",
  "Country": "Saudi Arabia",
  "City": "Riyadh",
  "Industry": "Automotive",
  "Source": "Apify + n8n",
  "Lead Status": "New",
  "Created At": "2026-11-02T12:00:00Z"
}
```

## Suggested future improvements

- Deduplicate by email or LinkedIn URL
- Add route for qualified leads only
- Add webhook to CRM
- Add notification email
- Add enrichment step for company domain validation
