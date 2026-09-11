# AI Automation Intern Assignment — Sarah Shaikh

## Submission details

- **Candidate:** Sarah Shaikh
- **Email:** SarahShaikh0405@gmail.com
- **Submission date:** 12 September 2026
- **Role:** AI Automation Intern

## Overview

This repository contains my submission for the AI Automation Intern technical assessment. It demonstrates a responsive student lead-capture form, n8n workflow automation, scheduled API data fetching, and an end-to-end form-to-webhook integration.

## Repository structure

```text
ai-intern-assignment-SarahShaikh/
├── part-a/
│   └── index.html
├── part-b/
│   ├── workflow-b1-lead-notification.json
│   ├── workflow-b2-scheduled-fetch.json
│   ├── screenshot-b1.png
│   ├── screenshot-b2.png
│   └── README.md
├── part-c/
│   ├── index.html
│   └── loom-link.txt
└── README.md
```

## Part A — Student Lead Capture Form

**Technologies:** HTML5, CSS3, Vanilla JavaScript

Features:
- Full name, email, country, course level, preferred university, and message fields
- Email and required-field validation with inline errors
- 300-character live message counter
- Responsive/mobile-friendly layout
- JSON output logged to the browser console
- Thank-you state without page reload

### Run Part A

Open `part-a/index.html` directly in a browser. No framework, build tool, or server is required.

## Part B1 — Lead Notification Workflow

**Flow:** Webhook → Set → IF → Email / No-Op

The workflow receives student lead data through an n8n webhook and extracts the key fields. PG and PhD leads are routed to an email notification, while UG leads follow a No-Op/mock branch.

The workflow JSON uses placeholder SMTP credential metadata. The actual Gmail SMTP credential is configured securely inside n8n and is not stored in this repository.

## Part B2 — Scheduled Data Fetch

**Flow:** Schedule Trigger → HTTP Request → Code → Set

The workflow uses the free **Open-Meteo** weather API because it is publicly accessible and does not require an API key. The request retrieves current Mumbai weather data, while the Code node transforms the API response into clean labelled fields.

API endpoint:

`https://api.open-meteo.com/v1/forecast?latitude=19.0760&longitude=72.8777&current=temperature_2m,relative_humidity_2m,weather_code,wind_speed_10m`

The workflow is configured for a daily 9:00 AM schedule and can also be executed manually during testing.

## Part C — End-to-End Integration

Part C extends the Part A form so it sends the validated form data to the active B1 n8n webhook using `fetch()` and `POST` with `Content-Type: application/json`.

Features added:
- Loading state (`Submitting...`)
- Disabled submit button while the request is in progress
- Success state after n8n accepts the request
- Error handling with button restoration
- JSON logging retained from Part A

The frontend uses the n8n production webhook endpoint. No SMTP password, API key, or private credential is included in this repository.

## Testing checklist

- [x] Part A form validation
- [x] Part A JSON console logging
- [x] B1 webhook and conditional routing
- [x] B1 PG/PhD email branch
- [x] B1 UG No-Op branch
- [x] B2 API request and JavaScript transformation
- [x] Part C fetch integration code
- [ ] Add B1 n8n canvas screenshot
- [ ] Add B2 n8n canvas screenshot
- [ ] Add final Part C Loom/GIF demo link

## Challenges and resolutions

One challenge was configuring Gmail SMTP for the n8n email node. The initial authentication failed because Gmail requires an App Password rather than the normal account password, so the SMTP credential was updated accordingly. Another challenge was distinguishing n8n's test webhook URL from its production webhook URL; Part C uses the activated production endpoint.

## Credentials and security

No passwords, SMTP credentials, API keys, or access tokens are committed to this repository. n8n credentials are configured through n8n's credential system.

## Final evidence

Before sending the final submission email, add the actual evidence files produced during testing:

1. `part-b/screenshot-b1.png` — B1 n8n canvas screenshot.
2. `part-b/screenshot-b2.png` — B2 n8n canvas screenshot.
3. `part-c/loom-link.txt` — final Loom recording URL, or replace it with `demo.gif`.

These evidence files should be the candidate's actual screenshots/recording rather than fabricated placeholders.
