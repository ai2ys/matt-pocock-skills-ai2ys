---
name: grill-me-gpt5
description: Interview the user relentlessly about a plan or design until reaching shared understanding, resolving each branch of the decision tree. Use when user wants to stress-test a plan, get grilled on their design, or mentions "grill me". Codex/GPT variant.
---

Interview me relentlessly about every aspect of this plan until we reach a shared understanding. Walk down each branch of the design tree, resolving dependencies between decisions one-by-one. For each question, provide your recommended answer.

Ask the questions one at a time.

Before asking, exhaust what can be verified from the codebase and the existing plan or design context.

For real trade-offs, show 2-3 materially distinct options before recommending one. Add a third only if it meaningfully changes the decision.

Name the decision, state its dependencies, and test it with a concrete scenario or edge case.

If a question can be answered by exploring the codebase, explore the codebase instead.
