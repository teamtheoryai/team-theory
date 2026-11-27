---
name: underwriting-memo
description: Recipe that produces a one-page candidate underwriting memo for a private-equity deal-partner audience from the candidate's interview transcripts, references, resume and scorecard. Use when the user runs /human-capital:underwriting-memo, says "underwriting memo", "write up this candidate for the deal team", "candidate memo", or wants a candidate assessed for a deal partner.
user-invocable: false
---

# Recipe: candidate underwriting memo

> This skill is a recipe: it says which tools to call, what to fetch, and where the result goes. The judgment comes from Team Theory (the workflow, its reading list, the user's preferences). If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

**Team Theory workflow:** `SCI-W-012` (Underwriting Memo Builder), or the firm's own memo workflow when `get_workflow` lists one for the firm the request concerns.

Tool names are the Team Theory MCP tools; your client may prefix them (e.g. `mcp__team-theory__…`). If the Team Theory tools are missing, stop and tell the user to connect `https://app.teamtheory.ai/mcp`.

## 1. Load the method

1. `get_custom_instructions`. Apply the result to every later step.
2. `get_workflow` with the workflow id above.
3. `read_methodology` for every item on the workflow's reading list, in order.

## 2. Fetch the inputs

Fetch from sources that are connected. Skip the rest without comment.

| Input | Source | What to fetch |
|---|---|---|
| Scorecard / target | This conversation, `~~cloud storage`, `~~ATS` (the job), Team Theory `list_documents` / `get_document`, `search_portfolio_knowledge` | The scorecard for the role |
| Interview transcripts | `~~meeting transcripts` | Every interview with the candidate for this role |
| Reference calls | `~~meeting transcripts`, `~~cloud storage` | Reference-call transcripts or notes for the candidate |
| Resume | `~~ATS` (the candidate), `~~cloud storage` | The candidate's resume |
| Assessments | `~~cloud storage`, Team Theory `list_documents` / `get_document` | Psychometric or assessment reports for the candidate |
| Candidate record | Team Theory `list_people` / `get_person` | What the firm already holds on the candidate |
| Company and deal | `~~company data`, `~~CRM` | The company, the deal, and the value-creation plan, if recorded |

- The Team Theory firm tools are available only to firm members. If one is not in your tool list, skip it.
- If a search returns more than one candidate or more than one role, ask the user which one.
- If the scorecard or the interview transcripts are missing, ask the user where they are, once. Continue with the answer.

## 3. Write the memo

Carry out the workflow's steps with the inputs from step 2. Report one line per step in chat (e.g. "Reading the three interview transcripts."). Produce the memo in the **Output format** below.

## 4. Check it

`check_methodology_trace` with the workflow id and the full draft. Fix everything it reports and run it again until it returns PASS.

## 5. Offer destinations

Offer the connected destinations in one short question:

| Destination | Action |
|---|---|
| `~~cloud storage`, `~~knowledge base` | Save the memo as a document |
| `~~ATS` | Attach the memo to the candidate on the job |
| `~~email` | Draft an email to the deal team with the memo attached |
| `~~chat` | Post the memo to the channel the user names |

Push only after an explicit yes and a named destination. Reply with the link or location. If nothing is connected, skip this step.

## Output format

- One artifact (document), not chat text. In chat, say one line and where the artifact is.
- One page, written for a deal partner.
- Header block: candidate name, role, company, date, and the inputs used.
- The sections the workflow specifies, in its order, each under its own heading. The first section fits in three lines.
- Each claim about the candidate carries its source in brackets: the document or call, and the timestamp or page where it has one.
- After the page: **Sources** (each input with its location and date) and **Methodology trace**, in the form `get_workflow` specifies.
