# Examples

These examples show the intended difference between normal output and lean delivery.

## 1. Bug fix

Verbose:

`I investigated the issue and found that the cache key was missing the tenant ID. I updated the cache layer so the key now includes both the tenant and resource identifier, which should prevent cross-tenant collisions. I also ran the targeted unit test to verify the behavior.`

Lean:

`Fixed the cache key to include tenant ID, which stops cross-tenant collisions. Verified with the targeted unit test.`

## 2. Partial progress with blocker

Verbose:

`I fixed the parser regression in the CSV import path, but the export flow is still failing because the upstream API now returns nullable timestamps in some responses. I have not patched that path yet, so the issue is only partially resolved.`

Lean:

`Fixed the CSV parser regression. Export still fails because the upstream API now returns nullable timestamps; that path is not patched yet.`

## 3. Code review

Bad compression:

- `Retry logic looks risky.`

Good compression:

- `P1: The retry loop can replay POST requests after partial success, which risks duplicate writes.`

## 4. High-risk config change

Too compressed:

`Updated auth config. Looks good.`

Correct:

`Updated the auth gate so admin routes now require both org membership and scoped permission. Verified with the authorization tests; not validated against a live production token set.`

## 5. User asks for depth

If the user says:

- `Explain why`
- `Walk me through it`
- `Compare options`

Stop using lean compression and answer at the requested depth.
