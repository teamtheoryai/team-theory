---
name: talent-brain
description: Sets up a Talent Partner Brain in the user's Claude Cowork project — a self-maintaining wiki of every company, seat, executive and search in their portfolio, fed on a schedule from their meetings, email and documents. Interviews the user briefly about their firm and where their information lives, seeds it from Team Theory, then builds it. Use when the user runs /human-capital:talent-brain, or asks to set up a brain, a talent wiki, a portfolio memory, or to have Claude "remember everything about my portfolio".
user-invocable: true
---

# Recipe: set up a Talent Partner Brain

The brain is the partner's unstructured memory: a folder of markdown pages in their Cowork project that Claude keeps current. Team Theory is the structured record. The brain's company, seat and person pages use the same fields as Team Theory's records, so what the partner learns can move into Team Theory without re-keying.

This skill is plumbing: it checks the workspace, collects the inputs, hands over the project instructions, and runs the build in [setup.md](setup.md). The rules the brain follows are in setup.md. Hiring method comes from Team Theory, never from the brain.

## 1. Check the workspace

- If this is not a Cowork project with a folder you can read and write, tell the user to create a project called **Talent Partner Brain** from scratch, give it a folder, and run `/human-capital:talent-brain` there. Stop.
- If `BRAIN.md` already exists in the folder, the brain is built. Offer to run its `start` skill instead. Stop.
- List which connectors are connected, by category (`~~meeting transcripts`, `~~email`, `~~cloud storage`, calendar). Say which of the brain's feeds each one will power.

## 2. Pull what Team Theory already holds

So the interview confirms instead of asks:

| Input | Tool | What to take |
|---|---|---|
| Preferences | `get_custom_instructions` | How the user likes to work |
| Organizations | `list_my_organizations` | The firm's name |
| Firm context | `get_organization_memory` | Standing facts about the firm and portfolio |
| Portfolio | `list_portfolio_entities` (if present), else `list_roles` | Companies and leadership seats |
| People in seats | `list_people`, `get_person` | Occupants and start dates |
| Open searches | `list_searches` | Searches in progress |

Skip any tool not in your tool list.

## 3. Interview

Two or three questions at a time, no more than eight in all. Prefill every answer you have from step 2 and ask the user to confirm or correct it.

| Topic | Ask |
|---|---|
| Firm | The firm, its funds, and who the user answers to |
| Portfolio | The portfolio companies and their leadership seats (show the list from Team Theory; ask what is missing) |
| Questions | The questions they are asked most, and by whom |
| Ratings | The rating scale they use for executives |
| Meetings | Where meeting notes and transcripts live |
| Documents | Where board decks, assessments and search reports live |
| Email | Which email label marks a message for the brain (default: `brain`) |
| Data rules | Their firm's rules on storing candidate and portfolio-company data with an AI tool. Ask once; record the answer verbatim. |

Save the answers, dated and attributed to the user, to `me/setup-interview.md`.

## 4. Hand over the project instructions

Show the contents of [project-instructions.md](project-instructions.md) in a code block. Ask the user to:

1. Paste it into this project's **Instructions** field.
2. Turn off **Use account memory** for this project, so nothing about a person travels into their other chats.

Wait until they confirm both.

## 5. Build

Follow [setup.md](setup.md) from **First session**, step 3 onward. The interview in step 3 above replaces the setup's interview: use `me/setup-interview.md`, and ask only what it is missing.

When creating company, seat and person pages, take Team Theory's records first. Cite them as a source (Team Theory, with the date read), then add what the user said in the interview, cited as coming from the user.

## 6. Close

End with five lines: what was built, how many pages, which feeds are scheduled, the three questions the brain can answer today, and the one thing the user should add next.

## Output

- The `talent-brain/` folder and nineteen project skills, as [setup.md](setup.md) specifies.
- `BRAIN.md` under about a hundred lines.
- Nothing written outside the project folder, and nothing sent.
