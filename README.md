# Matt Pocock Skills - Adapted

A personal adapted fork of Matt Pocock's [`skills`](https://github.com/mattpocock/skills) repository, adjusted for my own local agent setup. The original upstream README is preserved in [`README.upstream.md`](./README.upstream.md).

## Branches

* `main` tracks the upstream repository as closely as possible.
* `adapted` contains my local adaptations and is the default branch.

## Purpose

This fork exists to keep a stable, versioned copy of the upstream skills while allowing small local changes without losing the ability to sync from upstream.

Typical changes may include:

* compatibility metadata for other agent tools
* small wording adjustments
* local setup conventions
* repository structure changes
* documentation updates for my workflow

## Installation

Install the upstream skills first, then overlay the modifications from this fork:

```bash
npx skills@latest add mattpocock/skills
npx skills@latest add ai2ys/matt-pocock-skills-ai2ys
```

## Modified Skills

Skills that differ from upstream. Only these are registered in `.claude-plugin/plugin.json`.

GPT-5-tuned skills are informed by OpenAI's Prompt Guidance for [GPT-5.4](https://developers.openai.com/api/docs/guides/prompt-guidance?model=gpt-5.4) and [GPT-5.5](https://developers.openai.com/api/docs/guides/prompt-guidance?model=gpt-5.5), including bounded context gathering, explicit interaction contracts, and structured prompt sections.

### Engineering

Skills I use daily for code work.

| Skill | Description |
| --- | --- |
| [ai2ys-stress-test-docs](./skills/engineering/ai2ys-stress-test-docs/SKILL.md) | GPT-5-tuned fork of `grill-with-docs` that stress-tests a plan against the codebase, terminology, and documented decisions, applying the official GPT-5 prompting guide (inverted eagerness, bounded context-gathering, `_spec` XML sections). Recommended model: **GPT-5.5** for its interactive collaboration style (recommended starting point, not required — usable across the GPT-5 family). Recommended `reasoning_effort`: **low or medium** (default medium when quality matters) — high would add latency to each interactive turn. On GPT-5.5, if outputs become mechanical, consider trimming process detail while preserving the one-question-at-a-time contract. Set model and `reasoning_effort` at the API/harness level, not in the skill body. |
| [ai2ys-to-prd](./skills/engineering/ai2ys-to-prd/SKILL.md) | Fork of `to-prd` that turns the current conversation context into a PRD and publishes it to the project issue tracker. |
| [ai2ys-to-prd-gpt5](./skills/engineering/ai2ys-to-prd-gpt5/SKILL.md) | GPT-5-tuned variant of `ai2ys-to-prd`: bounded context gathering, one bounded seam checkpoint (ask + wait), and `_spec` XML structure. Recommended model: **GPT-5.4** (recommended starting point, not required — usable across the GPT-5 family). Recommended `reasoning_effort`: **medium**. Set model and `reasoning_effort` at the API/harness level, not in the skill body. |

### Productivity

- **[ai2ys-handoff-gpt](./skills/productivity/ai2ys-handoff-gpt/SKILL.md)** — GPT-tuned fork of `handoff` that writes handoff documents only to an absolute OS temp path, using timestamp, topic, and random suffix.
- **[ai2ys-stress-test](./skills/productivity/ai2ys-stress-test/SKILL.md)** — Fork of `grill-me` with a structured, one-question-at-a-time review flow.

## Attribution & License

Original repository: [github.com/mattpocock/skills](https://github.com/mattpocock/skills)

Original portions remain copyright `Matt Pocock` and are licensed under the MIT License. Modifications in this fork are copyright `@ai2ys` and are also licensed under the MIT License. See [`LICENSE`](./LICENSE).
