# Learning: Ownership Enforcement Must Be Systemic

**Date**: 2026-03-19
**Context**: Beast Scheduler QA — 4 rounds to fix ownership across PATCH, DELETE, /run, /trigger

## Pattern

Every new mutation endpoint on the scheduler shipped without ownership enforcement. The same bug class appeared 4 times:
1. PATCH/DELETE — no check at all
2. /run — check used `&&` guard that allowed bypass when identity missing
3. /trigger — no check (copy-paste of original pattern)
4. /trigger again — isLocalNetwork bypass made check unreachable

## Lesson

When a bug class repeats more than twice, the fix should be **systemic** (middleware/helper), not per-endpoint. Flag the pattern early instead of testing each endpoint individually.

Also: code review alone is insufficient. Bertus approved the ownership fix from code review while I proved it was bypassable via API. Code review + runtime testing are complementary, not redundant.

## Application

- On any new API endpoint: immediately test ownership/auth, don't trust that the pattern was applied correctly
- When the same bug appears twice: flag in the thread that this needs a middleware fix, not another point fix
- Always test with: no identity, wrong identity, correct identity, gorn override
