---
name: deep-dive-interview
description: Recipe that produces a comprehensive behavioral interview guide for a long chronological interview. Use when the user runs /human-capital:deep-dive-interview, or asks for a deep-dive, chronological, career-walk or Topgrading-style interview guide.
user-invocable: true
---

# Recipe: deep-dive interview

Run the five steps in [recipe.md](../../reference/recipe.md) with the values below. This skill holds no judgment: what to look for and what the deliverable must contain come from the Team Theory workflow.

**Team Theory workflow:** `SCI-W-003` (Deep Dive Interview Builder).

## Inputs

| Input | Source | What to fetch |
|---|---|---|
| Target (scorecard) | This conversation, `~~cloud storage`, `~~ATS` (the job), Team Theory `list_documents` / `get_document`, `search_portfolio_knowledge` | The target for the role |
| Resume | `~~ATS` (the candidate), `~~cloud storage` | The candidate's resume |
| Prior assessment | Team Theory `list_documents` / `get_document`, `~~cloud storage` | Any earlier assessment of the candidate |
| Candidate record | Team Theory `list_people` / `get_person` | What the firm already holds on the candidate |

The target is **required**. If none exists, offer to run `role-target` first.

## Destinations

| Destination | Action |
|---|---|
| `~~cloud storage`, `~~knowledge base` | Save as a document |
| `~~ATS` | Add the guide as the interview kit on the confirmed stage |
| `~~email` | Draft an email to the interviewer with the guide |

## Output format

- A document artifact.
- Header block: candidate, role, interview length, the inputs used.
- One section per career period from the resume, newest last, each with its questions numbered and follow-ups as bullets.
- A closing section for questions that span the career.
- A scoring table at the end: one row per facet, with columns for rating and evidence.
- Ends with **Sources** and **Methodology trace**.
