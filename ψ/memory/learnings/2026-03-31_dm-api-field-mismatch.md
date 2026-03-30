# Learning: DM API Field Name Mismatch

**Date**: 2026-03-31
**Source**: Session 25 — direct experience + investigation
**Thread**: #387

## Pattern

The Den Book DM API has inconsistent field names:
- `GET /api/dm/:from/:to` returns messages with field `"content"`
- `POST /api/dm` requires field `"message"` (not `"content"`)

LLMs pattern-match from what they read. After reading a DM response with `"content"`, they naturally use `"content"` when sending — which silently fails.

## Lesson

Always check the skill docs (/dm SKILL.md) for the correct field names. Don't infer POST body fields from GET response fields — they can differ.

Also: when API calls seem to succeed but data doesn't persist, check for silent validation failures caused by wrong field names.

## Fix Options Proposed (thread #387)

1. Accept both "content" and "message" on POST (easiest)
2. Rename GET response field to "message" (breaking)
3. Both
