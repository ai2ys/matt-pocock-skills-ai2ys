---
name: ai2ys-handoff-gpt
description: GPT-tuned fork of `handoff` that compacts the current conversation into a fresh-context handoff document, saved to OS temp by default or `./.tmp/` when local storage is requested.
argument-hint: "[local] What will the next session be used for?"
---

Write a handoff document summarising the current conversation so a fresh agent can continue the work.

<path_contract>
Save to the temporary directory of the user's OS — not the current workspace — unless the user explicitly asks for local/project-local storage (e.g. `local`, `project local`, `repo local`, `workspace local`); then save under `./.tmp/`.

Use this file pattern:
`handoff-<YYYYMMDD-HHMMSS>-<topic>-<random>.md`

Use a short kebab-case topic, max 40 chars; fallback to `session`. Use the platform-appropriate temp-file mechanism. On POSIX, `mktemp -t "handoff-$(date -u +%Y%m%d-%H%M%S)-<topic>-XXXXXX.md"` is appropriate.
</path_contract>

<content_contract>
The handoff must be self-contained enough for an agent with a fresh context to continue the work without reading this conversation.

Include these sections when relevant:

- Workspace or project path.
- Read-first artifacts: files, issues, PRDs, ADRs, docs, or URLs the next agent should inspect before acting.
- Current state: what was being worked on and why.
- Decisions made: only settled decisions, not speculation.
- Important corrections or constraints discovered during the session.
- Open questions / next decisions: ordered by leverage.
- Suggested next step.
- Suggested skills: skills the next agent should invoke, if any.
- Redactions: state whether secrets or personal data were omitted.
</content_contract>

Do not duplicate content already captured in other artifacts (PRDs, plans, ADRs, issues, commits, diffs). Reference them by path or URL instead, but include enough context to explain why each reference matters.

Redact any sensitive information, such as API keys, passwords, or personally identifiable information.

If the user passed arguments, treat local/project-local wording as a storage directive only; use the remaining argument text as the next-session focus and tailor the doc accordingly.

After writing the file, report the absolute path and nothing else unless the user asks for more.
