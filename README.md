# AI Support Ticket Triage

A no-code portfolio project that classifies synthetic SaaS support tickets, proposes a priority, drafts a response, and records results for human review.

## Workflow

Google Sheets (Search Rows) → Google Gemini 2.5 Flash (Simple text prompt) → Make Text Parser (Match pattern) → Google Sheets (Update a Row)

## What it does

- Reads customer-support tickets from Google Sheets.
- Classifies each ticket into one of seven categories: Availability, Authentication, Integration, Feature Request, Data Migration, Performance, or How-To.
- Assigns a proposed priority (P1–P4).
- Generates a draft customer response and marks it `Pending Review`.
- Writes results back to the original spreadsheet row using the row number from Search Rows.

## Baseline evaluation

Tested on **10 synthetic tickets** against predefined labels:

| Metric | Baseline result |
| --- | ---: |
| Category accuracy | 100% (10/10) |
| Priority accuracy | 70% (7/10) |

Three priority mismatches were identified: T006, T007, and T010. See [evaluation_report.md](evaluation_report.md).

## Design and safeguards

- Synthetic test data only; no customer information.
- AI-generated replies are **drafts** and require human review before sending.
- Technical error codes alone should not determine business impact.
- Prompt v2 was drafted after reviewing baseline mismatches; its effectiveness has **not yet been retested**.

## Repository contents

- `sample_tickets.csv` — synthetic test tickets and expected labels
- `prompt_v2.md` — revised classification instructions
- `evaluation_report.md` — baseline results, mismatches, and limitations

## Reproducing the workflow

1. Import `sample_tickets.csv` into Google Sheets, in a sheet named `Support Tickets`.
2. Add columns `AI_Category`, `AI_Priority`, `AI_Response`, and `Review_Status`.
3. In Make, configure **Google Sheets → Search Rows** to read the sheet.
4. Add **Google Gemini AI → Simple text prompt**. Insert mapped values for ticket ID, subject, and description in the prompt.
5. Add **Text Parser → Match pattern** to extract category, priority, and response.
6. Add **Google Sheets → Update a Row**, mapping the source row number and extracted fields. Set `Review_Status` to `Pending Review`.
7. Run a single-ticket test before processing the remaining synthetic tickets.

**Note:** Make modules and available Gemini usage limits may vary by account and over time. The workflow is not configured to send responses automatically.

## Skills demonstrated

SaaS support operations · No-code automation · Data mapping · AI prompt design · Technical troubleshooting · QA and evaluation · Human-in-the-loop workflows
