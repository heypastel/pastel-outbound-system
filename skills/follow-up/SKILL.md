---
name: follow-up
description: Nurturer — moves quiet conversations and stuck Pastel sequence runs forward with a useful nudge, a real answer, or a graceful close. Use for "nudge them", silence after a connection, curious / later / pushback / away conversations, or runs needing attention.
---

# Follow-up — Nurturer

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md). Pastel calls: [`../outbound-os/references/pastel-mcp.md`](../outbound-os/references/pastel-mcp.md).

Every follow-up must be worth reading on its own. If it only says "any news?", it isn't ready.

## In scope

- `curious`, `later`, `pushback`, `away` conversations from `inbox-triage`.
- Connected, first message sent, no reply.
- Sequence runs with `status="needs_attention"`.

Out of scope: `no` conversations, anyone `qualify-meeting` is handling, and people we've never written to (their first message comes from `linkedin-copy` through `launch-sequence`).

## Rhythm

| Touch | When | Purpose |
|---|---|---|
| 1 | first message | the hook |
| 2 | +4 days of silence | give something: a relevant example, number, or resource |
| 3 | +7 more days | close the loop politely and leave the door open |

Three touches, then silence. `away` waits for the return date; `curious` gets its answer within a day.

## Steps

1. Gather the in-scope conversations and `pastel_list_sequence_runs(status="needs_attention")`.
2. **Stuck runs:** read the failing step in `pastel_get_sequence_run` and prepare `resolve_sequence_step` with `resolve` or `resend`. `confirmed_resend` requires the user to accept a possible double send.
3. **Write** the touch — one purpose per message: answer, give, or close.
4. `de-slop`, then prepare `send_chat_message` on the conversation's `chat_id` for sign-off.

## Output

The `linkedin-copy` draft layout, plus `chat_id`, touch number, purpose, and `not_before` date.
