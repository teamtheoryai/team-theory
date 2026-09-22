# CLAUDE.md

## Versioning

**Every change bumps `version` in `.claude-plugin/plugin.json`.** Claude only re-fetches an installed plugin when that version changes, so a change without a bump never reaches users. Patch (0.2.0 → 0.2.1) for fixes and wording, minor (0.2.x → 0.3.0) for new commands, skills or connectors. One bump per PR is enough.

## Before pushing

Run `claude plugin validate .` and `claude plugin validate .claude-plugin/plugin.json`; both must pass.
