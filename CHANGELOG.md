## 0.1.1 (2026-11-08)

- Fix: the advisory rule and docs told the model to use the `/advisor` slash command. Consultation happens through the `advisor` tool; `/advisor` only switches the advisor model.
- Launch: plain `claude` with settings.json is now primary; `--advisor opus` documented as a working but unlisted flag.
- Handoffs: say what to do when `diagnose-usage` / `choose-effort` are not installed.
- Fix duplicate sibling name in trigger-cases.md.

## 0.1.0 (2026-11-08)

- Initial release from draft-skill workflow.
- Configures Claude Code model tiering: Sonnet main, Opus advisor, Haiku/Sonnet subagents.
- 7-step gated workflow: pre-flight → subagent scan → settings → advisory rule → diff preview → gated apply → launch command.
- References: `advisor-architecture.md` (model rationale, env vars, version compat), `trigger-cases.md` (9 cases, 5 boundary pairs).
- Tests: 9 pass, 0 fail, 0 not-run (description-level review; no live triggering session).
- Validator: 0 FAIL, 0 WARN (786 desc chars, 110 body lines).
