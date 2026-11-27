# Cookbook

Example prompts, and the strategic plays Team Theory can run for a PE talent partner. Each entry names what runs. Use them to show the user what is possible, and as patterns for routing a request that matches no single recipe.

## Single prompts

| Prompt | Runs |
|---|---|
| "Build a target for a CFO at our industrial distributor, from Tuesday's intake call in Granola." | `role-target` |
| "Turn the CFO target into a job description and post it on the Ashby job." | `job-description` |
| "Give me a 30-minute screening guide for the CFO long list." | `screening-interview` |
| "Split the CFO target across four interviewers and add the kits in Ashby." | `divide-and-conquer` |
| "I have 45 minutes with the VP Sales finalist tomorrow. Prep me." | `quick-interview-plan` |
| "Research the CEO candidate's track record at each company she ran." | `candidate-research` |
| "Pull every quote on how the CFO finalist handled a missed quarter, from the three interviews in Metaview." | `quote-ranking` |
| "Assess the COO finalist against the target, from the interviews and the Hogan report." | `leadership-assessment` |
| "Build the reference plan for the CFO finalist: who to call and what to ask." | `reference-check` |
| "Write the underwriting memo on the CFO finalist for the deal team." | `underwriting-memo` |
| "The CFO finalist has a competing offer. Build the closing plan." | `candidate-closing` |
| "Show me the portfolio talent review as a dashboard." | `portfolio-talent-review` |
| "Which executives are at retention risk, and who rated them?" | `list_observations`, `explain_observation` |
| "How has CEO rating moved across the portfolio over the last four reviews?" | `get_portfolio_trend` |
| "What does Team Theory say about back-channel references?" | `grep_methodology`, `read_methodology` |
| "Who sits in every CFO seat in the portfolio, and since when?" | `list_roles`, `list_people` |
| "What do we already know about this company?" | `get_organization_memory`, `list_documents` |
| "Set up a brain that remembers everything about my portfolio." | `talent-brain` |

## Strategic plays

Each play chains recipes and tools. Run the steps in order, confirm with the user between steps when a step's output feeds a decision, and deliver each step's artifact as it completes.

### 1. Hundred-day leadership read on a new platform
1. `get_organization_memory` and `list_roles` for the company: who sits where.
2. For each C-suite seat with interview or diligence material: `leadership-assessment` against a target built with `role-target` from the value-creation plan.
3. `portfolio-talent-review` for the company: which seats are a fit for the plan, which need support, which need a change.

### 2. Portfolio bench check before an exit window
1. `get_portfolio_summary` for succession and retention risk across companies due to exit.
2. `list_observations` for the executives behind each risk; `explain_observation` for any rating the user questions.
3. `portfolio-talent-review` as a dashboard filtered to those companies, with a succession column per critical seat.

### 3. Run a C-suite search end to end
1. `role-target` from the intake call.
2. `job-description`, posted to the ATS on a yes.
3. `screening-interview` for the long list.
4. `divide-and-conquer` for the finalist panel, kits pushed to the ATS.
5. `quote-ranking`, then `leadership-assessment`, per finalist.
6. `reference-check` for the preferred finalist.
7. `underwriting-memo` for the deal team.
8. `candidate-closing` once the firm decides.
9. On a yes: `create_person`, `link_person_to_role` to record the hire.

### 4. Board-ready talent update
1. `list_review_cycles` for the last two cycles and what changed between them.
2. `get_portfolio_trend` for the metrics the board follows.
3. `portfolio-talent-review` as a dashboard, with each changed rating linked to its source.

### 5. Mis-hire post-mortem
1. `list_documents` for the original target, assessment and memo on the executive.
2. `quote-ranking` on the original interviews against what went wrong.
3. Compare the target to what happened, using the methodology on decision traps (S4) and early intervention (S6) via `find_methodology`.
4. Deliver the comparison as an artifact. On a yes, and when a memory tool is present, add what the firm learned as memory cards.

### 6. Arm a portfolio company to hire on its own
1. `role-target` with the portfolio company's CEO for their open seat.
2. `divide-and-conquer` for their panel, as the interactive artifact each interviewer uses live.
3. `reference-check` for their finalist. The CEO runs the process; the talent partner reviews the artifacts.
