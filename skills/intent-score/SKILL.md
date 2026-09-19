---
name: intent-score
description: Scorer — gives each lead a 0-100 priority built from signal, fit, reach, and hook, alongside Pastel's Copilot ranking, and sets who gets contacted now. Use for "score / rank this list", before copy or any send, or to choose who gets a first message.
---

# Intent score — Scorer

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md). Pastel calls: [`../outbound-os/references/pastel-mcp.md`](../outbound-os/references/pastel-mcp.md).

The question is "should we reach out **this week**?" — a great-fit account with no recent activity waits.

## Rubric

| Part | Max | What earns points |
|---|---|---|
| Signal | 40 | Strength on the `find-signals` ladder × recency |
| Fit | 30 | Company and seat inside the core segment |
| Reach | 15 | 1st-degree connection, or has interacted with us or our posts |
| Hook | 15 | `account-research` strength: strong 15 · fair 9 · light 4 |

| Total | Action |
|---|---|
| 75–100 | Contact this week |
| 60–74 | Warm up with `post-engagement`, then contact |
| 40–59 | Watch — revisit when a new signal lands |
| 0–39 | Skip |

## Steps

1. Take leads that are _in_ and researched.
2. For leads from `pastel_recommend_best_leads`, read `evidence`: `activity_intent_score` and `freshness_score` inform Signal, `lead_quality_score` informs Fit (all 0–1). `priority_score` is a ranking value on Pastel's own scale (often above 1000) — show it as "Copilot #n" next to your total, never as the total.
3. Show all four parts for every lead.
4. Sort descending; the contact-now threshold is 75 unless `icp-context.md` sets another.
5. Check `pastel_list_sequence_runs(lead_id=…)` for anyone already in a run or already in conversation, and move them out of the new-outreach list.

Scores reflect the lead, not the draft. Claims about what converts belong to `pipeline-report`.

## Output

```
# Priority list — [date]
Threshold: [n] · Inputs: rubric + Copilot where available

| # | Person | Company | Total | Signal/40 | Fit/30 | Reach/15 | Hook/15 | Copilot | Action |
```

Contact-this-week → `linkedin-copy`. Warm-up → `post-engagement`. Watch → stays in Pastel untouched.
