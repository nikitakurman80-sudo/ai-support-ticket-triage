# Evaluation Report — Baseline v1

## Objective

Evaluate whether a no-code AI workflow can categorize and prioritize synthetic SaaS support requests against predefined project labels.

## Method

Ten synthetic support tickets were processed using Google Sheets, Make, and Gemini 2.5 Flash. Outputs were parsed and written back to the sheet. Category and priority predictions were compared with predefined expected labels.

## Baseline results

| Metric | Result |
| --- | ---: |
| Tickets evaluated | 10 |
| Category matches | 10/10 (100%) |
| Priority matches | 7/10 (70%) |

## Priority mismatches

| Ticket | Issue | Expected | AI prediction | Analysis |
| --- | --- | --- | --- | --- |
| T006 | Expired API token | P3 | P2 | Integration interruption may suggest urgency, but widespread impact was not confirmed in the ticket. |
| T007 | Missing Shopify orders | P1 | P2 | The project policy treats missing orders affecting fulfillment as critical. |
| T010 | Webhook HTTP 500 | P2 | P1 | An HTTP 500 error and delayed orders do not by themselves establish a complete outage. |

These are mismatches with **project-defined labels**, not proof that every alternative priority would be wrong under a real organization's incident policy.

## Improvement plan

Prompt v2 introduces more explicit impact-based priority criteria and emphasizes not inferring widespread outages from technical error codes alone. It also retains human review for all draft responses.

**Retest status:** Not yet measured. Do not claim improved accuracy until a new test is run.

## Limitations

- Small, synthetic dataset; results are not generalizable to production.
- Rules were refined after observing baseline errors, so the same ten tickets alone cannot validate generalization.
- A future evaluation should include new unseen tickets, ambiguous cases, and independent human review.
- Response quality and safety were not quantitatively scored.
