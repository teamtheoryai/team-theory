---
name: portfolio-talent-review
description: Recipe that maps a firm's portfolio talent data from Team Theory into a dashboard artifact: leadership ratings, risks and trends across companies and seats, with every value traceable to its source. Use when the user runs /human-capital:portfolio-talent-review, or asks for a portfolio talent review, a talent dashboard, a bench or succession view, or how the portfolio's leadership is rated.
user-invocable: true
---

# Recipe: portfolio talent review

Run the five steps in [recipe.md](../../reference/recipe.md) with the values below. This skill holds no judgment: what to look for and what the deliverable must contain come from the Team Theory workflow.

**Team Theory workflow:** `SCI-W-011` (Portfolio Talent Review).

## Inputs

| Input | Source | What to fetch |
|---|---|---|
| Metrics tracked | Team Theory `list_portfolio_metrics` | The metric keys the firm uses. Call first. |
| Companies, seats, people | Team Theory `list_portfolio_entities` | Exact names to pass to the next tools |
| Review cycles | Team Theory `list_review_cycles` | The cycles; for the latest, every company and seat with its ratings and the recent audit trail |
| Trends | Team Theory `get_portfolio_trend` | How each metric moved over the cycles |
| Roll-ups | Team Theory `get_portfolio_summary` | Averages, counts and distributions per metric |
| Recorded values | Team Theory `list_observations` | Each value with who or which company, period, source and date |
| Org charts and goals | `~~cloud storage`, Team Theory `list_documents` / `get_document` | Prior and future goals, the value-creation plan, if the user names them |

The portfolio tools are available only to owners of firms with Portfolio Talent Review switched on. If they are not in your tool list, tell the user that, and offer to run the review from documents instead (the org charts and goals row). Ask the workflow's clarifying questions (companies, timeframe, purpose, audience) in one message if the request does not answer them.

## Destinations

| Destination | Action |
|---|---|
| `~~cloud storage`, `~~knowledge base` | Save as a document |
| `~~email` | Draft an email to the deal team or board with the dashboard attached |
| `~~chat` | Post it to the channel the user names |

## Output format

- An **interactive dashboard artifact**: one self-contained HTML file with no external requests, data embedded. Render it as an artifact where the client supports it; otherwise save it as a file and give its location.
- Header: firm, companies covered, the review cycle shown, date generated.
- A row of headline figures from `get_portfolio_summary` (for example executives rated, at retention risk, seats without a successor), each with its count and the cycle.
- A **heat map**: companies as rows, the firm's metrics as columns, one cell per value, colored by the metric's scale.
- A **seat table** per company: seat, executive, tenure, each metric, change since the previous cycle.
- **Trend charts** from `get_portfolio_trend` for the metrics the user names, or the firm's headline metrics.
- Filters for company, seat and metric.
- Clicking a value shows its source from `list_observations`: who recorded it, when, and whether it was entered, carried forward or read from a document.
- The workflow's written review, in its sections, below the dashboard.
- Values exactly as Team Theory returns them; no value is computed or invented. A missing value shows as blank, not zero.
- Ends with **Sources** and **Methodology trace**.
