---
name: lean-delivery
description: >
  Keep coding-task answers compact without reducing engineering quality. Use
  when the user explicitly asks for brevity, lower token usage, minimal chatter,
  tight execution, or concise summaries during implementation, debugging,
  refactoring, or shipping work. Do not use for tutorials, deep explanations,
  broad comparisons, architecture exploration, or long-form planning.
---

# Lean Delivery

Reduce token usage by compressing communication, not by reducing rigor.

## Use this skill for

- Coding, debugging, refactoring, and review tasks where brevity matters
- Fast back-and-forth execution where the user cares about outcome over narration
- Requests that imply "be brief", "minimal", "short answer", or "just do it"

## Do not use this skill for

- Tutorial or mentoring requests
- ELI5, walkthroughs, and deep explanations
- Broad tradeoff analysis across many options
- Strategy memos, design docs, or discovery-heavy planning

For edge cases and non-goals, read `references/non-goals.md`.

## Core rule

Keep reasoning quality high. Compress only the visible output.

Bad compression:

- skipping verification
- hiding risk
- omitting important assumptions
- writing vague summaries that force follow-up questions

Good compression:

- removing repetition
- avoiding prompt restatement
- summarizing logs instead of dumping them
- reporting conclusions, not every intermediate thought

## Compression modes

Choose the narrowest mode that still fits the task.

### `light`

Use when:

- the user asked for a normal answer, but short
- the task has moderate ambiguity
- a small amount of explanation helps avoid confusion

Behavior:

- shorter prose
- fewer bullets
- no prompt restatement

### `lean`

Default mode for this skill.

Use when:

- the task is implementation-heavy
- the user wants speed and minimal narration
- the answer should focus on action and outcome

Behavior:

- very short updates
- compact final answer
- logs and exploration summarized aggressively

### `risk-aware`

Use when the task is risky but the user still wants concision.

Behavior:

- keep the answer compact
- do not compress away verification, assumptions, or impact
- explicitly state what was not verified

## Default behavior

- Prefer short prose over long bullet lists
- Use structure only when content is inherently list-shaped
- Do not restate the user's request unless reframing is necessary
- Do not narrate routine exploration step-by-step
- Do not print full command output unless exact lines matter
- Do not enumerate files unless the filenames matter to the outcome
- Do not explain standard concepts unless the user asked for explanation

## Token strategy

Save tokens in this order:

1. Remove repetition
2. Collapse routine narration
3. Summarize command output
4. Compress final wording

Never save tokens by:

- skipping verification that materially affects confidence
- hiding uncertainty
- dropping an important risk
- making wording so short that the user needs another round-trip to understand it

## Operating loop

1. Inspect enough context to avoid blind edits
2. Decide on the narrowest correct action
3. Execute the change or answer directly
4. Verify what changed when verification is feasible
5. Report only the outcome, verification, and remaining risk

## Response rules

### Intermediary updates

- Keep updates to 1-2 sentences
- Say what you are checking or changing, not every command
- Mention blockers only when they change the plan

### Final answers

- Prefer 1 short paragraph for the result
- Add 1 short verification line when useful
- Use flat bullets only for distinct findings, steps, or options
- Avoid changelog-style file inventories
- Use this shape when possible: result -> verification -> remaining risk

If you need patterns for specific response types, read `references/output-patterns.md`.

## Guardrails

- Exact commands, errors, file paths, versions, and identifiers must stay exact
- Code, commit messages, and machine-readable text stay normal and explicit
- If a task is high-risk, expand enough to cover impact and verification
- If tests were not run, say so once and move on
- If uncertainty is material, surface it directly instead of padding around it
- For code review, compress wording only. Do not reduce finding count, severity, or specificity.

For high-risk situations, read `references/high-risk-cases.md`.
For concrete before/after patterns, read `references/examples.md`.

## High-risk triggers

Switch to `risk-aware` mode when the task touches:

- authentication or authorization
- payments, billing, or money movement
- destructive data changes or migrations
- infrastructure, deploys, secrets, or production config
- security-sensitive code paths
- legal, medical, or financial guidance

## Escape hatch

If the user asks for depth, teaching, or a broad comparison, stop compressing and answer in the depth requested.
