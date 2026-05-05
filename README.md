# Handyman Service Automation Agent

A multi-agent n8n workflow that automates the entire customer intake-to-appointment lifecycle for a handyman service. Replaces ~30 minutes of manual phone tag with a 2-minute automated response — from form submission to a personalized quote email.

## How It Works

1. **Customer submits a request** via a public Google Form (job type, location, urgency)
2. **Google Sheets trigger** detects the new row and kicks off the workflow
3. **Normalization step** cleans and structures the raw form data
4. **Four specialized AI agents** run in sequence:
   - **Intake Agent** — extracts and classifies the job
   - **Pricing Agent** — generates a quote based on job scope
   - **Scheduling Agent** — proposes an appointment window
   - **Comms Agent** — drafts a personalized customer email
5. **Gmail node** sends the final email to the customer


## Why Multi-Agent?

The first version of this workflow used a single LLM call to handle intake, pricing, scheduling, and email drafting all at once. The output was inconsistent — pricing logic leaked into email tone, and debugging was nearly impossible.

Refactoring into four scoped agents added some latency and complexity to the graph, but produced dramatically more reliable outputs and made each stage independently tunable. The lesson: in AI workflows, **modularity beats cleverness**.

## Tech Stack

- **n8n** — workflow orchestration
- **Google Forms / Sheets** — intake and storage
- **OpenAI GPT** — agent reasoning
- **Gmail API** — customer communication
- **Custom webhooks** — agent endpoints

## Files

- `handyman-workflow.json` — exportable n8n workflow definition (import into your own n8n instance to run)
- `workflow.png` — visual canvas of the agent pipeline

## Built By

Maxwell Burns — Baylor University, Finance & MIS  
[Portfolio](https://yourportfolio.com) | [LinkedIn](https://linkedin.com/in/maxwell-burns-6359bb298)
