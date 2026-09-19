---
name: find-signals
description: Signal Scout — pulls people from Pastel who just did something that suggests they could buy (engaged with a relevant post, a competitor, a problem thread), each with the event and its date. Use for "find leads", "who's in market", "who engaged with this post or competitor", or building a warm list.
---

# Find signals — Signal Scout

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md). Pastel calls: [`../outbound-os/references/pastel-mcp.md`](../outbound-os/references/pastel-mcp.md).

Each row answers "what did this person just do?". A matching job title answers a different question and does not earn a row.

## Signal ladder (strongest at the top)

1. They wrote about the pain we remove, or asked their network for a tool.
2. They commented on or reacted to a competitor or a category thread.
3. Something changed for them: new seat within 90 days, hiring into the team we equip, money raised for this problem.
4. They engaged with our posts, or replied to a comment from `post-engagement`.
5. Their company mirrors a customer named in `icp-context.md`.

## Steps

1. Load the market plan or `icp-context.md`.
2. **Pastel's ranking first:** `pastel_recommend_best_leads` with the plan's filters (`job_titles`, `countries`, `industries`, `icp_definition_id`; `created_since` for a time window). `pastel_query_leads` when the user wants to browse past the top.
3. **For a specific post** ("who engaged with X"): locate it with `pastel_query_posts`, then `pastel_leads_for_post`.
4. **Capture the event.** Ranked items include it in `evidence` (`primary_event_type`, `primary_event_at`, `selection_reason`). For other rows, or to read the actual post or comment, call `pastel_get_details` five ids at a time.
5. Stop at 25 rows unless the user sets a size. Remove only the unmistakable misfits (our own team, competitor staff); fit judgement is `icp-filter`'s job.

Zero results → report zero, then offer one change at a time (persona, country, or signal type), or `target-accounts` to point a Pastel agent at new ground.

## Output

```
# Signals — [what we looked for] — [date]
Pulled from: Copilot ranking | lead query | post engagers · Rows: N

| Person | Headline | Company | What they did | When | lead_id | Suggested next |
```

Finish with a single `pastel_show_leads` call using the same ids in the same order, then pass the lead cards to `icp-filter`.
