---
name: to-prd-ai2ys
description: Turn the current conversation context into a PRD and publish it to the project issue tracker. Use when user wants to create a PRD from the current context.
---

This skill takes the current conversation context and codebase understanding and produces a PRD. Do NOT interview the user — just synthesize what you already know.

The issue tracker and triage label vocabulary should have been provided to you — run `/setup-matt-pocock-skills` if not.

## Process

1. Explore the repo to understand the current state of the codebase, if you haven't already. Use the project's domain glossary vocabulary throughout the PRD, and respect any ADRs in the area you're touching.

2. Sketch out the seams at which you're going to test the feature. Existing seams should be preferred to new ones. Use the highest seam possible. If new seams are needed, propose them at the highest point you can.

Check with the user that these seams match their expectations.

3. Write the PRD using the template below, then publish it to the project issue tracker. Apply the `ready-for-agent` triage label - no need for additional triage.

<prd-template>

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

<user-story-example>
### 1. As a mobile bank customer, I want

- US-1.1: to see balances on my accounts, so that I can make better informed decisions about my spending.
- US-1.2: to see recent transactions for each account, so that I can understand where my money is going.
</user-story-example>

Rules:
- Group stories by actor. Each heading must name a single actor/persona — not a feature area, workflow stage, or system component.
- Number actor groups globally: 1, 2, 3, etc. Preserve existing actor group numbers across revisions: a newly added actor takes the next unused number; never renumber existing groups, as that would change their story IDs.
- Number stories within each actor group using stable IDs: US-1.1, US-1.2, US-2.1, US-2.2, etc. IDs must be unique within the PRD and must not change across revisions unless a story is materially split, merged, or removed.
- Start each story with "to <verb>" and include both the <capability or action> and the <benefit>.
- Do not repeat the full actor phrase in every story.
- Keep the list extensive (cover all aspects of the feature), but merge duplicate or near-duplicate stories.
- Use story IDs when referring to stories in issues, implementation notes, testing decisions,
or follow-up planning.

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

Any further notes about the feature.

</prd-template>
