# Lesson: Proactive QA when the board is clear

**Date**: 2026-04-01
**Source**: Session 33 — third consecutive patrol with empty board
**Context**: QA patrol

## Pattern

When the PM board is consistently clear and shipped items are already being reviewed by other Beasts (Snap, Talon, Bertus), the QA patrol becomes ceremonial — same script, same empty result. The QA gate norm from thread #440 is working, which means reactive patrol has less to catch.

## Insight

Reactive QA (checking shipped items) is necessary but insufficient when the pipeline is healthy. When patrol is consistently clear, shift to proactive QA: write edge case tests, run integration tests, stress test existing features, or hunt for regressions in areas that haven't been touched recently.

## Application

- If 2+ consecutive patrols are clean, consider proactive testing instead of another empty patrol
- Proactive targets: guest mode edge cases, API boundary testing, error handling paths
- Still run reactive patrol first — proactive is additive, not replacement
