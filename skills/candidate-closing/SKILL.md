---
name: candidate-closing
description: Recipe that produces a strategy and materials for closing a chosen candidate. Use when the user runs /human-capital:candidate-closing, or asks how to close, sell or land a candidate, or handle a competing offer.
user-invocable: true
---

# Recipe: candidate closing plan

Run the five steps in [recipe.md](../../reference/recipe.md) with the values below. This skill holds no judgment: what to look for and what the deliverable must contain come from the Team Theory workflow.

**Team Theory workflow:** `SCI-W-009` (Candidate Closing Guidance).

## Inputs

| Input | Source | What to fetch |
|---|---|---|
| Candidate record | Team Theory `list_people` / `get_person` | What the firm already holds on the candidate |
| Assessment and interview notes | Team Theory `list_documents` / `get_document`, `~~meeting transcripts` | What the candidate said about their motivations and concerns |
| Offer | `~~ATS`, the user | The offer terms and any competing offer |
| Company context | `~~company data`, `~~CRM` | Ownership, stage, size, industry, deal and value-creation notes |

Ask the workflow's clarifying questions on the candidate's motivations and concerns in one message, and wait for the answers.

## Destinations

| Destination | Action |
|---|---|
| `~~cloud storage`, `~~knowledge base` | Save as a document |
| `~~email` | Draft the follow-up emails the plan calls for, for the user to send |
| `~~chat` | Post it to the channel the user names |

## Output format

- A document artifact.
- Header block: candidate, role, date, the inputs used.
- The sections the workflow specifies, in its order.
- A table of actions: who, what, by when.
- Any message to the candidate as a separate, ready-to-edit draft at the end.
- Ends with **Sources** and **Methodology trace**.
