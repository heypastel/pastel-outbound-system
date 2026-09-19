# Pastel tools

Server: `https://mcp.heypastel.com/mcp` (OAuth; the host handles auth). The server's live tool names win; this page maps them to jobs. `pastel_list_capabilities` is the live contract — when this file and that response disagree, the response wins.

## Session start

| Tool | Use |
|---|---|
| `pastel_list_capabilities` | Granted scopes, available actions and their `params_schema`, known limitations. Once per session. |
| `pastel_get_workspace` / `pastel_get_workspace_context` | Workspace summary; ICP, positioning, keywords, competitors, market |
| `pastel_list_connected_accounts` | LinkedIn accounts and whether outreach can be sent right now |
| `pastel_get_crawl_status` | Crawl runs in progress. An empty `active` list means nothing is running now, not that agents are broken |

## Targeting

| Tool | Use |
|---|---|
| `pastel_list_icp_definitions` | ICP definitions used by agents, leads, and Copilot matching |
| `pastel_list_agents` | Lead agents: ICP filters, tracked actions, sources. `include_stats=true` shows which produce |
| `pastel_get_lead_facets` | Valid filter values and counts (titles, countries, industries, company types) |

## Leads

| Tool | Use |
|---|---|
| `pastel_recommend_best_leads` | Top / best / priority leads, ranked by Copilot scoring. Each item's `evidence` holds the signal (`primary_event_type`, `primary_event_at`) and 0–1 sub-scores; `priority_score` is a ranking value, not 0–100 |
| `pastel_query_leads` | Filtered lead search and paging (`countries`, `job_titles`, `industries`, `icp_definition_id`, `agent_id`, `created_since`, `status`) |
| `pastel_leads_for_post` | Who reacted to or commented on one post. `no_leads_yet: true` is an answer, not an error |
| `pastel_get_details` | Up to 5 leads or posts: profile, company, ICP match reasons, activity signals |
| `pastel_aggregate_leads` | Counts grouped by `country`, `company_size`, `action`, `job_title`, `industry`, `company_type` |
| `pastel_get_result_set_page` | Next page of a large result set |

## Posts

| Tool | Use |
|---|---|
| `pastel_recommend_best_posts` | Posts most worth engaging with now |
| `pastel_query_posts` / `pastel_aggregate_posts` | Search, count by status / network / intent tag |
| `pastel_draft_reply` | Server-side comment draft for a post (not saved) |
| `pastel_get_reply_prompt` | Pastel's reply prompt, to draft with your own model |

## Inbox and sequences

| Tool | Use |
|---|---|
| `pastel_list_conversations` | LinkedIn inbox from Pastel's cache (`unread_only`, `search`) |
| `pastel_get_conversation` | One thread's messages |
| `pastel_list_sequence_actions` | Valid `action_id` / `condition_id` values. Call before composing any sequence |
| `pastel_list_sequence_runs` | Runs; `status="needs_attention"` finds stalled ones |
| `pastel_get_sequence_run` | One run's steps, status, and errors |

## Reporting

| Tool | Use |
|---|---|
| `pastel_get_workspace_stats` | Inbox, lead, and intent summary for a range |
| `pastel_get_performance` | Daily activity series: `7d`, `30d`, `90d`, `365d` |
| `pastel_list_action_records` / `pastel_get_action_record` | Audit of actions this user or token requested |
| `pastel_list_notifications` | Pastel notifications |

## Display

When the host renders Pastel widgets, finish a lead or post answer with **one** `pastel_show_leads` / `pastel_show_posts` call carrying the final curated ids in display order (max 50). The widget then matches your written table.

## Writes — `pastel_request_action`

Every mutation goes through one tool: `pastel_request_action(kind, params, title, description)`. The workspace policy decides the path: execute, return a short-lived `confirmation_token` that you pass back with `client_confirmed=true` once the user approved, or refuse with a disabled-action error. Send an `idempotency_key` on anything that contacts a person, so a retry never double-sends.

| `kind` | Params (see `params_schema` in capabilities for the full set) | Scope |
|---|---|---|
| `mark_lead_status` | `lead_ids`, `status`: `NEW` / `NOT_INTERESTED` / `PROCESSED` | `leads:write` |
| `mark_post_status` | `post_ids`, `status`: `PASS` / `REPLIED` / `SAVED`, `pass_reason` | `posts:write` |
| `save_reply` | `post_id`, `content` — saves a draft in Pastel, sends nothing | `posts:write` |
| `create_icp_definition` / `update_icp_definition` | `definition` (with `name`) / `definition_id`, `changes` | `icp:write` |
| `create_agent` / `update_agent` | `name`, `icp`, `tracked_actions`, `sources_config`, `schedule` / `agent_id`, `changes` | `agents:write` |
| `comment_on_post` / `react_to_post` / `react_to_comment` | `post_id` or `post_url`, `content` / `reaction` | `engage:write` |
| `visit_profile` / `send_invitation` / `send_message` | `lead_id`; `note` (≤300 chars) / `content` | `engage:write` |
| `push_to_lemlist` | `lead_id`, `campaign_id` or `campaign_name` — the email channel | `engage:write` |
| `create_sequence` | `lead_id` or `post_id`, ordered `steps` (`action_id`, `body`, `delay_days`, `condition_id`, branch fields) | `sequences:write`, `engage:write` |
| `pause_sequence` / `resume_sequence` / `resolve_sequence_step` | `run_id` (+ `step_id`, `resolution`) | `sequences:write` |
| `send_chat_message` | `chat_id`, `content` — reply in an existing thread | `messages:write` |
| `update_conversation` | `chat_id`, `conversation_action` (`mark_read`, `archive`, `star`, …) | `messages:write` |

Engagement and sequence steps run through Pastel's sequence engine: per-account pacing, daily caps, and working-hours gating apply, and the result is a queued run. Pass `queue_for_tomorrow=true` when today's cap is spent.

## Gaps to state plainly

- **No live search or crawl.** Discovery runs on the agents' own schedule.
- **No email finder or mailbox.** `find_email` and `send_email` are unavailable; email outreach is `push_to_lemlist`.
- **Missing scope.** When capabilities shows an action with `available: false`, name its `missing_scopes` and ask the user to reconnect Pastel and grant them. Continue with read-and-draft work meanwhile. A read tool can fail the same way (`scope_missing`, e.g. `sequences:read`): skip that section and list it under **Open questions**.

## Call policy

1. Batch reads: one `pastel_query_leads` with filters, then `pastel_get_details` in groups of 5.
2. After a write, confirm with the matching read (`pastel_get_action_record`, `pastel_get_sequence_run`, the lead) and report ids.
3. After an authentication error, make no more Pastel requests this run and ask the user to reconnect Pastel.
