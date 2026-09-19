---
name: icp-context-setup
description: Creates or refreshes icp-context.md — offer, buyers, no-go list, proof, voice, autopilot settings — from the Pastel workspace plus a short interview. Use on first run, when icp-context.md is missing, or when the user says their positioning, ICP, or sending rules changed.
---

# ICP context setup

House rules: [`../outbound-os/references/rules.md`](../outbound-os/references/rules.md). Pastel calls: [`../outbound-os/references/pastel-mcp.md`](../outbound-os/references/pastel-mcp.md).

Every outbound skill leans on this file, so each line is either backed by a source or marked `[missing]`.

## Steps

1. **Harvest Pastel.** `pastel_get_workspace_context` (positioning, ICP, keywords, competitors, market), `pastel_list_icp_definitions`, `pastel_list_agents` (their tracked actions are the buying moments already watched), `pastel_list_connected_accounts` (the sender). Read the user's site if they share it.
2. **Pre-fill** [`../outbound-os/icp-context.template.md`](../outbound-os/icp-context.template.md). Tag each pre-filled line with where it came from, e.g. `<!-- pastel: icp_definitions -->`.
3. **Ask for the gaps** in a single message of six questions or fewer. Unless already known, always cover: nameable customers or results, the no-go list, the ask we want, autopilot on or off.
4. **Save `icp-context.md`** in the location the user prefers (project root by default), `[missing]` where still unknown.
5. **Point out conflicts** between Pastel's ICP definitions and the user's answers, and offer `target-accounts` to align Pastel.

Finished when the file exists, no line is blank (filled or `[missing]`), and autopilot is explicitly on or off.
