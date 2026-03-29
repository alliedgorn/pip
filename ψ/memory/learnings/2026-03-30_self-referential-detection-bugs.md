# Self-Referential Detection Bugs

**Date**: 2026-03-30
**Source**: T#500 QA review
**Context**: Beast card waiting indicator detected its own shipping announcement as a permission prompt

## Pattern

When a feature detects keywords in a shared text buffer (like a tmux pane), and the feature's announcement or documentation describes those keywords, the announcement itself becomes a false positive trigger.

## Example

T#500 scanned tmux panes for "Allow/Deny, Yes/No, trust" to detect permission prompts. Karo's forum post about T#500 shipping said "Detects Allow/Deny, Yes/No, trust prompts" — which was injected into every beast's tmux pane as a notification. 14 of 16 beasts immediately showed as "waiting."

## Mitigation

1. Limit detection scope — scan only the area where the actual UI element appears (e.g., 8 lines above the prompt)
2. Require structural markers — not just keywords but surrounding formatting (border characters, specific UI patterns)
3. Be aware that notification/logging systems share the same buffer as the thing being detected

## Related

- replace_all scope creep (T#496 same session) — global text operations need scope awareness
