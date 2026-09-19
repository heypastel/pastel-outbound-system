---
name: target-accounts
description: Strategist — decides which market to go after and makes Pastel watch it, by proposing ICP definitions and lead agents. Use for "who should we go after", a new outbound push, a brief that is only a website, when find-signals comes back empty, or when pipeline-report says targeting is off.
---

# Target accounts — Strategist

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md). Pastel calls: [`../outbound-os/references/pastel-mcp.md`](../outbound-os/references/pastel-mcp.md).

Pastel only surfaces people its agents are told to watch. This skill is where that instruction gets written: which buyers, which moments, which sources.

## Steps

1. **Collect.** `icp-context.md`, `pastel_get_workspace_context`, `pastel_list_icp_definitions`, `pastel_list_agents(include_stats=true)`, and `pastel_aggregate_leads` by `job_title` and by `industry`. Include the latest `pipeline-report` if one exists.
2. **One-line offer**, in the words a buyer would use.
3. **Three roles:** who signs, who uses it, who pushes for it internally.
4. **Draw the line:** core segment, adjacent segment, no-go. Anything unclear sits outside until evidence moves it in.
5. **Choose up to three buying moments** that carry budget and urgency — e.g. reacting to a competitor's content, writing about the pain we remove, opening roles in the team we equip, stepping into a new seat. Generic likes are weak evidence.
6. **List the look-alikes to exclude:** service firms reselling to the real buyer, job seekers, competitors, segments we can't deliver for.
7. **Audit Pastel against it:** which agents already watch these moments, which yield leads, which drift outside the line.
8. **Draft the Pastel changes** — `create_icp_definition`, `update_icp_definition`, `create_agent`, `update_agent` — each with exact params and a one-line reason. After sign-off, request them and verify with `pastel_list_agents`.

## Output

```
# Market plan — [date]
Offer:
Roles: signs · uses · champions
Core / adjacent / no-go:
Buying moments we watch:
Moments we deliberately ignore:
Pastel changes (action · params · reason):
First batch: size · personas · countries · moment
Unknowns:
```

A plan built from a URL alone is marked _inferred_ and confirmed with the user before Pastel is touched.
