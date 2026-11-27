---
name: divide-and-conquer
description: Recipe that produces a Divide & Conquer interview plan from a scorecard as an interactive interview artifact, one guide per interviewer, and pushes it to the ATS. Use when the user runs /human-capital:interview-plan, says "divide and conquer", "interview plan", "split the interviews across the panel", or wants interview guides for multiple interviewers.
user-invocable: false
---

# Recipe: Divide & Conquer interview plan

Run the five steps in [recipe.md](../../reference/recipe.md) with the values below. This skill holds no judgment: what to look for and what the deliverable must contain come from the Team Theory workflow.

**Team Theory workflow:** `SCI-W-004` (Divide and Conquer Interview Plans Builder).

## Inputs

| Input | Source | What to fetch |
|---|---|---|
| Target (scorecard) | This conversation, `~~cloud storage`, `~~ATS` (the job), Team Theory `list_documents` / `get_document`, `search_portfolio_knowledge` | The target for the role |
| Intake call | `~~meeting transcripts` | The intake call for the role, if the user named one |
| Company context | `~~company data`, `~~CRM` | Ownership, stage, size, industry, deal and value-creation notes |
| Candidate pool | `~~talent intelligence` | Backgrounds of holders of comparable roles, to prefill the candidate-experience question |
| Interview panel | `~~ATS` | The interviewers on the job, if set |

The target is **required**. If none exists, offer to run `role-target` first. Ask the workflow's setup questions in one message, prefilled from the inputs, and wait for the answers before writing.

## Destinations

| Destination | Action |
|---|---|
| `~~ATS` | Create one interview (kit or stage) per interviewer on the confirmed job: questions, follow-ups, and the guide's facets as scorecard attributes where the ATS supports them |
| `~~cloud storage`, `~~knowledge base` | Save as a document |
| `~~email` | Draft one email per interviewer with the artifact and their guide named |
| `~~chat` | Post it to the channel the user names |

## Output format

- An **interactive artifact**: one self-contained HTML file with no external requests. Render it as an artifact where the client supports it; otherwise save it as a file and give its location.
- A header with role, company, date and number of interviewers, and a tab or selector for each interviewer plus an **Overview** tab.
- **Overview tab:** the facet coverage map, a table with one row per facet (ID and name) and one column per interviewer.
- **Each interviewer tab:** the cluster name and facets, then the questions in order. Each question has its follow-ups beneath it, a checkbox to mark it asked, and a notes field.
- A **scoring panel** on each interviewer tab: one row per facet, a rating control and an evidence field.
- A **Copy notes** button that copies that interviewer's notes and ratings as plain text, for the debrief or the ATS.
- Notes and ratings stay in the open page only; nothing is sent anywhere.
- Readable on a laptop and a phone; printable, one interviewer per page.
- The Sources and Methodology trace in a final collapsible section.
- Ends with **Sources** and **Methodology trace**.
