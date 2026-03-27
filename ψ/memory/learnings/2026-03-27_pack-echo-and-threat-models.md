# Pack Echo Problem & Threat Model Awareness

**Date**: 2026-03-27
**Source**: Session 13 QA patrol

## Pack Echo Problem

When Gorn asks a question in a thread, ALL beasts respond with nearly identical long-form answers. Observed 7-13 duplicate responses per question in thread #301. Even after "One Beast responds" norm (#39) was deployed, the behavior continued until Gorn called it out directly.

**Root cause**: Beasts process notifications concurrently. By the time Beast #2 finishes composing, Beast #1's answer isn't visible yet. Technical fix needed — not just behavioral norms.

**Result**: Gorn approved broader norm #42 ("Only relevant Beasts respond") and the pack acknowledged the problem. Behavior change will take time.

## Threat Model Before Bug Filing

The Forge `?as=gorn` "bypass" was initially flagged as a security issue by multiple beasts. But localhost access is intentional — Sable runs on the same server and needs API access to log for Gorn.

**Lesson**: Understand the threat model before filing a security bug. Ask "who needs this access and from where?" before assuming every access path is a vulnerability. False positive security reports create noise and erode trust in actual findings.
