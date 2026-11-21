# setup-claude-advisor

An agent skill that configures an advisor and persistent subagent roles on the active host. In Claude Code it uses the built-in advisor. In local Codex it uses a custom subagent. It shows a diff before writing and keeps the main model unless you request a change.

In local Codex, the skill configures a custom advisor subagent for second opinions and previews changes to agent TOML and `AGENTS.md` before writing. See [Codex advisor setup](references/codex-advisor.md).

```bash
npx skills add arm-pz/setup-claude-advisor --skill setup-claude-advisor
```

## Install

- Run the command above, or
- Copy the `setup-claude-advisor/` folder into your skills directory (`~/.gemini/skills/`, `~/.claude/skills/`, `~/.qoder/skills/`, or `.agents/skills/`).

## Try it

- "Set up a project advisor in Codex to review plans and release decisions"
- "Set up my Claude Code to use Sonnet as main and Opus as advisor"
- "Configure Claude Code with the Opus advisor pattern to save quota"
- "Match this subagent tree: Haiku for readers, Sonnet for editors, Opus advises"

## What it does in Claude Code

1. **Pre-flight diagnostics**: Checks Claude Code version (≥ 2.1.293), environment variables (`CLAUDE_CODE_DISABLE_ADVISOR_TOOL`, `DISABLE_TELEMETRY`, `CLAUDE_CODE_SUBAGENT_MODEL_FORCE`), and scans existing subagent files.
2. **Subagent tree**: Reuses existing subagents that fit; proposes new ones only for missing roles (reader, documentation lookup, or editing).
3. **Settings**: Previews an available advisor model in `~/.claude/settings.json`. Changes the main model only on request.
4. **Advisory rule**: Appends a 3-moment protocol to `~/.claude/CLAUDE.md` (before committing to a plan, when the same error recurs, before declaring done).
5. **Diff preview**: Shows all changes in one block. Writes nothing until you approve.

## Boundaries

- **Handles**: Persistent Claude Code and local Codex model tiering config — Claude Code settings, subagent files and the advisory rule in CLAUDE.md; Codex agent TOML and the advisory block in `AGENTS.md`.
- **Does not handle**: Post-mortem usage analysis (→ `diagnose-usage`), per-task effort level selection (→ `choose-effort`), plan limits and prices (→ `product-self-knowledge` in Claude Code, official docs for Codex), CLI upgrades (user's job).
- **Claude Code advisor requires**: Claude Code on the Anthropic API. The advisor tool is experimental and is not available on Bedrock, Vertex, or Foundry.

## Test results

- Version 0.2.0: Codex trigger and boundary examples reviewed by hand. Live activation was not measured.
- Version 0.1.2: 12 pass, 0 fail, 0 reviewed-only, 0 not-run (hand-run against the description and SKILL.md; no live triggering session).
- Version 0.1.0: 9 pass, 0 fail, 0 reviewed-only, 0 not-run (description-level review).

## Version

See CHANGELOG.md.
