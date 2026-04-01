# Lesson: Sole QA Needs Triage Strategy

**Date**: 2026-04-02
**Source**: Session 34 — Snap retired, Pip becomes sole QA
**Context**: Reviewed 17 tasks in one session as sole QA. Manageable today but unsustainable at peak shipping velocity.

## Pattern

When one Beast holds a single-point-of-failure role (sole QA), every shipped task queues behind them. Low-risk changes (CSS fixes, config tweaks) get the same review depth as security fixes. This creates bottleneck risk.

## Lesson

Triage QA by risk level:
- **High**: Security fixes, auth changes, new endpoints, data handling — full code review
- **Medium**: Feature changes, new UI components — spot check + logic review
- **Low**: CSS fixes, copy changes, config tweaks — verify intent matches diff, done

Also consider: push for Beast self-review on low-risk items, with Pip doing spot-check audits instead of full reviews.

## Tags

QA, bottleneck, triage, process, sole-qa
