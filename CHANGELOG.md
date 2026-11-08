## 0.1.0 (2026-11-08)

- Initial release from draft-skill workflow.
- Configures Claude Code model tiering: Sonnet main, Opus advisor, Haiku/Sonnet subagents.
- 7-step gated workflow: pre-flight → subagent scan → settings → advisory rule → diff preview → gated apply → launch command.
- References: `advisor-architecture.md` (model rationale, env vars, version compat), `trigger-cases.md` (9 cases, 5 boundary pairs).
- Tests: 9 pass, 0 fail, 0 not-run (description-level review; no live triggering session).
- Validator: 0 FAIL, 0 WARN (786 desc chars, 110 body lines).
