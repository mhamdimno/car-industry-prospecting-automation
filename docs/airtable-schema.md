# Airtable schema for car prospecting

Use the following fields in your Airtable base.

## Table: Prospects

| Field Name | Type | Description |
| --- | --- | --- |
| Name | Single line text | Prospect full name |
| Company | Single line text | Company or dealership name |
| Job Title | Single line text | Position title |
| Email | Email | Business email |
| Phone | Phone number | Direct phone |
| Website | URL | Official website |
| LinkedIn | URL | LinkedIn profile |
| Country | Single line text | Country |
| City | Single line text | City |
| Industry | Single line text | Automotive / Dealer / Supplier |
| Source | Single line text | Apify / LinkedIn / Form |
| Lead Status | Single select | New, Contacted, Qualified, Replied, Rejected |
| Notes | Long text | Internal notes |
| Created At | Date | Record creation time |

## Suggested views

- All Leads
- New Leads
- Qualified Leads
- Follow-up Needed
- Replied

## Optional automation

You can add Airtable automations to:
- send a notification when a lead is added
- flag leads with missing email
- schedule follow-up reminders
