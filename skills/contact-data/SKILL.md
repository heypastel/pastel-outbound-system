---
name: contact-data
description: Reachability Checker — confirms each lead can be contacted (LinkedIn profile resolvable, email route through Lemlist) and completes missing fields from Pastel and public sources, never by guessing. Use for "find their email", incomplete lead fields, or right before launching a sequence.
---

# Contact data — Reachability Checker

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md). Pastel calls: [`../outbound-os/references/pastel-mcp.md`](../outbound-os/references/pastel-mcp.md).

The system sells on LinkedIn first. A usable profile URL makes a lead contactable; an email address is a bonus channel.

## Steps

1. For every _in_ lead, note what's absent: profile URL, company domain, current title, email.
2. **Pastel:** `pastel_get_details` shows what the workspace already stores. Without a resolvable profile, Pastel can't invite or message the person — tag them `no-profile`.
3. **Public pages** for domain and title (company site, LinkedIn company page), with the link as source.
4. **Email:** Pastel has no address lookup. If `icp-context.md` allows email, tag the lead `via-lemlist`; `launch-sequence` pushes it to Lemlist, which does its own lookup. Otherwise the field is `[missing: email]`. Addresses assembled from a naming pattern are guesses, and a guessed address that bounces hurts the sending domain.
5. Merge duplicate people into one row.

## Output

```
# Reachability — [date]
Checked: N · Ready on LinkedIn: n · Email via Lemlist: n · No profile: n

| Person | Company | Profile | Domain | Email | Source | Tag |
```

Tags: `ready` · `via-lemlist` · `no-profile` · `incomplete`. `ready` leads continue to `intent-score`.
