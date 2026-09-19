---
name: post-engagement
description: Social Seller — warms prospects before any DM by commenting on and reacting to their LinkedIn posts through Pastel, choosing the posts most worth it. Use for "which posts should I comment on", warming a list, leads scored for warm-up, or working the Pastel posts inbox.
---

# Post engagement — Social Seller

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md). Pastel calls: [`../outbound-os/references/pastel-mcp.md`](../outbound-os/references/pastel-mcp.md).

A thoughtful comment on someone's post, a few days before the invitation, means they already know your name when it arrives. The comment serves their thread; selling waits for the DM.

## Steps

1. **Choose posts.** `pastel_recommend_best_posts` (status `NEW`), or for specific leads, `pastel_query_posts` by author or company. Open each with `pastel_get_details`.
2. **Skip** hiring announcements, personal or sensitive news, and anything older than a week.
3. **Draft.** `pastel_draft_reply(post_id)`, or `pastel_get_reply_prompt` to write it yourself within Pastel's reply guidance. Then `de-slop`.
4. **What a strong comment does:** brings one concrete data point, example, or respectful disagreement from our field, or asks the author something they'd enjoy answering. One to three sentences, without our product, links, or invitations to DM.
5. **Request, after sign-off:** `comment_on_post` (or `save_reply` to park it as a Pastel draft), plus `react_to_post` when it fits. Then `mark_post_status` → `REPLIED` on engaged posts and `PASS` with a `pass_reason` on skipped ones.
6. **Pass on:** people who reply or react back move to `launch-sequence` three to five days later, with "we commented on [post], [date]" recorded as their signal.

## Output

```
# Comment plan — [date]

### [Author] · [Company] · posted [date]
Post opens with: "…"
Why engage: …
Comment:
> …
Request: comment_on_post + react_to_post | save_reply | PASS — reason
```

Close with one `pastel_show_posts` call listing the chosen ids.
