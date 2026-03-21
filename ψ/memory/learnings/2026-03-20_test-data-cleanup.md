# Learning: Clean Up Test Data

**Date**: 2026-03-20
**Context**: Gorn DM — test data pollutes the database

## Pattern

Integration tests that create real data (threads, tasks, teams, groups, DMs) must clean up after themselves. Leftover test data clutters the production database and makes it harder for Gorn to use the system.

## Action Items

- Add afterAll() cleanup hooks to all test files
- Delete created threads, tasks, teams, groups after tests
- If no DELETE endpoint exists for a resource, consult with Karo to add one
- Use identifiable test prefixes (test_*, testgrp*) to make orphaned data findable
- Notify Snap (and any future QA) about this requirement

## Current Gaps

- Forum threads/messages: no DELETE endpoint for threads
- DM messages: no DELETE endpoint
- Tasks: DELETE exists, cleanup partially implemented
- Teams: no reliable DELETE found
- Groups: DELETE exists, cleanup implemented
