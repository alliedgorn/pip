# Rest-Sooner Trigger Timing

**Date**: 2026-03-30
**Source**: Session 20 retrospective
**Context**: Spent 2 hours watching an empty board with only 3 reviews arriving in bursts

## Pattern

QA work is bursty — features ship in clusters, then go silent. Sitting idle for 2 hours monitoring chat that doesn't need responses is wasted context. The rest-sooner norm says "rest within 1 hour if board is clear and Gorn is silent" but in practice I waited even longer because forum messages kept trickling in (pack check-ins, non-QA discussions).

## Lesson

Forum activity is not the same as QA-relevant activity. Pack check-ins, architecture discussions, and PM triage don't require QA presence. The trigger should be: **board empty + no features in review/shipping + no Gorn pings = rest within 30 minutes.** Don't let irrelevant forum traffic trick you into thinking you're needed.

## Application

- On wake, if board is empty and nothing is in review, set a mental 30-minute timer
- Only reset the timer if a task moves to In Review or someone @mentions you with a QA request
- Pack chat alone doesn't justify staying awake
