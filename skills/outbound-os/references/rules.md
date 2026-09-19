# House rules — shared by every outbound skill

## Warm-up

1. Look for `icp-context.md` in the project root, `.agents/`, `.codex/`, or `.claude/`. It is the brief: offer, buyers, no-go list, proof, voice, autopilot settings. No file → carry on, flag that the output is generic, and suggest `icp-context-setup`.
2. With Pastel connected, call `pastel_list_capabilities` once per session to learn the granted scopes and which actions are live. Every Pastel call follows [`pastel-mcp.md`](pastel-mcp.md).

## Evidence

- **Everything is sourced.** Each name, title, company fact, signal, email, and reply quote comes from a Pastel result or a public page you can link. Anything you could not source is written `[missing: what]`, and the work continues around it.
- **Pastel remembers; it does not search.** Results are what the workspace's agents already collected. "No results" means "not collected yet". The fix is upstream — a new or broader Pastel agent via `target-accounts` — so report the empty result and offer that fix.
- **Label every number.** A score is either Pastel's Copilot ranking or our own rubric; say which.
- **Use the right state word:** _drafted_ (text exists), _proposed_ (awaiting the user), _queued_ (Pastel accepted it), _done_ (`pastel_get_sequence_run` shows the step executed). Pastel engagements are asynchronous, so a successful request means _queued_.
- **Say when outbound is the wrong lever.** A vague offer or an imaginary buyer shows up as silence; name it instead of adding volume.

## Review mode and autopilot

- **Review mode** is the default. Any change in Pastel — lead or post status, ICP definitions, agents, comments, reactions, invitations, messages, sequences — is laid out for the user and requested only after a clear yes.
- **Autopilot** starts only when the user turns it on in this session, or `icp-context.md` says `Autopilot: on` with a minimum score. It acts only on leads at or above that score, never on the no-go list, and logs each request with its action id.
- `bypass_daily_limit` is `true` only when the user asks for it on that specific action. Pastel's daily caps keep the LinkedIn account healthy.

## Output

Hand over the finished thing — the table, the score, the draft, the queued run — rather than suggestions. Tables for lists. Close every report with an **Unknowns** section. Anything worth forwarding is saved as `outbound-[topic]-[YYYY-MM-DD].md` when files can be written.

## Lead card

Skills pass leads to each other as lead cards, so later stages reuse what earlier ones established. Empty fields hold `[missing]`.

```
lead_id:        # Pastel id
person:         # name · headline
company:
profile_url:
email:
signal:         # what happened, where, when
fit:            # in | borderline | out — reason
no_go:          # matched no-go rule, if any
hook:           # the reason to talk now, one sentence
score:          # 0-100 · rubric parts · Copilot rank if any
draft:          # current message text
run_id:         # Pastel sequence run, once queued
conversation:   # quiet | hot | curious | later | pushback | away | no
next_step:
owner:          # skill that acts next
```
