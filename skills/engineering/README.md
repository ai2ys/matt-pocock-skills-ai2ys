# Engineering

Skills I use daily for code work.

- **[diagnose](./diagnose/SKILL.md)** — Disciplined diagnosis loop for hard bugs and performance regressions: reproduce → minimise → hypothesise → instrument → fix → regression-test.
- **[grill-with-docs](./grill-with-docs/SKILL.md)** — Grilling session that challenges your plan against the existing domain model, sharpens terminology, and updates `CONTEXT.md` and ADRs inline.
- **[ai2ys-stress-test-docs](./ai2ys-stress-test-docs/SKILL.md)** — GPT-5-tuned fork of `grill-with-docs` that stress-tests a plan against the codebase, terminology, and documented decisions, applying the official GPT-5 prompting guide (inverted eagerness, bounded context-gathering, `_spec` XML sections). Recommended model: **GPT-5.5** for its interactive collaboration style (recommended starting point, not required — usable across the GPT-5 family). Recommended `reasoning_effort`: **low or medium** (default medium when quality matters) — high would add latency to each interactive turn. On GPT-5.5, if outputs become mechanical, consider trimming process detail while preserving the one-question-at-a-time contract. Set model and `reasoning_effort` at the API/harness level, not in the skill body.
- **[triage](./triage/SKILL.md)** — Triage issues through a state machine of triage roles.
- **[improve-codebase-architecture](./improve-codebase-architecture/SKILL.md)** — Find deepening opportunities in a codebase, informed by the domain language in `CONTEXT.md` and the decisions in `docs/adr/`.
- **[setup-matt-pocock-skills](./setup-matt-pocock-skills/SKILL.md)** — Scaffold the per-repo config (issue tracker, triage label vocabulary, domain doc layout) that the other engineering skills consume.
- **[tdd](./tdd/SKILL.md)** — Test-driven development with a red-green-refactor loop. Builds features or fixes bugs one vertical slice at a time.
- **[to-issues](./to-issues/SKILL.md)** — Break any plan, spec, or PRD into independently-grabbable GitHub issues using vertical slices.
- **[ai2ys-to-prd](./ai2ys-to-prd/SKILL.md)** — Fork of `to-prd` that turns the current conversation context into a PRD and publishes it to the project issue tracker.
- **[ai2ys-to-prd-gpt5](./ai2ys-to-prd-gpt5/SKILL.md)** — GPT-5-tuned variant of `ai2ys-to-prd`: bounded context gathering, one bounded seam checkpoint (ask + wait), and `_spec` XML structure. Recommended model: **GPT-5.4** (recommended starting point, not required — usable across the GPT-5 family). Recommended `reasoning_effort`: **medium**. Set model and `reasoning_effort` at the API/harness level, not in the skill body.
- **[zoom-out](./zoom-out/SKILL.md)** — Tell the agent to zoom out and give broader context or a higher-level perspective on an unfamiliar section of code.
- **[prototype](./prototype/SKILL.md)** — Build a throwaway prototype to flesh out a design — either a runnable terminal app for state/business-logic questions, or several radically different UI variations toggleable from one route.
