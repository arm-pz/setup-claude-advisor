# setup-claude-advisor

Configure Claude Code for quota-optimised model tiering: Sonnet as the working model, Opus as the on-call strategic advisor, and Haiku/Sonnet subagents assigned by role. Shows every proposed change as a diff preview before touching any file.

## Install

- Copy the `setup-claude-advisor/` folder into your skills directory (`~/.gemini/skills/`, `~/.claude/skills/`, `~/.qoder/skills/`, or `.agents/skills/`), or
- `npx skills add arm-pz/setup-claude-advisor --skill setup-claude-advisor`

## Try it

- "Set up my Claude Code to use Sonnet as main and Opus as advisor"
- "Configure Claude Code with the Opus advisor pattern to save quota"
- "Match this subagent tree: Haiku for readers, Sonnet for editors, Opus advises"

## What it does

1. **Pre-flight diagnostics**: Checks Claude Code version (≥ 2.1.293), environment variables (`CLAUDE_CODE_DISABLE_ADVISOR_TOOL`, `DISABLE_TELEMETRY`, `CLAUDE_CODE_SUBAGENT_MODEL_FORCE`), and scans existing subagent files.
2. **Subagent tree**: Reuses existing subagents that fit; proposes new ones only for missing roles (code reader → Haiku, doc lookup → Haiku, code editor → Sonnet).
3. **Settings**: Patches `~/.claude/settings.json` with `model: sonnet` and `advisorModel: opus`.
4. **Advisory rule**: Appends a 3-moment protocol to `~/.claude/CLAUDE.md` (before committing to a plan, when the same error recurs, before declaring done).
5. **Diff preview**: Shows all changes in one block. Writes nothing until you approve.

## Boundaries

- **Handles**: Persistent Claude Code model tiering config — settings, subagent files, advisory rule in CLAUDE.md.
- **Does not handle**: Post-mortem usage analysis (→ `diagnose-usage`), per-task effort level selection (→ `choose-effort`), plan limits and prices (→ `product-self-knowledge`), CLI upgrades (user's job).
- **Requires**: Claude Code on the Anthropic API. The advisor tool is experimental and is not available on Bedrock, Vertex, or Foundry.

## Test results

- Version 0.1.2: 12 pass, 0 fail, 0 reviewed-only, 0 not-run (hand-run against the description and SKILL.md; no live triggering session).
- Version 0.1.0: 9 pass, 0 fail, 0 reviewed-only, 0 not-run (description-level review).

## Version

See CHANGELOG.md.
