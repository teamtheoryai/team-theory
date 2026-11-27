# What Team Theory's methodology covers, and how to find it

Team Theory's methodology (tt-science) is a released, versioned library of hiring science. The connector serves one release. Use this map to know what exists and to phrase queries; read the pages themselves for the content. Never answer a methodology question from this map.

## The library

| Area | What it holds | How to reach it |
|---|---|---|
| **Curriculum** (stages S1–S7) | The method end to end, one folder per stage | `list_methodology` with `curriculum/` |
| **Frameworks** (`SCI-F-001`–`018`) | The named models the method uses | `list_methodology` with `frameworks/`; read by id |
| **SOPs** (`SCI-P-001`–`006`) | Runnable procedures | Read by id |
| **Specifications** (`SCI-A-001`–`007`) | What a deliverable must contain | Read by id |
| **Instructions** (`SCI-I-001`–`016`) | The text the agent follows for one piece of work | Reached through a workflow's reading list |
| **Workflows** (`SCI-W-001`–`014`) | The deliverables, step by step | `get_workflow` |
| **Question banks** | Over 1,300 behavioral questions by C-suite function (13), by competency, by interview stage, plus washout and development probes | `list_methodology` with `question-banks/` |
| **Science** | The research evidence base, with evidence-strength ratings | `list_methodology` with `science/` |
| **Psychometrics** | Reference pages for common instruments | `list_methodology` with `psychometrics/` |
| **AI readiness** | Competencies, probes, reference questions and target outcomes for AI readiness in leaders | `list_methodology` with `ai-readiness/` |
| **Examples** | A fictional fund and its portfolio, used in worked examples | `examples/`. Fictional: never present as real. |

### Curriculum stages and their subjects

| Stage | Subjects |
|---|---|
| **S1 Role definition** | The Target document, Blue Sky exercise, stakeholder alignment, cultural differentiation, specialist vs. generalist, common errors |
| **S2 Sourcing** | The sourcing pyramid, the hook conversation, candidate motivation (ten factors), network building, common errors |
| **S3 Assessment** | Interview formats, the P.R.O.B. framework, the Archaeological Dig, note-taking, managing interview dynamics, the debrief protocol |
| **S4 Decision-making** | The two-stage decision model, information reliability hierarchy, rating design, the R.R.M. weakness framework, bias mitigation, HiPPO and groupthink, decision traps |
| **S5 Process architecture** | Process tiers by role level, RACI, the Talgo reference script, back-channel references, offer management, competing offers |
| **S6 Post-hire** | Onboarding intelligence, 30-60-90 milestones, target to performance management, early intervention, retention, succession planning, human capital due diligence in PE |
| **S7 Talent partner excellence** | The portfolio intelligence function, value demonstration, trusted-advisor reputation, firm culture, influencing founders in minority positions, DEI as accuracy |

### Named frameworks

The Target Document · P.R.O.B. Question Framework · 6-Box Question Matrix · The Archaeological Dig (Golden Triangle) · Sourcing Effectiveness Pyramid · Ten Factor Motivation Framework · Two-Stage Decision Model · Four Horsemen of Hiring Bias · Information Reliability Hierarchy · R.R.M. Weakness Framework · Process Architecture & Offer Management · Post-Hire Excellence Framework · Succession Planning Matrix · Talent Partner Excellence Framework · PE Human Capital Lifecycle · Psychometric Interpretation Protocol · Decision Signals · AI-Readiness Competencies

### SOPs

Hiring Process Design · Talgo Reference Interview Script · Target Document Creation · Onboarding Intelligence Brief · Portfolio Talent Review · Human Capital Due Diligence

## How to query it

1. **A deliverable:** `get_workflow` first. Its reading list is the exact set of pages to read. Do not search instead.
2. **A subject in plain words:** `find_methodology` ("how to weigh reference evidence", "interviewing a CFO who has never been a CFO"). It returns page and section ids, not answers.
3. **A named concept or exact term:** `grep_methodology` with the name ("P.R.O.B.", "Talgo", "backchannel", "9-box"). Literal, not a pattern. Try the variants a name is written in ("PROB", "P.R.O.B.").
4. **Browsing:** `list_methodology` with no path for everything, a folder (`frameworks/`) for its pages, or a page id for its sections.
5. **Reading:** `read_methodology` with an id (`SCI-F-009`), a path (`curriculum/03-assessment/debrief-protocol.md`) or a section (`SCI-F-009#tiers`). Read every part of a long page.
6. **Citing:** cite exactly as `read_methodology` says ("Cite as …").

If `find_methodology` and `grep_methodology` both return nothing, the methodology does not cover the subject. Say so. Do not fill the gap with general knowledge presented as Team Theory's method.

Phrase queries by subject and stage, not by the user's wording: "reference checks for a CFO" → `grep_methodology` "reference" and `find_methodology` "reference calls for a finance executive"; "should we keep the CEO" → `find_methodology` "assessing a sitting CEO against the value-creation plan" and the S6 and S7 folders.
