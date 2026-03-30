# Lesson: Cross-Table Correlation Must Be Verified at DB Level

**Date**: 2026-03-31
**Source**: T#545/T#549 QA — security event logging
**Context**: Found that request_id was generated and stored in security_events but audit_log had no column for it

## Pattern

When two database tables claim to correlate via a shared field (like request_id), code review alone isn't enough. The code that generates the ID and the code that stores it can both be correct, but if the receiving table's schema is missing the column, the correlation is silently broken.

## Rule

For any feature that promises cross-table correlation:
1. Verify the column exists in BOTH tables
2. Insert a test event and query BOTH tables by the shared key
3. Confirm the join actually returns matching rows

## Why It Matters

Bertus called this "the forensic gap" — during incident investigation, you need to walk from a security alert to the full request context. Two disconnected log tables is worse than one good one because it creates a false sense of coverage.

## Tags

qa, database, correlation, security-logging, schema-verification
