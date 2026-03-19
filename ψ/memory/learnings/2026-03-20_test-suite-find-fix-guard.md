# Learning: The Find-Fix-Guard Cycle

**Date**: 2026-03-20
**Context**: Building automated test suite (Task #61) — first test found a bug on first build

## Pattern

When a test suite finds a bug:
1. **Find** — test documents the current (broken) behavior
2. **Fix** — developer ships the fix
3. **Guard** — flip the test from documenting the bug to asserting the correct behavior

The test becomes a regression guard permanently. The bug can never come back silently.

## Example

- forum.test.ts: "POST without author succeeds" (documents bug)
- Karo fixes: author now required (Task #63)
- Test flipped to: "POST without author returns 400" (regression guard)

## Application

- When writing tests, include known-bug tests that document current broken behavior
- When a fix ships, immediately flip the test — don't wait
- The test suite is not just for finding bugs — it's for preventing their return
- This cycle is the primary value proposition for automated testing
