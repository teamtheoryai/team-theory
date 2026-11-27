# Human Capital Plugin

A [Team Theory](https://teamtheory.ai) plugin for Claude Cowork and Claude Code, bringing Team Theory's human capital methodology into your hiring workflows.

Executive hires are made on instinct far more often than anyone admits. The role gets defined in a 30-minute intake call that lives in someone's notes, the job description is a recycled template, and the interview loop is four smart people asking the same "tell me about yourself" questions and comparing gut feels afterwards. The facets that actually predict success in the role get covered twice, or not at all.

Team Theory turns that into a system. This plugin pulls the role context you already have — job descriptions in Google Drive, Box or SharePoint, intake calls in Granola, Metaview or BrightHire, the job in Ashby or Workable, company context from PitchBook and Affinity — grounds it in Team Theory's hiring methodology, and produces the documents a disciplined search runs on: a role target that defines what success looks like, an interview plan that splits the target across the panel so every facet is tested once, and an underwriting memo that puts the evidence on a candidate in front of the deal team.

## Recipes

Each recipe pulls the inputs from your connected tools, has Team Theory supply the method, writes the deliverable as an artifact, checks it against the methodology, and offers to push it where your team works.

### 1. Role target
A Team Theory scorecard for the role: mission, outcomes and competencies. Pulls the job description or intake call you point to, plus company and market context.

**Slash command:** `/human-capital:target`

```
/human-capital:target CFO for a PE-backed industrial services company, intake call in Granola from Tuesday
```

### 2. Divide & Conquer interview plan
One interview guide per interviewer, built from the scorecard, with a facet coverage map and a scoring table per guide. Offers to push one interview kit per interviewer to your ATS.

**Slash command:** `/human-capital:interview-plan`

```
/human-capital:interview-plan from the CFO target above, 4 interviewers
```

### 3. Candidate underwriting memo
A one-page memo on a candidate for the deal team, built from the interview transcripts, reference calls, resume, assessments and scorecard. Every claim cites its source.

**Slash command:** `/human-capital:underwriting-memo`

```
/human-capital:underwriting-memo the CFO finalist, interviews in Metaview
```

## MCP Connectors

Only Team Theory is required. Everything else is optional: the workflows use whatever is connected and skip the rest. See [CONNECTORS.md](CONNECTORS.md) for categories and alternatives.

| Connector | URL | Purpose |
|-----------|-----|---------|
| **Team Theory** | `https://app.teamtheory.ai/mcp` | Required — the methodology (workflows and their reading lists, the trace check), your preferences, and your firm's records and documents |
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
   - **Claude Code:** `/plugin marketplace add teamtheoryai/human-capital-plugin`, then `/plugin install human-capital@human-capital`
   - **Cowork:** add this repository as a plugin
2. Sign in to Team Theory when prompted, and connect any optional platforms you use
3. Run `/human-capital:target` with the role, and point Claude at the JD or intake call if you have one
4. Run `/human-capital:interview-plan` to split the target across your interview panel
5. Run `/human-capital:underwriting-memo` once the candidate has been interviewed and referenced
6. Say yes when Claude offers to push a result to your ATS, drive or channel — nothing is pushed, posted or shared without your explicit yes

You can also just ask in plain words — "build a scorecard for the CFO role", "split the interviews across four people" — and the right workflow starts.

## File Structure

```
├── .claude-plugin/
│   ├── plugin.json                  # Plugin manifest
│   └── marketplace.json             # Lets this repo be added as a marketplace
├── .mcp.json                        # 13 MCP server connections
├── CONNECTORS.md                    # Connector categories and ~~placeholders
├── LICENSE
├── README.md
├── commands/
│   ├── target.md                    # /human-capital:target
│   ├── interview-plan.md            # /human-capital:interview-plan
│   └── underwriting-memo.md         # /human-capital:underwriting-memo
└── skills/
    ├── role-target/
    │   └── SKILL.md                 # Recipe: role target (scorecard)
    ├── divide-and-conquer/
    │   └── SKILL.md                 # Recipe: Divide & Conquer interview plan
    └── underwriting-memo/
        └── SKILL.md                 # Recipe: candidate underwriting memo
```

## How the recipes are written

Every skill in this plugin is a recipe, in the sense Zapier uses the word. **A skill holds no judgment.** It says:

- **Which tools to call and what to fetch from each:** the transcript from `~~meeting transcripts`, the job from `~~ATS`, the firm's records from Team Theory.
- **Which Team Theory workflow to load:** `get_workflow` with the workflow's id, then `read_methodology` for every page on its reading list. How to read the evidence, which standard to apply and which sections the deliverable contains all come from there, from the user's preferences (`get_custom_instructions`), and from the firm's own workflows when `get_workflow` lists one.
- **The output format:** the artifact's layout, length, tables and citation style. Format only, never content.
- **Where the result goes:** the destinations to offer, after an explicit yes.

Each recipe ends with `check_methodology_trace` and fixes what it reports before the user sees the result.

Keep new skills to this shape. A rule about what a good question, competency or memo is belongs in Team Theory's methodology, not in a skill: written there, it reaches every recipe and the Team Theory app at once, and improves with each methodology release. Written in a skill, it is a second copy that drifts.

**Commands** are entry points: one sentence to orient the user, then the skill.

**Design decisions:**
- Tool-agnostic — skills refer to connector categories (`~~ATS`, `~~meeting transcripts`…), so any tool in a category works
- Grounded, not generated — every deliverable is built from the Team Theory workflow and the user's own sources
- Working steps stay quiet — one line per step in chat; the user sees the artifact, not the scaffolding
- Drafts, not sends — nothing is pushed to an ATS, drive or channel without an explicit yes and a named destination

## License

[MIT](LICENSE)
