---
name: leadership-assessment
description: Recipe that produces an evidence-based leadership assessment of a candidate or sitting executive against a scorecard, from interview transcripts, resume and assessments. Use when the user runs /human-capital:leadership-assessment, or asks to assess, evaluate or write up a candidate or executive against a target.
user-invocable: true
---

# Recipe: full leadership assessment

Run the five steps in [recipe.md](../../reference/recipe.md) with the values below. This skill holds no judgment: what to look for and what the deliverable must contain come from the Team Theory workflow.

**Team Theory workflow:** `SCI-W-005` (Full Leadership Assessment).

## Inputs

| Input | Source | What to fetch |
|---|---|---|
| Target (scorecard) | This conversation, `~~cloud storage`, `~~ATS` (the job), Team Theory `list_documents` / `get_document`, `search_portfolio_knowledge` | The target for the role |
| Interview transcripts | `~~meeting transcripts`, Team Theory `list_documents` / `get_document` | Every interview with the candidate for this role |
| Resume | `~~ATS` (the candidate), `~~cloud storage` | The candidate's resume |
| Assessments | `~~cloud storage`, Team Theory `list_documents` / `get_document` | Psychometric or assessment reports for the candidate |
| Candidate record | Team Theory `list_people` / `get_person` | What the firm already holds on the candidate |

The target and at least one transcript are **required**. Read each transcript in full.

## Destinations

| Destination | Action |
|---|---|
| `~~cloud storage`, `~~knowledge base` | Save as a document |
| `~~ATS` | Attach the assessment to the candidate |
| `~~email` | Draft an email to the hiring team with it attached |

## Output format

- A document artifact.
- Header block: candidate, role, company, date, the inputs used.
- The sections the workflow specifies, in its order, each under its own heading.
- A summary table near the top: one row per facet, with its rating and a one-line evidence note.
- Every supporting quote verbatim, with its source transcript and timestamp.
- Ends with **Sources** and **Methodology trace**.
