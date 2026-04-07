# High-Risk Cases

Lean delivery still applies, but compression must not hide material risk.

## Expand the answer when the task affects

- authentication, sessions, roles, or permission checks
- secrets, environment variables, deployment config, or infrastructure state
- payments, billing logic, payouts, invoicing, or subscription changes
- database migrations, backfills, destructive writes, or data retention
- security boundaries, encryption, signing, or untrusted input handling
- production incidents or rollback-sensitive fixes

## Minimum extra detail to include

- what changed
- why it is safe or what remains unsafe
- what was verified
- what was not verified
- any assumption that could change the outcome

## Example shape

`Updated the role gate so admin-only routes now check both org membership and scoped permission. Verified with the authorization test suite; I did not validate against a live production token set.`

## Never compress away

- destructive impact
- unverified rollout risk
- migration order
- secret handling
- user-visible behavior changes
