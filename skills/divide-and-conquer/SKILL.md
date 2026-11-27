---
name: divide-and-conquer
description: Recipe that produces a Team Theory Divide & Conquer interview plan from a scorecard, one guide per interviewer, and pushes it to the ATS. Use when the user runs /human-capital:interview-plan, says "divide and conquer", "interview plan", "split the interviews across the panel", or wants interview guides for multiple interviewers from a scorecard or target.
user-invocable: false
---

# Recipe: Divide & Conquer interview plan

> This skill is a recipe: it says which tools to call, what to fetch, and where the result goes. The judgment comes from Team Theory (the workflow, its reading list, the user's preferences). If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

**Team Theory workflow:** `SCI-W-004` (Divide and Conquer Interview Plans Builder), or the firm's own interview-plan workflow when `get_workflow` lists one for the firm the request concerns.

Tool names are the Team Theory MCP tools; your client may prefix them (e.g. `mcp__team-theory__…`). If the Team Theory tools are missing, stop and tell the user to connect `https://app.teamtheory.ai/mcp`.

## 1. Load the method

1. `get_custom_instructions`. Apply the result to every later step.
2. `get_workflow` with the workflow id above.
3. `read_methodology` for every item on the workflow's reading list, in order.

## 2. Fetch the inputs

Fetch the scorecard from the first place it is found:

1. This conversation (a target from `/human-capital:target`, or a pasted scorecard).
2. Where the user pointed: `~~cloud storage`, `~~knowledge base`, `~~email`, `~~ATS` (the job).
3. Team Theory `list_documents` / `get_document`, then `search_portfolio_knowledge`, for the role's scorecard.

If no scorecard exists, offer to run `/human-capital:target` first and stop.

Then fetch, from sources that are connected:

| Input | Source | What to fetch |
|---|---|---|
| Intake call | `~~meeting transcripts` | The intake call for the role, if the user named one |
| Company context | `~~company data`, `~~CRM` | Ownership, stage, industry, team size |
| Candidate pool | `~~talent intelligence` | Backgrounds of holders of comparable roles, to prefill the candidate-experience question |
| Interviewers | `~~ATS` | The interview panel on the job, if set |

- The Team Theory firm tools are available only to firm members. If one is not in your tool list, skip it.
- If a search returns more than one match, ask the user which one.

## 3. Ask the workflow's setup questions

Ask the questions the workflow's setup step lists, in one message. Prefill any answer found in step 2 for the user to confirm. Skip any the user already answered. Wait for the answers.

## 4. Write the plan

Carry out the workflow's remaining steps. Report one line per step in chat (e.g. "Creating the clusters."). Keep clusters, drafts and validation notes out of chat. Produce the plan in the **Output format** below.

## 5. Check it

`check_methodology_trace` with the workflow id and the full draft. Fix everything it reports and run it again until it returns PASS.

## 6. Offer destinations

Offer the connected destinations in one short question:

| Destination | Action |
|---|---|
| `~~ATS` | Create one interview (kit or stage) per interviewer guide on the confirmed job: questions, follow-ups, and the guide's facets as scorecard attributes where the ATS supports them |
| `~~cloud storage`, `~~knowledge base` | Save the plan as a document |
| `~~email` | Draft one email per interviewer with their guide |
| `~~chat` | Post the plan to the channel the user names |

Push only after an explicit yes, with the job and interview stage confirmed. Reply with links or locations. If a guide could not be pushed, say which one and the error returned.

## Output format

- One artifact (document), not chat text. In chat, say one line and where the artifact is.
- Header block: role title, company, date, number of interviewers, and the scorecard used.
- **Facet coverage map:** a table with one row per scorecard facet (ID and name) and one column per interviewer, marking who covers it.
- **One guide per interviewer**, each under its own heading with the cluster name: the facets it covers, then numbered questions, each with its follow-ups as bullets beneath it.
- A **scoring table** at the end of each guide: one row per facet, with columns for rating and evidence.
- Each guide fits on one page so it can be handed to the interviewer on its own.
- Last section: **Methodology trace**, in the form `get_workflow` specifies.
