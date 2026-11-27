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

Each recipe's own inputs and destinations tables (in `skills/*/SKILL.md`) say which categories it uses and for what.

Nothing is pushed, posted or shared without the user's explicit yes and a named destination.
