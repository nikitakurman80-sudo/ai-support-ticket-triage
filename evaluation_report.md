## Prompt Optimization Results

The AI Support Ticket Triage workflow was evaluated using 10 synthetic SaaS customer support tickets.

Three iterations of the classification prompt were tested to improve consistency and accuracy.

### Results by Version

| Version | Category Accuracy | Priority Accuracy |
|---|---|---|
| Baseline v1 | 100% (10/10) | 70% (7/10) |
| Improved v2 | 100% (10/10) | 100% (10/10) |
| Final version | 100% (10/10) | 100% (10/10) |

### Issues Identified and Resolved

- **T006:** Incorrect priority assignment and subsequent category mismatch involving an expired API token.
- **T007:** Underestimated business impact of missing Shopify orders.
- **T010:** Overestimated severity of HTTP 500 webhook errors.

### Improvements Implemented

- Introduced business-impact-based priority rules.
- Distinguished authentication failures from integration problems.
- Improved escalation criteria for critical customer order issues.
- Refined classification rules through iterative testing.

### Final Outcome

The final prompt achieved 100% category and priority agreement with the predefined labels across all 10 development tickets.

**Limitation:** These results were obtained on the same dataset used to refine the prompt. They demonstrate successful rule alignment, not independently validated production accuracy.

### Next Step

Evaluate the final prompt against 20 previously unseen synthetic support tickets to measure generalization and identify remaining classification weaknesses.
## Independent Validation — 20 New Support Tickets

Following iterative prompt optimization, the final AI classification workflow was evaluated against 20 new synthetic SaaS customer support tickets that were not part of the initial 10-ticket development dataset.

The final prompt was used without further modifications during this validation run.

### Validation Results

| Metric | Result |
|---|---|
| Tickets processed | 20 |
| Correct category classifications | 20/20 |
| Category accuracy | 100% |
| Correct priority classifications | 20/20 |
| Priority accuracy | 100% |
| Classification mismatches | 0 |

### Workflow Architecture

Google Sheets → Make.com → Google Gemini 2.5 Flash → Text Parser → Google Sheets

### Key Outcomes

- Successfully processed 20 new synthetic customer support tickets.
- Automatically assigned support categories and priority levels.
- Generated customer response drafts for human review.
- Extracted structured AI output using regular expressions.
- Updated the corresponding Google Sheets records.
- Achieved 100% agreement with predefined classification labels on the validation dataset.

### Limitations

This validation used synthetic examples and project-defined labels. The dataset was relatively small, and its labels were not independently adjudicated.

The results demonstrate successful workflow execution and agreement with the test labels, but do not establish production-level reliability.

### Final Project Status

**Completed — Development and Initial Validation**

The project demonstrates practical skills in SaaS workflow automation, AI integration, technical troubleshooting, data mapping, structured output parsing, and quality assurance.
