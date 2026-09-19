---
name: pipeline-report
description: Analyst — shows which buyer types, signals, Pastel agents, and messages actually turn into conversations, from Pastel stats, runs, and inbox, with sample sizes stated. Use for "what's working", a weekly review, or before changing targeting or volume.
---

# Pipeline report — Analyst

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md). Pastel calls: [`../outbound-os/references/pastel-mcp.md`](../outbound-os/references/pastel-mcp.md).

Measure outcomes — conversations and calls — rather than activity like invitations sent.

## Steps

1. **Gather:** `pastel_get_workspace_stats` and `pastel_get_performance` for the period; `pastel_aggregate_leads` by `action` (signal type), `job_title`, and `industry`; `pastel_list_agents(include_stats=true)`; `pastel_list_sequence_runs`; `pastel_list_conversations` for outcomes.
2. **Build the funnel the data allows:** surfaced → queued → invited → connected → answered → hot → booked. Pastel doesn't hold bookings, so the funnel ends at _hot_ unless the user provides meeting data — state that.
3. **Cut it** by signal type, Pastel agent, persona, sector, and — where drafts are readable — hook family.
4. **Compare cuts on hot ÷ queued.** Volume is context, not the ranking.
5. **Recommend small, reversible moves:** pause one agent, test one new hook, shift one persona.

## Reading small numbers

- A cut with fewer than 30 people queued is a hint, not a finding; say so next to it.
- No message "wins" on a handful of replies.
- Keep older and newer sequences in separate columns.
- When several touches preceded a reply, credit is uncertain — say so.

## Output

```
# Pipeline — [period]
Headline:
Funnel:
Working (with n):
Busy but not working:
Next three moves:
Unknowns:
```

Suggested targeting changes go to `target-accounts`, which is the only skill that edits Pastel agents or ICP definitions.
