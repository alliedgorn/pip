# Lesson: API Namespace Mismatch + Always Test Dedup

**Date**: 2026-03-28
**Source**: Session 15 — Forge CSV import QA

## API Namespace

The Forge UI feature uses `/api/routine` not `/api/forge`. Don't assume the API namespace matches the UI name. When testing a new feature, **ask for the endpoint** before brute-forcing paths.

**Correct Forge/Routine endpoints:**
- POST /api/routine/import/alpha-progression (multipart file upload, gorn-only)
- Needs `?as=gorn` for auth

## Always Test Duplicate Import

Uploading the same data file twice is a universal edge case. Found that Forge import had no dedup — 156 sessions became 312. Fixed by Karo with date-based dedup.

**Test pattern**: Upload → verify count → upload same file → verify count unchanged.

## Check History Before Filing Bugs

PWA manifest returning HTML looked like a bug, but PWA was intentionally reverted for Capacitor native app. Check recent threads/decisions before filing.
