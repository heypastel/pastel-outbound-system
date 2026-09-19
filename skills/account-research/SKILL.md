---
name: account-research
description: Researcher — finds the hook for each qualified lead (the reason to talk to this person now) from Pastel lead details, their posts, and first-hand public sources. Use to research a company or person, after icp-filter, before writing copy.
---

# Account research — Researcher

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md). Pastel calls: [`../outbound-os/references/pastel-mcp.md`](../outbound-os/references/pastel-mcp.md).

The deliverable is a **hook**: one sentence connecting something true about this person to something we fix. One hook per lead — pick the strongest and let the rest go.

## Steps

1. Work only on leads marked _in_.
2. **Pastel:** `pastel_get_details` for profile, company, and captured activity; `pastel_query_posts` by name or company for posts they wrote or joined.
3. **The company, first-hand:** their website, LinkedIn page, blog, press page, filings. Note what they sell, to whom, roughly how big, and anything that happened in the last quarter.
4. **The person:** scope of the role, tenure, what they seem to be accountable for, and any public statement of a problem.
5. **Translate:** describe the problem the way they would, in their vocabulary.
6. **Specificity check:** swap in a competitor's name — if the hook still works, it is too generic. Research further or mark it _light_.
7. **Watch-outs:** existing customer, a fresh raise that's drawing a crowd of sellers, a purchasing-only role, a language mismatch.

A _light_ hook is acceptable: it leads to a shorter, plainer message. The writing belongs to `linkedin-copy`, which receives the hook only.

## Output per lead

```
lead_id:
who:            # one line on the person and company
moment:         # dated event, or "none found"
hook:           # one sentence
usable_proof:   # from icp-context.md only
avoid:          # topics to steer clear of
strength: strong | fair | light
sources:        # links
missing:        # [missing: …]
```
