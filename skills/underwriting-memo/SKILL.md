---
name: underwriting-memo
description: Recipe that produces a one-page candidate underwriting memo for a private-equity deal-partner audience from the candidate's interview transcripts, references, resume and scorecard. Use when the user runs /human-capital:underwriting-memo, says "underwriting memo", "write up this candidate for the deal team", "candidate memo".
user-invocable: false
---

# Recipe: candidate underwriting memo

Run the five steps in [recipe.md](../../reference/recipe.md) with the values below. This skill holds no judgment: what to look for and what the deliverable must contain come from the Team Theory workflow.

**Team Theory workflow:** `SCI-W-012` (Underwriting Memo Builder).

## Inputs

| Input | Source | What to fetch |
|---|---|---|
| Target (scorecard) | This conversation, `~~cloud storage`, `~~ATS` (the job), Team Theory `list_documents` / `get_document`, `search_portfolio_knowledge` | The target for the role |
| Interview transcripts | `~~meeting transcripts`, Team Theory `list_documents` / `get_document` | Every interview with the candidate for this role |
| Reference calls | `~~meeting transcripts`, `~~cloud storage` | Reference-call transcripts or notes for the candidate |
| Resume | `~~ATS` (the candidate), `~~cloud storage` | The candidate's resume |
| Assessments | `~~cloud storage`, Team Theory `list_documents` / `get_document` | Psychometric or assessment reports for the candidate |
| Candidate record | Team Theory `list_people` / `get_person` | What the firm already holds on the candidate |
| Company and deal | `~~company data`, `~~CRM` | The company, the deal, and the value-creation plan, if recorded |

The target and the interview transcripts are **required**.

## Destinations

| Destination | Action |
|---|---|
| `~~cloud storage`, `~~knowledge base` | Save as a document |
| `~~ATS` | Attach the memo to the candidate on the job |
| `~~email` | Draft an email to the deal team with the memo attached |
| `~~chat` | Post it to the channel the user names |

## Output format

- A document artifact, one page, written for a deal partner.
- Header block: candidate, role, company, date, the inputs used.
- The sections the workflow specifies, in its order. The first section fits in three lines.
- Each claim about the candidate carries its source in brackets: the document or call, and the timestamp or page where it has one.
- Ends with **Sources** and **Methodology trace**.
