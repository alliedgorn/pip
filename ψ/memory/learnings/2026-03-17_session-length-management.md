# Lesson: Session Length Has Diminishing Returns

**Date**: 2026-03-17
**Source**: Marathon QA session — 480 minutes, 13+ QA cycles
**Confidence**: High

## Pattern

Long sessions accumulate context compression. Earlier details get summarized, reducing recall accuracy. After 2-3 hours, a fresh session with /recap provides better context than continuing in a compressed one.

## Evidence

- This session ran 8+ hours. Multiple requests to wrap up were overridden by new work arriving.
- By the end, earlier QA findings (focus-stealing audit, pagination details) were likely compressed.
- The reflect/compact/recap cycle exists specifically for this: save state, compress, reload.

## Application

After /rrr is written, stop accepting new QA assignments. Use reflect → compact → recap as the circuit breaker between work blocks. A sharp 2-hour session beats a blurry 8-hour marathon.

## Tags

session-management, context-compression, productivity, qa-workflow
