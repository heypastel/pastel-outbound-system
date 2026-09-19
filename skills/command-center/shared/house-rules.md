# House rules

Every skill in this system follows these. They exist so that anything the system hands you can be trusted without re-checking it.

## Start of every session

1. **Read the brief.** `outbound-brief.md` lives in the project root or `.codex/`. It says what we sell, to whom, who is off-limits, what proof we may cite, how we sound, and whether autopilot is on. Missing → keep going, say the output is generic, and suggest the `outbound-brief` skill.
2. **Read your permissions.** With Pastel connected, call `pastel_list_capabilities` once. It lists the granted scopes and which actions are live today. How to call Pastel: [`pastel-tools.md`](pastel-tools.md).

## Truth

- **Source or silence.** People, companies, titles, signals, emails, and quotes come from a Pastel result or a page you can link. When something can't be sourced, write `[missing: what]` and carry on without it.
- **Pastel remembers what its agents found; it does not search on request.** An empty result has three possible causes. Run the empty-result check below before saying anything.
- **Pastel runs actions on its own clock.** A successful request means Pastel scheduled it within the account's pacing. Report it as _scheduled_ until `pastel_get_sequence_run` shows the step completed.

## Empty-result check

1. `pastel_aggregate_leads()` with no filters: is the workspace empty, or only this query?
2. **Leads exist** → the filters are too tight. Show what Pastel does have nearby with `pastel_get_lead_facets` (the closest titles, countries, industries, with counts) and let the user pick, or point a Pastel agent somewhere new with `market-map`.
3. **Workspace empty** → `pastel_get_crawl_status` and `pastel_list_agents`:
   - a crawl is running (`active` not empty) → "Pastel's agents are doing their first run on your market. It usually takes 30–45 minutes; outreach can start once it's done." Meanwhile offer `outbound-brief`, `market-map`, `post-studio`, or research on companies the user names. Never fill the gap with made-up leads.
   - no crawl, no agents → Pastel has nothing to watch yet: finish Pastel onboarding (website, LinkedIn), or create a first agent with `market-map`.
   - no crawl, agents exist → they ran and found nothing: show their filters and offer `market-map` to widen them.

## Approval

- **Default: every change waits for a yes.** Lead or post status, ICP definitions, agents, comments, reactions, invitations, messages, sequences — show exactly what will happen, then wait.
- **Autopilot** needs two things: `Autopilot: on` (in `outbound-brief.md`, or said by the user during the session) and a minimum priority. It never touches anyone below that priority or on the off-limits list, and it logs every request with its action id.
- `bypass_daily_limit` stays `false` unless the user asks for it on that exact action.

## Output

Deliver the finished thing — the table, the ranking, the draft, the scheduled run. Lists are tables. Every report closes with **Open questions**. Reports worth keeping are also saved as `outbound-[topic]-[YYYY-MM-DD].md` if files can be saved.

## Lead card

Leads move between skills as lead cards, so nothing gets researched twice. Unknown fields hold `[missing]`.

```
lead_id:        # Pastel id
who:            # name · headline · company
profile_url:
email:
caught:         # the event: what they did, where, when
verdict:        # yes | maybe | no — reason
off_limits:     # the rule it hit, if any
why_now:        # one sentence
priority:       # 0-100 · parts · Copilot rank if any
draft:          # current message
run_id:         # Pastel sequence run once scheduled
thread:         # none | hot | curious | timing | pushback | stop
next:           # the next action
owner:          # the skill that acts next
```
