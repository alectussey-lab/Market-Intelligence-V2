# Market Intelligence V2

An AI-powered market intelligence tool that looks up company manufacturing plant locations across the US and Canada.

## Features

- 🔍 **Company Lookup** — Enter any company name to research its manufacturing footprint
- 🗺️ **Interactive Map** — View plant locations plotted on a Leaflet.js map
- 📊 **Summary Cards** — Instant overview of company name, employees, ownership, and estimated plant count
- 🏭 **Plant Table** — Detailed breakdown of each facility including parent company, location, and products
- ⚡ **Real-time Progress** — Animated progress bar while AI research runs

## Tech Stack

- **Frontend**: Vanilla HTML/CSS/JS with [Leaflet.js](https://leafletjs.com/) for mapping
- **Backend**: [n8n](https://n8n.io/) workflow automation
- **AI Engine**: Claude (Anthropic) via n8n HTTP node
- **Webhook**: n8n cloud webhook triggers the AI research pipeline

## How It Works

1. User enters a company name in the search field
2. A POST request is sent to the n8n webhook
3. n8n calls the Claude API with a specialized manufacturing research prompt
4. Claude returns structured JSON with plant data
5. The frontend parses the response and renders the map + table

## n8n Workflow

The `n8n_workflow.json` file contains the full workflow. Import it into your n8n instance to replicate the backend pipeline.

**Workflow nodes:**
- `Webhook` → receives the company name
- `Claude API` → queries Anthropic with a manufacturing research prompt
- `Parse & Validate` → cleans and validates the JSON response
- `Respond to Webhook` → returns the data to the frontend

## Setup

1. Import `n8n_workflow.json` into your n8n instance
2. Add your Anthropic API key to the `Claude API` node credentials
3. Update the `N8N_WEBHOOK_URL` in `index.html` to point to your webhook endpoint
4. Open `index.html` in a browser
