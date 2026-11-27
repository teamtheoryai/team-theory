# The recipe steps

Every skill in this plugin runs these five steps. A skill fills in the blanks: its Team Theory workflow, its inputs, its destinations and its output format. A skill holds no judgment; the method comes from Team Theory.

Tool names are the Team Theory MCP tools. Your client may prefix them (e.g. `mcp__team-theory__…`). If the Team Theory tools are missing, stop and tell the user to connect `https://app.teamtheory.ai/mcp`.

## 1. Load the method

1. `get_custom_instructions`. Apply the result to every later step.
2. `get_organization_memory` with `companyName` set to the company the request is about. Treat the cards as standing facts about the firm.
3. `get_workflow` with the skill's workflow id. If `get_workflow` lists a workflow shared in the firm the request concerns for the same deliverable, use that one instead.
4. `read_methodology` for every item on the workflow's reading list, in order, every part of every page.

## 2. Fetch the inputs

Fetch what the skill's inputs table lists, from sources that are connected. Skip the rest without comment.

- Team Theory record and document tools are available only to firm members. If one is not in your tool list, skip it.
- Read a whole document with `get_document`. Never rebuild a document from `search_portfolio_knowledge` fragments; see [memory-and-documents.md](memory-and-documents.md).
- If a search returns more than one match, ask the user which one.
- If an input the skill marks **required** is missing, ask the user where it is, once, then continue with the answer.
- If the project holds a Talent Partner Brain (`BRAIN.md` in its folder), read the wiki pages for the company, seat, people and search first, and cite them like any other source. In step 5, also save the artifact to the brain's `outputs/` and link it from those pages.

## 3. Produce the artifact

Carry out the workflow's steps with the inputs. In chat, report one line per step (e.g. "Reading the three interview transcripts."). Keep drafts and working notes out of chat. Produce the result in the skill's **Output format**. In chat, say one line and where the artifact is.

Every artifact ends with a **Sources** section (each input, its location and date) and a **Methodology trace** in the form `get_workflow` specifies.

## 4. Check it

`check_methodology_trace` with the workflow id and the full draft. Fix everything it reports and run it again until it returns PASS.

## 5. Offer destinations

Offer the connected destinations from the skill's table in one short question. Push only after an explicit yes and a named destination; confirm the exact job, candidate or channel first. Reply with the link or location. If a push fails, say which item and the error returned. If nothing is connected, skip this step.

When the tool list includes a Team Theory tool that saves a document or adds a memory, offer it here too, under the same rule; see [memory-and-documents.md](memory-and-documents.md).
