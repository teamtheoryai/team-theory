---
name: quick-interview-plan
description: Recipe that produces a focused interview plan for one interviewer and one candidate, fast. Use when the user runs /human-capital:quick-interview-plan, or says "prep me for my interview with", "quick interview plan", "what should I ask".
user-invocable: true
---

# Recipe: quick interview plan

Run the five steps in [recipe.md](../../reference/recipe.md) with the values below. This skill holds no judgment: what to look for and what the deliverable must contain come from the Team Theory workflow.

**Team Theory workflow:** `SCI-W-002` (Quick Interview Plan Builder).

## Inputs

| Input | Source | What to fetch |
|---|---|---|
| Target (scorecard) | This conversation, `~~cloud storage`, `~~ATS` (the job), Team Theory `list_documents` / `get_document`, `search_portfolio_knowledge` | The target for the role |
| Resume | `~~ATS` (the candidate), `~~cloud storage` | The candidate's resume |
| Candidate record | Team Theory `list_people` / `get_person` | What the firm already holds on the candidate |
| Candidate background | `~~talent intelligence` | The candidate's career history, if the resume is missing |

Ask once for the role and the candidate if neither is given.

## Destinations

| Destination | Action |
|---|---|
| `~~cloud storage`, `~~knowledge base` | Save as a document |
| `~~email` | Draft an email to the interviewer with the plan |
| `~~chat` | Post it to the channel the user names |

## Output format

- A document artifact, one page.
- Header block: candidate, role, interview length, the inputs used.
- Numbered questions in the order to ask them, each with its follow-ups as bullets.
- A scoring table at the end: one row per facet, with columns for rating and evidence.
- Ends with **Sources** and **Methodology trace**.
