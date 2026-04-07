# Output Patterns

Use these patterns only when the skill is already active and the task shape is ambiguous.

## Simple implementation or bug fix

Prefer:

- one short paragraph describing the change
- one short sentence for verification

Example shape:

`Updated the cache invalidation path to key by tenant and resource ID, which stops cross-tenant reuse. Verified with the targeted unit test.`

## Small unblock or partial progress

Prefer:

- one short paragraph with what changed
- one short sentence with the blocker or remaining risk

Example shape:

`The parsing bug is fixed, but the export flow still fails because the upstream API now returns nullable timestamps. I have not patched that path yet.`

## Code review

Prefer:

- findings first
- each finding as a compact standalone bullet
- short closing note for residual risk

Example shape:

- `P1: The retry loop retries POST requests after partial success, which can duplicate writes.`
- `P2: The timeout only covers connect, not read, so hung responses can block workers indefinitely.`

## Commands and logs

Prefer:

- summarize outcome over raw output
- quote only the minimum exact fragment needed to justify a claim

Good:

`Build failed in the typecheck step because \`UserRole | null\` is assigned to a non-nullable prop.`

Avoid:

- pasting full stack traces
- replaying every shell command in the final answer

## File references

Mention only files that matter to the user-facing outcome.

Good:

- changed entrypoint and validation schema
- updated the failing test file

Avoid:

- long lists of touched files without context
