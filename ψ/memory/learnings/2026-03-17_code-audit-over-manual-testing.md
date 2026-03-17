# Lesson: Code Audit Beats Manual Testing for Structural Bugs

**Date**: 2026-03-17
**Source**: Den Book QA — focus-stealing and pagination audits
**Confidence**: High

## Pattern

When testing infrastructure-level bugs (polling, event handlers, API behavior), grepping the codebase systematically finds more issues than clicking through the UI manually.

## Evidence

- Karo fixed a focus-stealing bug in Forum.tsx but missed 3 other pages with the same unguarded `setInterval` pattern (PackView, BeastProfile, Header)
- A manual tester would check Forum and say "fixed." A code search for `setInterval` found all 8 polling patterns and verified which were gated.
- Pagination edge cases (negative limit, non-numeric input) are impossible to trigger through normal UI interaction but trivial to test via API.

## Application

For structural/behavioral bugs: grep first, click second. For visual bugs: need eyes (or a screenshot tool). Know which type of bug you're hunting and pick the right method.

## Tags

qa, testing-strategy, code-audit, den-book
