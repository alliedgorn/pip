# Lesson: Check Full Composite Key Before Flagging Duplicates

**Date**: 2026-03-28
**Source**: Session 17 — T#429 false positive

## What Happened

Flagged 12 "duplicate" exercises in the Forge library based on name alone. Karo closed as false positive — the entries are unique by (name, equipment) composite key. E.g. "Bench Press" with Barbell vs Dumbbells vs Smith Machine are legitimately different exercises.

## Rule

When checking for duplicates, always identify the full uniqueness constraint (composite key) before filing a bug. A name match alone doesn't mean duplicate — check all dimensions of the record.

## Apply When

- QA'ing any data import or library content
- Checking for dedup issues in any table
- Before filing "duplicate data" bugs
