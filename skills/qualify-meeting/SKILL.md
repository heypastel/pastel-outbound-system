---
name: qualify-meeting
description: Qualifier — checks a hot conversation on four points (pain, power, priority, profile), asks the one question that closes the biggest gap, and suggests booking only when the case is there. Use on hot replies, demo requests, or "is this worth a call".
---

# Qualify meeting — Qualifier

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md). Pastel calls: [`../outbound-os/references/pastel-mcp.md`](../outbound-os/references/pastel-mcp.md).

A calendar slot is the most expensive thing in the funnel. It goes to conversations that have earned it.

## The four Ps

| P | Question | Evidence |
|---|---|---|
| Pain | Have they described a problem we remove? | their sentence, quoted |
| Power | Can they decide, or bring the person who does? | role + what they said |
| Priority | Is there a reason to act in the next ~90 days? | deadline, event, target |
| Profile | Are they still inside the core segment? | `icp-filter` verdict |

Four of four: propose a time. Two or three: ask about the weakest P. One or none: keep nurturing via `follow-up`. If the user's team qualifies with BANT, MEDDICC, or similar, express the result in their framework.

## Steps

1. Read the full conversation with `pastel_get_conversation`.
2. Score the four Ps with evidence.
3. Write the next message: a single question aimed at the weakest P, or a booking proposal matching the ask in `icp-context.md` (booking link only if one is configured). Nothing is booked until the prospect agrees to a time.
4. Not ready → hand to `follow-up` naming the missing P.
5. Once a call is booked, prepare `mark_lead_status` → `PROCESSED`.

## Output

```
# Qualification — [Person]
Verdict: book | ask | nurture
Pain: "…"
Power:
Priority:
Profile:
Next message:
> …
Booking link: [link] | [missing]
```
