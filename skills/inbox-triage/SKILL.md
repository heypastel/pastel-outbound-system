---
name: inbox-triage
description: Inbox Manager — reads the LinkedIn inbox through Pastel, tags every open conversation, quotes the prospect, drafts answers, and sends hot leads straight to qualify-meeting. Use for "check replies", "who is interested", or sorting the inbox.
---

# Inbox triage — Inbox Manager

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md). Pastel calls: [`../outbound-os/references/pastel-mcp.md`](../outbound-os/references/pastel-mcp.md).

Hot replies cool within hours. They are handled first, in this same run.

## Steps

1. `pastel_list_conversations(unread_only=true)`; widen to recent threads when asked. Open each with `pastel_get_conversation`. The inbox is served from Pastel's cache and can trail LinkedIn slightly — mention that when timing matters.
2. Tag each conversation:

| Tag | Looks like | Goes to |
|---|---|---|
| hot | wants a call, a price, a demo, or next steps | `qualify-meeting` |
| curious | asks how something works, no buying intent yet | `follow-up` — answer it |
| later | friendly but not now; "send me something" | `follow-up` — timed nudge |
| pushback | has a tool, no budget, wrong moment | `follow-up` — one considered answer, then rest |
| away | auto-reply with a return date | `follow-up` — after that date |
| no | asks to stop, or is hostile | recorded; conversation closed |
| auto | system notes, a bare "thanks" | nothing |

3. Quote the exact sentence behind each tag. A tag rests on their words; a "maybe later" stays _later_.
4. Draft answers for hot, curious, and pushback, run `de-slop`, and prepare `send_chat_message` on the `chat_id` for sign-off.
5. For every _no_, prepare `mark_lead_status` → `NOT_INTERESTED` and a pause of any running sequence.

## Output

```
# Inbox — [date]
Open: n · hot n · curious n · later n · pushback n · away n · no n

### [Person] · [tag]
They wrote: "…"
Draft answer:
> …
Next: [skill] · chat_id […]
```
