---
name: candidate-research
description: Recipe that produces a cited background research report on an executive candidate: career history and each company's performance during their tenure. Use when the user runs /human-capital:candidate-research, or asks to research, background or look into a candidate or sitting executive.
user-invocable: true
---

# Recipe: candidate deep research

Run the five steps in [recipe.md](../../reference/recipe.md) with the values below. This skill holds no judgment: what to look for and what the deliverable must contain come from the Team Theory workflow.

**Team Theory workflow:** `SCI-W-014` (Candidate Deep Research).

## Inputs

| Input | Source | What to fetch |
|---|---|---|
| Target (scorecard) | This conversation, `~~cloud storage`, `~~ATS` (the job), Team Theory `list_documents` / `get_document`, `search_portfolio_knowledge` | The target for the role |
| Resume | `~~ATS` (the candidate), `~~cloud storage` | The candidate's resume |
| Career history | `~~talent intelligence`, web search | The candidate's roles, dates and companies |
| Company performance | `~~company data`, web search | Each employer's performance and milestones during the candidate's tenure |
| Candidate record | Team Theory `list_people` / `get_person` | What the firm already holds on the candidate |

Ask once for the candidate's full name and current company if not given. Web search is the client's own; use it when the client has it.

## Destinations

| Destination | Action |
|---|---|
| `~~cloud storage`, `~~knowledge base` | Save as a document |
| `~~ATS` | Attach the report to the candidate |
| `~~chat` | Post it to the channel the user names |

## Output format

- A document artifact.
- Header block: candidate, role being considered for, date, the sources used.
- A career timeline table: one row per role, with company, title, dates.
- The sections the workflow specifies, in its order, one subsection per company in the timeline.
- Every factual claim carries a numbered citation; the Sources section lists each citation with its link and access date.
- Ends with **Sources** and **Methodology trace**.
