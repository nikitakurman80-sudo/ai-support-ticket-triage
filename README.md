## Project Results

**Status: Completed — Development & Initial Validation**

Built and tested a no-code AI-powered SaaS support ticket triage workflow using Make.com, Google Gemini 2.5 Flash, and Google Sheets.

### Performance Metrics

| Metric | Result |
|---|---|
| Total synthetic tickets evaluated | 30 |
| Final development test — Category Accuracy | 100% (10/10) |
| Final development test — Priority Accuracy | 100% (10/10) |
| New validation test — Category Accuracy | 100% (20/20) |
| New validation test — Priority Accuracy | 100% (20/20) |
| Validation classification mismatches | 0 |

### Workflow Architecture

**Google Sheets → Make.com → Gemini AI → Text Parser → Google Sheets**

The automation:

1. Retrieves incoming customer support tickets from Google Sheets.
2. Sends ticket details to Google Gemini for classification.
3. Assigns a support category and business-impact-based priority (P1–P4).
4. Generates a professional customer response draft.
5. Extracts structured results using a regular expression.
6. Updates the corresponding Google Sheets row.
7. Marks each response as `Pending Review` for human verification.

### Prompt Optimization

The initial prompt achieved 100% category accuracy and 70% priority accuracy on 10 development tickets.

After analyzing three priority mismatches, the classification instructions were refined to better distinguish authentication issues, integration failures, and business-critical incidents.

The final prompt achieved 100% agreement with predefined labels on the development set and a separate 20-ticket validation set.

### Skills Demonstrated

- SaaS workflow automation
- AI integration and prompt engineering
- Technical support triage
- Data mapping and validation
- Regular expression parsing
- Troubleshooting and quality assurance
- Documentation and testing

### Evaluation

See [Evaluation Report](evaluation_report.md) for detailed testing results and identified issues.

### Limitations

All tickets were synthetic, and classifications were evaluated against project-defined labels. The 20-ticket validation set was not used to revise the final prompt, but its labels were not independently reviewed. These results demonstrate successful initial validation rather than guaranteed accuracy on production data.
