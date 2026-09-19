---
name: daily-brief
description: Morning outbound plan — what Pastel collected overnight, who answered, what's stuck, and the five moves worth making today with drafts ready. Use for "morning brief", "what should I do today", or a scheduled daily run.
---

# Daily brief

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md). Pastel calls: [`../outbound-os/references/pastel-mcp.md`](../outbound-os/references/pastel-mcp.md).

A fifteen-minute outbound routine, prepared in advance. The brief only reads and drafts; each move waits for a yes.

## Steps

1. **Health:** `pastel_list_connected_accounts` — can we send today? (`pastel_get_crawl_status` shows only crawls running right now; the newest lead dates in step 4 tell you whether agents are producing.)
2. **Inbox:** `pastel_list_conversations(unread_only=true)`, tagged the `inbox-triage` way; hot conversations lead the brief.
3. **Stuck:** `pastel_list_sequence_runs(status="needs_attention")`.
4. **New signals:** `pastel_recommend_best_leads(created_since=<yesterday>, limit=10)`, checked quickly against `icp-context.md`.
5. **Posts:** `pastel_recommend_best_posts(limit=5)`.
6. **Choose five moves** by this priority: answer hot → unblock stuck runs → comment on a strong post → first message to a new high-score lead → scheduled follow-up. Draft each with the owning skill, then `de-slop`.

## Output

```
# Today — [date]
Sending: ok | blocked · New signals: n (newest [date]) · Unread: n · Stuck: n · Posts: n

1. [Move] — [Person, Company] — [reason]
   > draft
   Reply "go 1" to approve
…

Waiting on you:
Unknowns:
```

"go N" runs that move through `launch-sequence`, `follow-up`, or `post-engagement`.
