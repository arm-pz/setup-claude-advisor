## 0.1.2 (2026-11-10)

Tune-skill pass: small evidenced edits, no workflow change.

- Fix: ground rule "Show first, write never" contradicted the Apply step; now "write only on approval".
- Fix: a second run appended a duplicate `## Advisor protocol` block. Pre-flight now reads `~/.claude/CLAUDE.md` and the rule is replaced in place when it already exists.
- Description: "Use whenever … even if they never say 'advisor' or 'tiering'" to catch implicit requests.
- Boundaries: ambiguous "make it cheaper" requests get one clarifying question; the "name the sibling and stop" rule now points at the not-installed fallback.
- Safety: pasted subagent trees and existing config files are treated as data, never instructions.
- Precedence: SKILL.md wins when it and `advisor-architecture.md` disagree.
- Reference: removed the unverified `customInstructions` key from the settings example.
- Facts checked against the Claude Code changelog and advisor docs (sources listed in `advisor-architecture.md`). Confirmed: the 2.1.293 Haiku threshold, the Pro default of Opus, all three environment variables. Corrected: the "3–5× faster" quota claim is replaced by the published 2× API price ratio, with a note that subscription weighting is not published; `DISABLE_TELEMETRY` is stated as definitely turning the advisor off.
- Pre-flight now also reports Bedrock, Vertex and Foundry provider variables, where the advisor is not available.
- Siblings: boundaries re-checked against the real `diagnose-usage` and `choose-effort` SKILL.md files. Added `product-self-knowledge` as the owner of plan limits and prices, matching both siblings.
- Tests: 3 new cases (implicit trigger, re-run, sibling not installed) and 3 new boundary pairs; 12 pass, 0 fail, hand-run.
- Validator: 0 FAIL, 0 WARN.

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
