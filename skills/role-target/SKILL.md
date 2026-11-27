---
name: role-target
description: Recipe that produces a role target (Team Theory scorecard) from a job description, intake-call transcript, or role context. Use when the user runs /human-capital:target, says "create a target", "build a scorecard", "define the role", or shares a JD / intake call and wants the role defined.
user-invocable: false
---

# Recipe: role target (scorecard)

> This skill is a recipe: it says which tools to call, what to fetch, and where the result goes. The judgment comes from Team Theory (the workflow, its reading list, the user's preferences). If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

**Team Theory workflow:** `SCI-W-006` (Scorecard Builder), or the firm's own scorecard workflow when `get_workflow` lists one for the firm the request concerns.

Tool names are the Team Theory MCP tools; your client may prefix them (e.g. `mcp__team-theory__…`). If the Team Theory tools are missing, stop and tell the user to connect `https://app.teamtheory.ai/mcp`.

## 1. Load the method

1. `get_custom_instructions`. Apply the result to every later step.
2. `get_workflow` with the workflow id above.
3. `read_methodology` for every item on the workflow's reading list, in order.

## 2. Fetch the inputs

Fetch only what the user pointed to, from sources that are connected. Skip the rest without comment.

| Input | Source | What to fetch |
|---|---|---|
| Job description or role brief | `~~cloud storage`, `~~knowledge base`, `~~email`, `~~ATS` (job posting) | The document the user named |
| Intake call | `~~meeting transcripts` | The transcript the user named |
| Company context | `~~company data`, `~~CRM` | Ownership, stage, size, financials, deal and relationship notes for the company |
| Talent market | `~~talent intelligence` | Holders of comparable roles at comparable companies |
| Firm's records | Team Theory `list_roles`, `list_documents`, `get_document` | The role, if it exists, and any prior scorecard for the same company or role |
| Firm's documents | Team Theory `search_portfolio_knowledge` | Prior scorecards or JDs for the same company or role |

- The Team Theory firm tools are available only to firm members. If one is not in your tool list, skip it.
- If a search returns more than one match, ask the user which one.
- If the user pointed to nothing, ask once for the role title, the company, and whether a JD or intake call exists. Continue with the answer.

## 3. Write the target

Carry out the workflow's steps with the inputs from step 2. Report one line per step in chat (e.g. "Reading the intake call."). Produce the target in the **Output format** below.

## 4. Check it

`check_methodology_trace` with the workflow id and the full draft. Fix everything it reports and run it again until it returns PASS.

## 5. Offer destinations

Offer the connected destinations in one short question:

| Destination | Action |
|---|---|
| `~~cloud storage`, `~~knowledge base` | Save the target as a document |
| `~~ATS` | Attach the target to the job |
| `~~email` | Draft an email to the hiring team with the target attached |
| `~~chat` | Post the target to the channel the user names |

Push only after an explicit yes and a named destination. Reply with the link or location. If nothing is connected, skip this step.

## Output format

- One artifact (document), not chat text. In chat, say one line and where the artifact is.
- Header block: role title, company, date, and the inputs used (document names and dates).
- The sections the workflow specifies, in its order, each under its own heading.
- Lists of outcomes and competencies as tables, one row per item, with its ID (`R1`, `CC1`…) in the first column.
- One to two pages.
- Last two sections: **Sources** (each input with its location) and **Methodology trace**, in the form `get_workflow` specifies.
