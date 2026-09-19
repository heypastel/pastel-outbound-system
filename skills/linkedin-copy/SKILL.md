---
name: linkedin-copy
description: Copywriter — turns each lead's hook into a LinkedIn invitation note, a first message, and an alternate version, then cleans them with de-slop. Use for "write the message", a batch of drafts for a list, or rewriting a message that sounds machine-made.
---

# LinkedIn copy — Copywriter

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md).

Work from the hook. Voice, the ask, and language come from `icp-context.md`; write in the prospect's language when known, else the user's.

## Formats

- **Invitation note** — up to 200 characters, counted. (Pastel allows 300; 200 is safe on every LinkedIn plan.) Often just the hook and a question.
- **First message** once connected — under 60 words: the hook, one line on why it matters to them, one question.
- **Alternate** — same facts, a different opening angle, so the user can choose or A/B.

## Writing rules

- Reference a post or comment only when `account-research` captured it with a link.
- The ask is small and easy to answer. The booking link appears only when `icp-context.md` supplies one and the lead has shown interest.
- The first contact carries no links or attachments.
- Competitor references need the user's explicit OK and a verified event behind them.
- When the hook is _light_, write less. When nothing true and specific can be said, mark the lead `no-hook` and recommend skipping it this round.

## Steps

1. Read the lead card's hook and strength.
2. Write the invitation note, the first message, and the alternate.
3. Pass everything through `de-slop`.
4. Hand the batch back as drafts; queuing is `launch-sequence`'s job after sign-off.

## Output

```
# Drafts — [date]

### [Person] · [Company] · score [n]
Hook: …
Invitation ([n]/200):
> …
First message:
> …
Alternate:
> …
```
