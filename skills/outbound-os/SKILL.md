---
name: outbound-os
description: Runs the full outbound motion on Pastel — targeting, signal-based lead finding, fit checks, research, scoring, LinkedIn copy, post engagement, sequences, inbox, follow-up, meeting qualification, pipeline reporting. Use when the user asks to run outbound end to end, "work the pipeline", or gives a multi-step sales task spanning several of those jobs. Also the home of the shared rules and Pastel tool map every outbound skill uses.
---

# Outbound OS

You orchestrate. Each job has its own skill; you decide the route, pass lead cards from one skill to the next, and own the moment of sign-off before anything reaches a prospect.

Load [`references/rules.md`](references/rules.md) now (evidence, review mode, lead card). Load [`references/pastel-mcp.md`](references/pastel-mcp.md) before your first Pastel call.

## Opening move

1. Warm-up from rules.md.
2. Snapshot the workspace in three lines: `pastel_list_connected_accounts` (can we send?), `pastel_get_workspace_stats` (volume this week), newest leads' dates (are the agents producing?).
3. When the user names a target in the request, it wins over `icp-context.md` for this run; say so in the snapshot.
4. Choose a route and post the tracker.

## Skill directory

| Need | Skill |
|---|---|
| Draft or update the brief | `icp-context-setup` |
| Decide the market; configure Pastel ICPs and agents | `target-accounts` |
| Pull people with fresh buying signals | `find-signals` |
| In / borderline / out per lead | `icp-filter` |
| The hook for each lead | `account-research` |
| Reachability and email route | `contact-data` |
| 0–100 priority | `intent-score` |
| Invitation note and messages | `linkedin-copy`, then `de-slop` |
| Comments and reactions on their posts | `post-engagement` |
| Queue sequences in Pastel | `launch-sequence` |
| Sort the LinkedIn inbox | `inbox-triage` |
| Nudges and stuck runs | `follow-up` |
| Call-worthy or not | `qualify-meeting` |
| Conversion by signal, agent, persona | `pipeline-report` |
| Morning plan | `daily-brief` |

## Routes

- **Cold start:** target-accounts → find-signals → icp-filter → account-research → contact-data → intent-score → linkedin-copy → de-slop → ✋ sign-off → launch-sequence.
- **Existing Pastel leads:** icp-filter → account-research (in only) → intent-score → linkedin-copy → de-slop → ✋.
- **Warm first:** find-signals → post-engagement → ✋ → launch-sequence a few days later, once they've seen your name.
- **Inbox:** inbox-triage, then hot → qualify-meeting; curious, later, away → follow-up; no → recorded, nothing sent.
- **Stuck:** follow-up on quiet threads and `needs_attention` runs, while pipeline-report looks for the cause.
- **Review:** pipeline-report, then target-accounts if the numbers point at targeting.

✋ **Sign-off** means: show the drafts and the exact Pastel requests you'd make, then stop until the user says yes. Autopilot skips it only within the limits in rules.md.

## Parallel work

With subagents available, split the wide stages and keep every Pastel request with yourself:

- Research: one subagent per lead, eight at a time at most; you consolidate the hooks.
- Copy: one subagent per group of leads sharing a hook (individual subagents only for five leads or fewer); you run `de-slop` across the combined output.
- Inbox: triage first, then pass each thread only to the skill that owns its label.

Brief each subagent with the skill to use, its lead cards, and the expected output. Without subagents, run the route step by step in the order written.

## Tracker

Post it when you start and when you finish.

```
# Outbound tracker — [date]
Pastel: on | off · Autopilot: on | off · Aim: [who, in one line]

| Step | Leads | Waiting for |
|---|---|---|
| Surfaced | | |
| Fit: in | | |
| Hook found | | |
| Priority ≥ threshold | | |
| Written | | |
| Needs your OK | | |
| Queued | | |
| Answered | | |
| Call-worthy | | |
| Booked | | |
```

Finish with three next moves and the skills that ran.

## Boundaries

- 50 new leads per run, unless the user picks the number.
- Sequences are relaunched only after `pipeline-report` explains the last result.
- If Pastel returns an error, halt Pastel requests, show the error, and keep researching and drafting.
