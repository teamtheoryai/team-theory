---
name: role-target
description: Recipe that produces a role target (Team Theory scorecard) from a job description, intake-call transcript, or role context. Use when the user runs /human-capital:target, says "create a target", "build a scorecard", "define the role", or shares a JD / intake call and wants the role defined.
user-invocable: false
---

# Recipe: role target (scorecard)

Run the five steps in [recipe.md](../../reference/recipe.md) with the values below. This skill holds no judgment: what to look for and what the deliverable must contain come from the Team Theory workflow.

**Team Theory workflow:** `SCI-W-006` (Scorecard Builder).

## Inputs

| Input | Source | What to fetch |
|---|---|---|
| Job description or brief | `~~cloud storage`, `~~knowledge base`, `~~email`, `~~ATS` (job posting) | The document the user named |
| Intake call | `~~meeting transcripts` | The transcript the user named |
| Company context | `~~company data`, `~~CRM` | Ownership, stage, size, industry, deal and value-creation notes |
| Talent market | `~~talent intelligence` | Holders of comparable roles at comparable companies |
| Firm's records | Team Theory `list_roles`, `list_documents` / `get_document` | The role, if it exists, and any prior target for the same company or role |

If the user pointed to nothing, ask once for the role title, the company, and whether a JD or intake call exists.

## Destinations

| Destination | Action |
|---|---|
| `~~cloud storage`, `~~knowledge base` | Save as a document |
| `~~ATS` | Attach the target to the job |
| `~~email` | Draft an email to the hiring team with it attached |
| `~~chat` | Post it to the channel the user names |

## Output format

- A document artifact.
- Header block: role title, company, date, and the inputs used.
- The sections the workflow specifies, in its order, each under its own heading.
- Outcomes and competencies as tables, one row per item, with its ID (`R1`, `CC1`…) in the first column.
- One to two pages before Sources and Methodology trace.
- Ends with **Sources** and **Methodology trace**.
