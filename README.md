# AI Email Outreach — n8n Workflow

Automated outreach pipeline built in n8n that reads a contact list 
from Google Sheets, generates a unique personalised email per contact 
through the Groq API, and delivers each one via Gmail on a fully 
automated daily schedule.

## How It Works
Google Sheets → Loop → Groq API (LLaMA 3.3-70b) → Gmail → Inbox
1. Schedule trigger fires daily at 09:00
2. Google Sheets node pulls all contacts from the configured sheet
3. Loop Over Items processes each contact individually
4. Groq API generates a unique personalised email for each contact
5. Gmail node delivers the email directly to each recipient

## Tech Stack

| Layer | Tool |
|---|---|
| Workflow orchestration | n8n |
| Contact data | Google Sheets API |
| AI content generation | Groq API — llama-3.3-70b-versatile |
| Email delivery | Gmail via OAuth2 |

## Setup

1. Import the workflow JSON into your n8n instance
2. Create a Google Sheets credential using OAuth2
3. Create a Gmail credential using OAuth2
4. Add your Groq API key as an HTTP Header Auth credential
5. Set your Google Sheet name in the Sheets node
6. Activate the workflow

## Google Sheet Format

| Name | Email | Message Topic |
|---|---|---|
| James Miller | james@example.com | product launch |

## Notes

Groq API free tier is sufficient for standard usage.
Gmail OAuth2 credential requires a Google Cloud project with Gmail API enabled.
Workflow runs daily at 09:00 — adjustable in the Schedule Trigger node.
