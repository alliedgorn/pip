# Learning: Audit WebSocket Broadcast Payloads

**Date**: 2026-03-27
**Source**: Session 12 — spec #13 WS debugging with Gorn

## Pattern

When a WebSocket is declared "read-only" or "safe for unauthenticated access," always audit what data is actually being broadcast. The distinction between "event notification" (IDs only) and "full content broadcast" is a security boundary.

## Context

Den Book WS was broadcasting full objects — task details, comment content, Prowl personal tasks — to all connected clients. The pack (including security Beast) initially said "it's just metadata." Gorn caught the actual data leakage by checking DevTools.

## Rule

Before approving unauthenticated WS access:
1. Grep all `wsBroadcast()` calls
2. Check if payloads contain content, not just IDs
3. Strip to minimum: `{event, id}` — let frontend fetch details via authenticated REST

## Tags

websocket, security, data-leakage, broadcast, audit
