# Team Theory as the firm's record: documents and memory

Team Theory holds two kinds of record for a firm. **Documents** are the source material: transcripts, scorecards, assessments, memos, intake notes. **Memory** is the firm's standing context: how it works, its preferences, and standing facts about its portfolio, kept as short cards. Read both before you advise on or write for a firm. Write to them only with the user's explicit yes.

## Reading memory

- `get_organization_memory` returns the firm's approved memory cards. Pass `companyName` when the request concerns a particular company or firm: the user may belong to several, and omitting it reads only one.
- Call it at the start of any recipe or advice, so you start from what the firm already knows.
- A short notice means memory is turned off or empty. Continue without it.

## Reading documents

| Need | Tool | Note |
|---|---|---|
| What documents exist for a person, role or company | `list_documents` | Exhaustive. Each row says whether the document can be opened. |
| The full text of one document | `get_document`, with the `[id]` from a list | Use this whenever a recipe needs a whole document. |
| Passages on a subject across all documents | `search_portfolio_knowledge` | Fragments, ranked by relevance. Not exhaustive. Pass `organizationPublicId` (from `list_my_organizations`) to search one firm. |
| A person or role and its history | `list_people`, `get_person`, `list_roles`, `list_searches` | Exhaustive. Use before search for "who" and "which" questions. |

Rules:

- A list answers "do we hold this"; a search does not. Start with a list.
- Ids printed by these tools are for passing to the next tool only. Never show one to the user or accept one from them.
- If `get_document` says a document is still processing, tell the user and try again later. If it says the document cannot be read, tell the user. In both cases, never reconstruct the document from search fragments.
- Cite each document you use by name and date in the artifact's **Sources** section.

## Writing records

Available today, when the user approved write access at sign-in and holds a role that allows it:

| Tool | Does |
|---|---|
| `create_person` | Adds a person to the firm's records |
| `create_role` | Adds a role (seat) at a portfolio company, optionally opening a search |
| `link_person_to_role` | Puts a person in a seat |

These find before they create, so a retry adds nothing. There is no edit and no delete. If the tools are not in your tool list, the connection is read-only: tell the user they can reconnect and approve write access.

## Saving documents and adding memories

Team Theory is adding tools to save a document and to add a memory card. Check your tool list for them on every run.

**When a document-saving tool is present:** after a recipe produces an artifact, offer to save it to Team Theory, attached to the person or role it concerns. Save only after an explicit yes. Save the final artifact, with its Sources and Methodology trace.

**When a memory tool is present:** offer to add a memory when the user states a standing fact or preference about the firm ("we always run four interviewers for C-suite searches", "the portfolio company's board meets quarterly"). One fact per card, in one sentence, with where it came from. Add only after an explicit yes. Never add a judgment about a person as a memory.

**Until then:** offer to save the artifact to `~~cloud storage` instead, and tell the user it can be uploaded to Team Theory in the app. Tell the user a standing fact can be added to memory in the app.
