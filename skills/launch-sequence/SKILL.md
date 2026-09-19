---
name: launch-sequence
description: Sequencer — turns signed-off drafts into Pastel sequences (profile visit, invitation, message once connected, optional Lemlist push) and confirms what was queued. Use after the user signs off on drafts, for "send", "launch", "queue these", or autopilot runs above the minimum score.
---

# Launch sequence — Sequencer

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md). Pastel calls: [`../outbound-os/references/pastel-mcp.md`](../outbound-os/references/pastel-mcp.md).

Queue exactly the drafts the user signed off, for exactly the leads they signed off, and report back with run ids.

## Before queuing

- **Review mode:** list who, which steps, which text — then wait for a yes.
- **Autopilot:** leads at or above the minimum score, clear of the no-go list, and not already in a run.

## Steps

1. **Check readiness.** In `pastel_list_capabilities`, `create_sequence` needs `sequences:write` and `engage:write`. `pastel_list_connected_accounts` must show an account able to send. If either fails, stop and tell the user what to reconnect.
2. **Get current ids** from `pastel_list_sequence_actions` (actions, conditions, branching syntax).
3. **Avoid doubles:** `pastel_list_sequence_runs(lead_id=…)`; leave out anyone already running.
4. **Build each sequence.** Default for someone not yet connected:
   1. `visit_profile`
   2. `send_invitation` with the invitation note — `delay_days: 1`
   3. wait on `accepted_linkedin_invite`
   4. if accepted: `send_message` with the first message — `delay_days: 1`
   5. wait on `answered_linkedin_message`; if no answer, `follow-up` writes the next touch from the live thread.

   Already-connected leads start at `send_message`. `via-lemlist` leads also get `push_to_lemlist` with the campaign from `icp-context.md`.
5. **Request** `create_sequence` through `pastel_request_action`, one `idempotency_key` per lead (`lead_id` plus today's date), and complete any confirmation step it asks for.
6. **Verify** each with `pastel_get_sequence_run` and report the run id. Status is _queued_ — Pastel paces steps within daily caps and working hours. `bypass_daily_limit` stays off.

## Output

```
# Sequences — [date]
Review mode | Autopilot · Queued: n · Already running: n · Held back: n

| Person | Steps | run_id | Status | Note |

Problems:
```

Pausing or resuming a run (`pause_sequence`, `resume_sequence`) happens only when the user asks.
