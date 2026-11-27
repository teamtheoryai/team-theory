---
name: reference-check
description: Recipe that produces a structured reference call guide for a candidate: who to call and what to ask. Use when the user runs /human-capital:reference-check, or asks for references, a reference plan, reference questions or back-channel checks.
user-invocable: true
---

# Recipe: reference call plan

Run the five steps in [recipe.md](../../reference/recipe.md) with the values below. This skill holds no judgment: what to look for and what the deliverable must contain come from the Team Theory workflow.

**Team Theory workflow:** `SCI-W-007` (Reference Call Builder).

## Inputs

| Input | Source | What to fetch |
|---|---|---|
| Target (scorecard) | This conversation, `~~cloud storage`, `~~ATS` (the job), Team Theory `list_documents` / `get_document`, `search_portfolio_knowledge` | The target for the role |
| Assessment and interview notes | Team Theory `list_documents` / `get_document`, `~~meeting transcripts` | The candidate's assessment and interview notes |
| References | `~~ATS` (the candidate), the user | Names, relationships and contact details of the references |
| Resume | `~~ATS` (the candidate), `~~cloud storage` | The candidate's resume |

The target is **required**. If none exists, offer to run `role-target` first.

## Destinations

| Destination | Action |
|---|---|
| `~~cloud storage`, `~~knowledge base` | Save as a document |
| `~~ATS` | Attach the guide to the candidate |
| `~~email` | Draft the outreach emails to each reference, for the user to send |

## Output format

- A document artifact.
- Header block: candidate, role, date, the inputs used.
- A table of references to call: name, relationship, period worked together, the facets each is placed to speak to.
- One call guide per reference: numbered questions, follow-ups as bullets, and space for notes.
- A closing table: one row per facet, with a column per reference for what each said.
- Ends with **Sources** and **Methodology trace**.
