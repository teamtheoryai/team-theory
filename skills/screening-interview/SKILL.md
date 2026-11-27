---
name: screening-interview
description: Recipe that produces a short screening interview guide for a long list of candidates. Use when the user runs /human-capital:screening-interview, or asks for a screening guide, phone screen, first-round or prospector interview.
user-invocable: true
---

# Recipe: screening (prospector) interview

Run the five steps in [recipe.md](../../reference/recipe.md) with the values below. This skill holds no judgment: what to look for and what the deliverable must contain come from the Team Theory workflow.

**Team Theory workflow:** `SCI-W-008` (Screening/Prospector Interview Builder).

## Inputs

| Input | Source | What to fetch |
|---|---|---|
| Target (scorecard) | This conversation, `~~cloud storage`, `~~ATS` (the job), Team Theory `list_documents` / `get_document`, `search_portfolio_knowledge` | The target for the role |
| Job | `~~ATS` | The job and its stages |

The target is **required**. If none exists, offer to run `role-target` first.

## Destinations

| Destination | Action |
|---|---|
| `~~ATS` | Add the guide as the screening stage's interview kit |
| `~~cloud storage`, `~~knowledge base` | Save as a document |
| `~~chat` | Post it to the channel the user names |

## Output format

- A document artifact, one page, usable during a call.
- Header block: role, company, length of the screen, the target used.
- Numbered questions, each with its follow-ups as bullets beneath it.
- A short scoring table at the end: one row per facet screened, with columns for rating and note.
- Ends with **Sources** and **Methodology trace**.
