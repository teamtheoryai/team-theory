# Jobs to be done: the PE talent partner

What a private-equity talent partner hires this plugin to do, across the life of a deal. Use it to see the range of what can be asked, and to route each job to its recipe and tools. The same recipes serve portfolio-company leaders, leadership advisors and heads of talent; the jobs differ, the routing does not.

The talent partner typically covers twenty or more portfolio companies with little or no team. Their output is judged by the deal team and the board.

| Stage | Job | Recipe | Team Theory tools and connectors |
|---|---|---|---|
| **Pre-deal** | Read the management team of a target before the price is set | `leadership-assessment`, `underwriting-memo` | Diligence notes from `~~cloud storage`; management interviews from `~~meeting transcripts`; `~~company data` for the company; methodology: human capital due diligence (`SCI-P-006`) |
| **Pre-deal** | Research a sitting executive's track record | `candidate-research` | `~~talent intelligence`, `~~company data`, web research |
| **Post-close** | Decide which seats to change in the first hundred days | `portfolio-talent-review` | `list_roles`, `list_people`, `get_person`; the value-creation plan from `~~cloud storage` |
| **Search** | Define a seat by the results it must deliver | `role-target` | Intake call from `~~meeting transcripts`; `~~company data`, `~~CRM` |
| **Search** | Write a job description that attracts the right pool | `job-description` | The target; `~~ATS` to post |
| **Search** | Screen a long list fast and consistently | `screening-interview` | The target; the job in `~~ATS` |
| **Search** | Run a panel where each interviewer covers different ground | `divide-and-conquer` | The target; the panel from `~~ATS`; one kit per interviewer back to `~~ATS` |
| **Search** | Prepare a single interviewer quickly, or for a long deep-dive | `quick-interview-plan`, `deep-dive-interview` | The target; the candidate's resume from `~~ATS` |
| **Search** | Track what open searches exist and where they stand | (orchestrator) | `list_searches`, `list_roles`; the jobs in `~~ATS` |
| **Decision** | Pull the evidence on a candidate out of hours of transcripts | `quote-ranking` | Transcripts from `~~meeting transcripts` |
| **Decision** | Assess a finalist against the target | `leadership-assessment` | Target, transcripts, resume, assessments |
| **Decision** | Run references that can't be gamed | `reference-check` | Target, assessment; the references' details from `~~ATS` |
| **Decision** | Put the case for a candidate to the deal partner | `underwriting-memo` | Target, transcripts, references, resume, assessments |
| **Offer** | Close the candidate the firm wants | `candidate-closing` | Assessment, interview notes; `~~email` to draft |
| **Hold** | Review every leadership team across the portfolio | `portfolio-talent-review` | Portfolio metrics, review cycles and observations from Team Theory |
| **Hold** | Find the companies with a thin bench or a retention risk | `portfolio-talent-review` | `get_portfolio_summary`, `list_observations` |
| **Hold** | Explain where a rating came from before a board meeting | (orchestrator) | `list_observations`, `explain_observation`, `list_review_cycles` |
| **Hold** | Plan succession for critical seats | `portfolio-talent-review` | Portfolio metrics; methodology: succession planning (`SCI-F-013`) |
| **Exit** | Show buyers the leadership team is an asset | `portfolio-talent-review`, `leadership-assessment` | Review cycles; methodology: PE human capital lifecycle (`SCI-F-015`) |
| **Function** | Stop rebuilding context before every board meeting, search kickoff and CEO call | `talent-brain` | Team Theory records to seed it; `~~meeting transcripts`, `~~email`, `~~cloud storage` to feed it |
| **Function** | Answer a methodology question for a deal partner or a portfolio CEO | (orchestrator) | `find_methodology`, `read_methodology` |
| **Function** | Keep the firm's records current after a hire | (orchestrator) | `create_person`, `create_role`, `link_person_to_role` |
| **Function** | Show the deal team what the talent function delivered this quarter | (orchestrator) | `list_review_cycles`, `get_portfolio_trend`, `list_searches`; methodology: value demonstration (S7) |
