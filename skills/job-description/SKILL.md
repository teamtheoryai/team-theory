---
name: job-description
description: Recipe that produces a job description from a role target and posts it to the ATS. Use when the user runs /human-capital:job-description, or asks to write, draft or rewrite a job description or job posting.
user-invocable: true
---

# Recipe: job description

Run the five steps in [recipe.md](../../reference/recipe.md) with the values below. This skill holds no judgment: what to look for and what the deliverable must contain come from the Team Theory workflow.

**Team Theory workflow:** `SCI-W-010` (Job Description Builder).

## Inputs

| Input | Source | What to fetch |
|---|---|---|
| Target (scorecard) | This conversation, `~~cloud storage`, `~~ATS` (the job), Team Theory `list_documents` / `get_document`, `search_portfolio_knowledge` | The target for the role |
| Company context | `~~company data`, `~~CRM` | Ownership, stage, size, industry, deal and value-creation notes |
| Existing posting | `~~ATS` (the job) | The current posting, if one exists |

The target is **required**. If none exists, offer to run `role-target` first.

## Destinations

| Destination | Action |
|---|---|
| `~~ATS` | Replace or create the posting on the confirmed job |
| `~~cloud storage`, `~~knowledge base` | Save as a document |
| `~~chat` | Post it to the channel the user names |

## Output format

- A document artifact, ready to paste into a job board.
- Header block (not part of the posting): role, company, date, the target used.
- The sections the workflow specifies, in its order, with plain headings and short paragraphs or bullets.
- No internal IDs (`R1`, `CC1`) and no methodology citations in the posting text; they go in Sources and Methodology trace below it.
- Ends with **Sources** and **Methodology trace**.
