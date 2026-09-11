# Part B — n8n Workflows

## B1 — Lead Notification

Import `workflow-b1-lead-notification.json` into n8n.

Flow:

`Webhook → Set → IF (PG/PhD?) → Email / No-Op`

PG and PhD leads use the email branch. UG leads use the No-Op branch.

For testing, use the n8n test webhook URL. After testing, activate the workflow and use the production webhook URL for Part C.

## B2 — Scheduled Data Fetch

Import `workflow-b2-scheduled-fetch.json` into n8n.

Flow:

`Schedule Trigger → HTTP Request → Code → Set`

### API

Open-Meteo was selected because it is free, public, and does not require an API key. The workflow retrieves current weather data for Mumbai and transforms it into clean fields.

The schedule is configured for daily execution at 9:00 AM.

## Credentials

B1 SMTP credentials are configured directly in n8n. No password or secret is stored in this repository.
