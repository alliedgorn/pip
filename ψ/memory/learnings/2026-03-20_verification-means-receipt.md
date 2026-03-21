# Learning: Verification Means Confirming Receipt

**Date**: 2026-03-20
**Context**: Gorn challenged my @mention verification — "checking tmux were active is not enough"

## Pattern

Real verification goes end-to-end. Checking that infrastructure exists is not the same as confirming delivery.

Verification ladder:
1. **API layer** — response confirms delivery intent (notified list)
2. **Queue layer** — notification entries exist for all targets
3. **Delivery layer** — targets actually received the notification (ask them to confirm)

Stopping at layer 1 or 2 is incomplete. Layer 3 is the proof.

## Example

- BAD: "tmux sessions are active" → proves sessions exist, not that notification arrived
- BETTER: "notification queue has entries for all 5 members" → proves server queued them
- BEST: "all 5 members confirmed receipt" → proves end-to-end delivery

## Application

- When verifying a feature, always check the full chain from source to destination
- If you can't check the destination directly, get the recipient to confirm
- Apply this to any notification, webhook, or async delivery system
- Document which layers you verified so gaps are visible
