# AI Lead Generation & Scoring Agent (n8n)

An n8n workflow that captures leads through a web form, validates and de-duplicates them, scores them 0–100 using an AI Agent plus rule-based criteria, classifies them as Hot / Warm / Cold, routes each to the right sales path, and sends a weekly management report.


## Features
- Web form for lead capture (budget, timeline, role, company size, source, need)
- Data validation and normalization (Persian digits, phone formats, email check)
- Duplicate and incomplete lead detection
- AI Agent (OpenAI gpt-4o-mini) that analyzes the free-text need
- Hybrid scoring: AI for text understanding, rules for numeric criteria
- Hot / Warm / Cold classification with a different sales path for each
- Google Sheets as database (Leads, Duplicates, Incomplete tabs)
- Weekly management report by email

## Scoring model (0–100)
| Criterion | Max points | Source |
|---|---|---|
| Budget | 25 | Rule |
| Timeline | 20 | Rule |
| Decision authority | 15 | Rule |
| Company size | 10 | Rule |
| Need clarity | 10 | AI Agent |
| Source quality | 10 | Rule |
| Data completeness | 10 | Rule |

## Tiers and routing
| Tier | Score | Action |
|---|---|---|
| Hot | 70–100 | Instant alert to sales manager, call within 1 hour |
| Warm | 40–69 | Assign to sales expert, proposal within 24h |
| Cold | below 40 | Automated nurturing email |

## Tech stack
n8n · OpenAI API · JavaScript · Google Sheets · Gmail

## Setup
1. Import `lead-scoring-workflow.json` into n8n (Workflows → Import from File).
2. Create a Google Sheet with three tabs: `Leads`, `Duplicates`, `Incomplete`, and add column headers matching the workflow nodes.
3. Connect your own credentials: Google Sheets, Gmail, OpenAI.
4. Replace `YOUR_GOOGLE_SHEET_ID` and `your-email@example.com` in the nodes.
5. Activate the workflow and open the form's Production URL.

