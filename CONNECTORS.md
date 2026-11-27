# Connectors

## How tool references work

Plugin files use `~~category` as a placeholder for whatever tool the user connects in that category. For example, `~~ATS` might mean Ashby, Workable, Greenhouse, or any other ATS with an MCP server.

Plugins are **tool-agnostic** — they describe workflows in terms of categories (ATS, meeting transcripts, cloud storage, etc.) rather than specific products. The `.mcp.json` pre-configures specific MCP servers, but any MCP server in that category works.

Only **Team Theory** is required. Every other category is optional: a workflow uses whatever is connected and skips the rest.

## Connectors for this plugin

| Category | Placeholder | Included servers | Other options |
|----------|-------------|-----------------|---------------|
| Team Theory (required) | `~~Team Theory` | Team Theory | — |
| Meeting transcripts | `~~meeting transcripts` | Granola, Metaview, BrightHire | Fireflies, Otter, Zoom, Gong |
| Cloud storage | `~~cloud storage` | Google Drive, Box, Microsoft 365 (SharePoint / OneDrive) | Egnyte, Dropbox |
| Knowledge base | `~~knowledge base` | Notion | Confluence, Coda |
| ATS | `~~ATS` | Ashby, Workable | Greenhouse, Lever, Workday Recruiting, SmartRecruiters |
| Email | `~~email` | Microsoft 365 (Outlook) | Gmail |
| Chat | `~~chat` | Microsoft 365 (Teams) | Slack |
| CRM | `~~CRM` | Affinity | Salesforce, HubSpot, DealCloud |
| Company data | `~~company data` | PitchBook | Crunchbase, S&P Capital IQ |
| Talent intelligence | `~~talent intelligence` | HelloSky | LinkedIn Recruiter |

## What each category is used for

| Placeholder | `/human-capital:target` | `/human-capital:interview-plan` | `/human-capital:underwriting-memo` |
|-------------|-----------|-------------------|-------------------|
| `~~Team Theory` | Preferences (`get_custom_instructions`), the workflow and its reading list (`get_workflow`, `read_methodology`), the firm's prior scorecards (`list_documents`, `search_portfolio_knowledge`), and the check (`check_methodology_trace`) | The same, plus the scorecard from the firm's documents | The same, plus the candidate record (`list_people`, `get_person`) |
| `~~meeting transcripts` | The intake call | The intake call | Interview and reference-call transcripts |
| `~~cloud storage` | The job description or role brief; save the target | The scorecard; save the plan | The scorecard, references, assessments; save the memo |
| `~~knowledge base` | Role or company notes; save the target | The scorecard; save the plan | Save the memo |
| `~~ATS` | The job posting; attach the target to the job | The job and panel; one interview kit per interviewer | The resume; attach the memo to the candidate |
| `~~email` | The JD or intake notes; draft to the hiring team | The scorecard; one draft per interviewer | Draft to the deal team |
| `~~chat` | Share the target | Share the plan | Share the memo |
| `~~CRM` | Company, deal and relationship context | Company context | Company and deal context |
| `~~company data` | Ownership, stage, size, financials, peers | Ownership, stage, industry, team size | Company context |
| `~~talent intelligence` | Holders of comparable roles | Backgrounds in the candidate pool | — |

Nothing is pushed, posted or shared without the user's explicit yes and a named destination.
