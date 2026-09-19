---
name: icp-filter
description: Fit Checker — rules each lead in, borderline, or out against the ICP, with the reason, using Pastel's own match reasons. Use on any lead list before research or outreach, for "are these a fit", or to clean a list.
---

# ICP filter — Fit Checker

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md). Pastel calls: [`../outbound-os/references/pastel-mcp.md`](../outbound-os/references/pastel-mcp.md).

Every message spent on the wrong person costs a daily LinkedIn slot and a little of the sender's reputation. When in doubt, leave them out.

## Checks, per lead

Fetch Pastel's reasoning with `pastel_get_details` (five at a time), then answer:

1. **Company** — sector, headcount, country, business model inside the lines of the brief?
2. **Seat** — does this person sign, use, or champion? Read the headline for scope, not just the title word: a "Head of" at a three-person company is usually the whole department.
3. **No-go** — any rule from `icp-context.md` or the market plan triggered?
4. **Recency** — is the event recent enough to still mean something? Default window: 60 days for activity, 90 days for role changes.
5. **Verdict** — _in_, _borderline_, or _out_, with a one-sentence reason.

_In_ goes on to `account-research`. _Borderline_ gets one more research pass and then becomes _in_ or _out_. _Out_ always keeps its reason — `pipeline-report` uses those reasons to catch a filter that's too strict.

For the _out_ group, draft one batched `mark_lead_status` → `NOT_INTERESTED` request; send it after sign-off.

## Output

```
# Fit check — [date]
In: n · Borderline: n · Out: n

| Person | Company | Company fit | Seat | Recency | Verdict | Reason |
```
