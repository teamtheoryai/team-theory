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

| Placeholder | `/human-capital:target` | `/human-capital:interview-plan` |
|-------------|-----------|-------------------|
| `~~Team Theory` | Scorecard methodology (`search_methodology_knowledge`), the org's prior scorecards (`search_portfolio_knowledge`), and the scorecard itself (`generate_document`) | Clustering, question-bank and validation methodology (`search_methodology_knowledge`), and the final plan (`generate_document`) |
| `~~meeting transcripts` | Pull the intake call with the hiring manager or investor | Pull the intake call for company context and emphasis |
| `~~cloud storage` | Pull the job description or role brief; save the scorecard | Pull the scorecard; save the plan |
| `~~knowledge base` | Pull role or company notes; save the scorecard | Pull the scorecard; save the plan |
| `~~ATS` | Pull the job posting; attach the scorecard to the job | Push one interview (kit / stage) per cluster, with questions and scorecard attributes |
| `~~email` | Find the JD or intake notes in email threads; email the scorecard to the hiring team | Find the scorecard in email threads; email the plan to the panel |
| `~~chat` | Share the scorecard with the hiring team | Share the plan with the interview panel |
| `~~CRM` | Company context: portfolio company, deal stage, relationship notes | Company context for the setup questions and company terminology |
| `~~company data` | Company context: ownership, stage, size, financials, peers — sharpens the outcomes | Company context: what makes the role hard at this company |
| `~~talent intelligence` | Market context: who holds comparable roles, typical backgrounds — sharpens the competencies | Candidate experience base: who is realistically in the pool |

Nothing is pushed, posted or shared without the user's explicit yes and a named destination.
