# Human Capital Plugin

A [Team Theory](https://teamtheory.ai) plugin for Claude Cowork and Claude Code, bringing Team Theory's human capital methodology into your hiring workflows.

Executive hires are made on instinct far more often than anyone admits. The role gets defined in a 30-minute intake call that lives in someone's notes, the job description is a recycled template, and the interview loop is four smart people asking the same "tell me about yourself" questions and comparing gut feels afterwards. The facets that actually predict success in the role get covered twice, or not at all.

Team Theory turns that into a system. This plugin pulls the role context you already have — job descriptions in Google Drive, Box or SharePoint, intake calls in Granola, Metaview or BrightHire, the job in Ashby or Workable, company context from PitchBook and Affinity — grounds it in Team Theory's hiring methodology, and produces the documents a disciplined search runs on: a role target that defines what success looks like, an interview plan that splits the target across the panel so every facet is tested once, and an underwriting memo that puts the evidence on a candidate in front of the deal team.

## Recipes

Each recipe pulls the inputs from your connected tools, has Team Theory supply the method, produces the deliverable as an artifact, checks it against the methodology, and offers to push it where your team works. One recipe per Team Theory workflow.

| Stage | Recipe | Slash command | Delivers |
|---|---|---|---|
| Role definition | Role target | `/human-capital:target` | The scorecard: mission, outcomes, competencies |
| Role definition | Job description | `/human-capital:job-description` | A posting built from the target; pushed to the ATS on a yes |
| Assessment | Screening interview | `/human-capital:screening-interview` | A one-page screening guide for the long list |
| Assessment | Quick interview plan | `/human-capital:quick-interview-plan` | A one-page plan for one interviewer and one candidate |
| Assessment | Deep-dive interview | `/human-capital:deep-dive-interview` | A career-walk interview guide |
| Assessment | Divide & Conquer interview plan | `/human-capital:interview-plan` | An **interactive** artifact: one tab per interviewer with questions, notes and scoring; one kit per interviewer in the ATS |
| Assessment | Candidate research | `/human-capital:candidate-research` | A cited background report on a candidate's career and companies |
| Decision | Quote finder and ranker | `/human-capital:quote-ranking` | Every relevant verbatim quote, ranked and mapped to the scorecard |
| Decision | Leadership assessment | `/human-capital:leadership-assessment` | An evidence-based assessment against the target |
| Process | Reference check | `/human-capital:reference-check` | Who to call and what to ask each reference |
| Decision | Underwriting memo | `/human-capital:underwriting-memo` | A one-page memo on a candidate for the deal team |
| Process | Candidate closing | `/human-capital:candidate-closing` | A closing strategy, actions and draft messages |
| Post-hire | Portfolio talent review | `/human-capital:portfolio-talent-review` | An **interactive dashboard** of the firm's portfolio ratings, risks and trends, every value traceable to its source |
| Setup | Talent Partner Brain | `/human-capital:talent-brain` | A self-maintaining wiki of every company, seat, executive and search in the portfolio, inside the user's Cowork project, seeded from Team Theory and fed on a schedule from their meetings, email and documents |


General talent questions (Team Theory's General Advice workflow) go to the orchestrator, which answers from the methodology.

You can also just ask in plain words, or describe a bigger goal ("run the CFO search end to end", "get me ready for the board's talent update"): the **orchestrator** subagent routes it and chains the recipes. See the [cookbook](reference/cookbook.md) for prompts and plays.

## MCP Connectors

Only Team Theory is required. Everything else is optional: the workflows use whatever is connected and skip the rest. See [CONNECTORS.md](CONNECTORS.md) for categories and alternatives.

| Connector | URL | Purpose |
|-----------|-----|---------|
| **Team Theory** | `https://app.teamtheory.ai/mcp` | Required — the methodology (workflows and their reading lists, the trace check), your preferences, and your firm's memory, records, documents and portfolio data |
| **Granola** | `https://mcp.granola.ai/mcp` | Intake-call transcripts and meeting notes |
| **Metaview** | `https://mcp.metaview.ai/mcp` | Interview intelligence — intake and interview transcripts |
| **BrightHire** | `https://app.brighthire.ai/mcp/v1` | Interview intelligence — intake and interview transcripts |
| **Google Drive** | `https://drivemcp.googleapis.com/mcp/v1` | Job descriptions, role briefs; save targets and plans |
| **Box** | `https://mcp.box.com` | Job descriptions, role briefs; save targets and plans |
| **Notion** | `https://mcp.notion.com/mcp` | Role and company notes; save targets and plans |
| **Ashby** | `https://mcp.ashbyhq.com/mcp/v1` | ATS — job context; push interview kits |
| **Workable** | `https://mcp.workable.com/mcp` | ATS — job context; push interview kits |
| **Microsoft 365** | `https://microsoft365.mcp.claude.com/mcp` | SharePoint and OneDrive documents, Outlook email, Teams — pull JDs and intake notes; save and share targets and plans |
| **Affinity** | `https://mcp.affinity.co/mcp` | CRM — portfolio company, deal and relationship context |
| **PitchBook** | `https://premium.mcp.pitchbook.com/mcp` | Company data — ownership, stage, size, financials and peers |
| **HelloSky** | `https://api.hellosky.ai/mcp/` | Talent intelligence — comparable leaders and the realistic candidate pool |

### Native Integrations

These are native Claude integrations — no MCP connector install needed. They're available when the user connects them in Claude Desktop or Cowork.

| Integration | Purpose |
|-------------|---------|
| **Slack** | Share the target or plan with the hiring team |

## Quick Start

1. Install the plugin:
   - **Claude Code:** `/plugin marketplace add teamtheoryai/team-theory`, then `/plugin install human-capital@human-capital`
   - **Cowork:** add this repository as a plugin
2. Sign in to Team Theory when prompted, and connect any optional platforms you use
3. Run `/human-capital:target` with the role, and point Claude at the JD or intake call if you have one
4. Run `/human-capital:interview-plan` to split the target across your interview panel
5. Run `/human-capital:underwriting-memo` once the candidate has been interviewed and referenced, or any recipe in the table above
6. Say yes when Claude offers to push a result to your ATS, drive or channel — nothing is pushed, posted or shared without your explicit yes

You can also just ask in plain words — "build a scorecard for the CFO role", "split the interviews across four people" — and the right workflow starts.

## File Structure

```
├── .claude-plugin/
│   ├── plugin.json                  # Plugin manifest
│   └── marketplace.json             # Lets this repo be added as a marketplace
├── .mcp.json                        # MCP server connections
├── CONNECTORS.md                    # Connector categories and ~~placeholders
├── agents/
│   └── orchestrator.md              # Routes requests across recipes, connectors and Team Theory
├── commands/                        # Short aliases: target, interview-plan, underwriting-memo
├── reference/
│   ├── recipe.md                    # The five steps every recipe runs
│   ├── jobs-to-be-done.md           # What a PE talent partner uses the plugin for
│   ├── cookbook.md                  # Example prompts and multi-step plays
│   ├── methodology-map.md           # What Team Theory's methodology covers, and how to query it
│   └── memory-and-documents.md      # Reading and writing the firm's documents, records and memory
└── skills/                          # One recipe per Team Theory workflow
    ├── role-target/  job-description/  screening-interview/  quick-interview-plan/
    ├── deep-dive-interview/  divide-and-conquer/  candidate-research/  quote-ranking/
    ├── leadership-assessment/  reference-check/  underwriting-memo/  candidate-closing/
    ├── portfolio-talent-review/
    └── talent-brain/                # Sets up the Talent Partner Brain: SKILL.md, the project instructions, the build spec
```

## How the recipes are written

Every skill in this plugin is a recipe, in the sense Zapier uses the word. **A skill holds no judgment.** It says:

- **Which tools to call and what to fetch from each:** the transcript from `~~meeting transcripts`, the job from `~~ATS`, the firm's records from Team Theory.
- **Which Team Theory workflow to load:** `get_workflow` with the workflow's id, then `read_methodology` for every page on its reading list. How to read the evidence, which standard to apply and which sections the deliverable contains all come from there, from the user's preferences (`get_custom_instructions`), and from the firm's own workflows when `get_workflow` lists one.
- **The output format:** the artifact's layout, length, tables and citation style. Format only, never content.
- **Where the result goes:** the destinations to offer, after an explicit yes.

The steps every recipe shares (load the method, fetch, produce, check with `check_methodology_trace`, offer destinations) live once in [reference/recipe.md](reference/recipe.md). A skill file holds only its workflow id, inputs table, destinations table and output format.

**To add a recipe:** copy any skill folder, set the workflow id, fill the three tables and the output format, and add a row to the orchestrator's routing table.

Keep new skills to this shape. A rule about what a good question, competency or memo is belongs in Team Theory's methodology, not in a skill: written there, it reaches every recipe and the Team Theory app at once, and improves with each methodology release. Written in a skill, it is a second copy that drifts.

**The orchestrator** (`agents/orchestrator.md`) is a subagent that routes requests: it holds the map of what each connector and each Team Theory tool can do, hands off to a recipe when one matches, runs multi-step plays from the cookbook, and otherwise loads the matching Team Theory workflow. Like the recipes, it holds no judgment of its own. When you add a recipe or a connector, add it to the orchestrator's map.

**The reference files** give the orchestrator and the recipes their orientation: the jobs a PE talent partner does, a cookbook of prompts and plays, a map of what Team Theory's methodology covers and how to query it, and how to read and write the firm's documents and memory. They describe what exists and where to find it; they hold no method.

**Team Theory as the record.** Recipes read the firm's memory (`get_organization_memory`) before they write, read whole documents with `get_document` rather than search fragments, and write records only with an explicit yes. Tools to save documents and add memories are on Team Theory's roadmap; the recipes check for them on every run and use them when they appear.

**Commands** are short aliases for the three original recipes. Every other recipe is invoked by its skill name.

**Design decisions:**
- Tool-agnostic — skills refer to connector categories (`~~ATS`, `~~meeting transcripts`…), so any tool in a category works
- Grounded, not generated — every deliverable is built from the Team Theory workflow and the user's own sources
- Working steps stay quiet — one line per step in chat; the user sees the artifact, not the scaffolding
- Drafts, not sends — nothing is pushed to an ATS, drive or channel without an explicit yes and a named destination

## License

[MIT](LICENSE)
