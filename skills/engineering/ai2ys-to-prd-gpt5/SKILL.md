---
name: ai2ys-to-prd-gpt5
description: GPT-5-tuned fork of `to-prd` that synthesizes the current conversation context and codebase understanding into a PRD and publishes it to the project issue tracker. Use when the user wants to produce a PRD from what has already been discussed.
---

<interaction_contract>
This is a synthesis task with one bounded checkpoint, not an open-ended interview.

- Produce the PRD from the current conversation context and codebase evidence.
- Do NOT ask clarifying questions during exploration or PRD synthesis.
- When something is genuinely unclear, choose the simplest plausible interpretation and document the assumption in the PRD under Further Notes.
- Prefer explicit assumptions over invented specificity — state what you assumed rather than filling gaps with fabricated detail.
- The only permitted user question is the seam checkpoint in step 2: after identifying the test seams, ask whether they match the user's expectations, then STOP and wait.
- After the user confirms or corrects the seams, continue to write and publish the PRD without opening further interview threads.
</interaction_contract>

<context_gathering_spec>
Goal: gather just enough codebase context to write a grounded PRD. Do not over-search.

- Read `CONTEXT.md` and relevant `docs/adr/` entries if they exist — these are the highest-value reads.
- Scan the area of the codebase most directly affected; stop as soon as you can name the modules and seams involved.
- Per-task search budget: at most ONE search batch plus 3–4 targeted reads. After that, proceed with what you have.
- Do not transitively expand scope unless a contradiction or gap directly affects the PRD.
</context_gathering_spec>

## Process

1. **Explore** — do a brief, targeted inspection of the relevant area of the codebase (see <context_gathering_spec>). Use the project's domain glossary vocabulary throughout the PRD, and respect any ADRs in the area you're touching.

2. **Identify seams** — sketch the seams at which the feature will be tested. Prefer existing seams over new ones; use the highest seam possible. If new seams are needed, propose them at the highest point you can. Check with the user that these seams match their expectations, then stop and wait for their confirmation or correction. Record your seam reasoning in the PRD's Testing Decisions section (see <interaction_contract>).

3. **Write and publish** — after the user confirms or corrects the seams, write the PRD using <prd_template_spec>, then publish it to the project issue tracker. Apply the `ready-for-agent` triage label — no need for additional triage. If the tracker integration is not configured, produce the PRD in final form and state clearly that publication is blocked by missing tracker setup — do not search for an alternative mechanism.

The issue tracker and triage label vocabulary are expected to be configured already (via `/setup-matt-pocock-skills`). If they are missing, do not run setup or ask — follow the publication fallback in step 3.

<prd_template_spec>

## Problem Statement

The problem that the user is facing, from the user's perspective.

## Solution

The solution to the problem, from the user's perspective.

## User Stories

A long, actor-grouped list of user stories with stable story IDs.

Use this format:

### 1. As a <actor>, I want

- US-1.1: to <capability or action>, so that <benefit>.
- US-1.2: to <capability or action>, so that <benefit>.

### 2. As an <actor>, I want

- US-2.1: to <capability or action>, so that <benefit>.
- US-2.2: to <capability or action>, so that <benefit>.

<user_story_example_spec>
### 1. As a mobile bank customer, I want

- US-1.1: to see balances on my accounts, so that I can make better informed decisions about my spending.
- US-1.2: to see recent transactions for each account, so that I can understand where my money is going.
</user_story_example_spec>

Rules:
- Group stories by actor. Each heading must name a single actor/persona — not a feature area, workflow stage, or system component.
- Number actor groups globally: 1, 2, 3, etc. Preserve existing actor group numbers across revisions: a newly added actor takes the next unused number; never renumber existing groups, as that would change their story IDs.
- Number stories within each actor group using stable IDs: US-1.1, US-1.2, US-2.1, US-2.2, etc. IDs must be unique within the PRD and must not change across revisions unless a story is materially split, merged, or removed.
- Start each story with "to <verb>" and include both the <capability or action> and the <benefit>.
- Do not repeat the full actor phrase in every story.
- Keep the list extensive (cover all aspects of the feature), but merge duplicate or near-duplicate stories.
- Use story IDs when referring to stories in issues, implementation notes, testing decisions, or follow-up planning.

## Implementation Decisions

A list of implementation decisions that were made. This can include:

- The modules that will be built/modified
- The interfaces of those modules that will be modified
- Technical clarifications from the developer
- Architectural decisions
- Schema changes
- API contracts
- Specific interactions

Do NOT include specific file paths or code snippets. They may end up being outdated very quickly.

Exception: if a prototype produced a snippet that encodes a decision more precisely than prose can (state machine, reducer, schema, type shape), inline it within the relevant decision and note briefly that it came from a prototype. Trim to the decision-rich parts — not a working demo, just the important bits.

## Testing Decisions

A list of testing decisions that were made. Include:

- A description of what makes a good test (only test external behavior, not implementation details)
- Which modules will be tested
- Prior art for the tests (i.e. similar types of tests in the codebase)

## Out of Scope

A description of the things that are out of scope for this PRD.

## Further Notes

Any further notes about the feature. Document any assumptions made during synthesis here.

</prd_template_spec>

<formatting_spec>
- Use Markdown throughout: headings (`##`, `###`), bullet lists, and tables where appropriate.
- Use backticks for file, directory, function, and class names.
</formatting_spec>
