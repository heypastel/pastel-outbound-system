# Pastel Outbound System

**Our complete outbound system, free. 17 skills covering almost every repetitive part of outbound.**

Built for **GPT-6 Astra** in Codex and ChatGPT. It is plain markdown, so it also runs in Claude Code, Cursor, or any agent that reads skills — whichever model you use.

Every skill runs on your live data through the **[Pastel](https://heypastel.com) MCP**: the leads Pastel's agents find from LinkedIn buying signals, your posts inbox, your LinkedIn conversations, and your sequences.

## The 17 skills

| # | Skill | Does |
|---|---|---|
| 1 | `outbound-os` | Orchestrates everything: picks the route, passes leads between skills, owns sign-off |
| 2 | `icp-context-setup` | Writes your `icp-context.md` from your Pastel workspace + 6 questions |
| 3 | `target-accounts` | Decides who to target and sets up the Pastel agents that hunt them |
| 4 | `find-signals` | Pulls leads showing real buying intent, each with the signal and date |
| 5 | `icp-filter` | In / borderline / out, with the reason for each |
| 6 | `account-research` | One hook per lead: the reason to talk to them now |
| 7 | `contact-data` | Checks every lead is reachable; email goes through Lemlist, never guessed |
| 8 | `intent-score` | 0–100 priority from signal, fit, reach, and hook |
| 9 | `linkedin-copy` | Invitation note + first message + an alternate |
| 10 | `de-slop` | Removes AI tells from everything before you see it |
| 11 | `post-engagement` | Warms prospects by commenting on their posts before the DM |
| 12 | `launch-sequence` | Visit → invite → DM-on-accept sequences, queued in Pastel |
| 13 | `inbox-triage` | Tags every conversation, quotes the prospect, drafts the answer |
| 14 | `follow-up` | Three touches max, each one worth reading |
| 15 | `qualify-meeting` | Pain, power, priority, profile — before it takes a calendar slot |
| 16 | `pipeline-report` | Which buyer types, signals, and hooks turn into conversations |
| 17 | `daily-brief` | Every morning: what came in, and the five actions worth doing today, drafted |

Plus a **14-person team** of agents — Orchestrator, Strategist, Signal Scout, Fit Checker, Researcher, Reachability Checker, Scorer, Copywriter, Social Seller, Sequencer, Inbox Manager, Nurturer, Qualifier, Analyst — so hosts with subagents can research and write in parallel.

## How the work flows

```
target-accounts ─ who, and which Pastel agents hunt them
   ↓
find-signals → icp-filter → account-research → contact-data → intent-score
   ↓                                                              ↓ 60–74: warm up first
linkedin-copy → de-slop                                    post-engagement (warm up)
   ↓
✋ you approve
   ↓
launch-sequence → inbox-triage → follow-up / qualify-meeting
   ↓
pipeline-report → back to target-accounts
```

**Nothing reaches a prospect without your yes.** Review mode is the default. Autopilot is opt-in with a minimum score, and Pastel's pacing and daily caps still apply.

## Install

### Codex (GPT-6 Astra)

```bash
codex plugin marketplace add heypastel/pastel-outbound-system
```

Then install **Pastel Outbound System** from the plugin list and approve the Pastel connection when prompted.

Optional — the 14 agents for parallel work:

```bash
mkdir -p ~/.codex/agents && cp codex-agents/*.toml ~/.codex/agents/
```

### ChatGPT

This is a standard OpenAI plugin, and ChatGPT Work mode runs those too. Or add `https://mcp.heypastel.com/mcp` as a connector and add the `skills/` folders.

### Claude Code

```
/plugin marketplace add heypastel/pastel-outbound-system
/plugin install pastel-outbound@pastel-outbound-system
```

### Anything else (Cursor, other agents)

Drop the `skills/` folder where your agent loads skills from, and add `https://mcp.heypastel.com/mcp` as an MCP server.

## Connect Pastel

1. Create a [Pastel](https://heypastel.com) workspace and add your website — Pastel learns your ICP from it.
2. Link the LinkedIn profile that will do the outreach.
3. Approve the MCP connection when your agent asks. To let the system **send** (not just draft), grant the `engage`, `sequences`, and `messages` scopes. The system checks your scopes at the start of every session and tells you what's missing.

Without Pastel, the skills still research and draft, but they have no leads, signals, inbox, or sending.

## First five minutes

1. *"Set up my ICP context."* → runs `icp-context-setup`.
2. *"Show me what Pastel found this week — leads, posts, replies. Don't change anything."*
3. *"Who showed buying signals this week? Pick the best 25, write their messages, and hold them for my review."*
4. Every morning: *"Run my daily brief."* If your agent can schedule tasks, schedule it for weekdays at 8am.

## Principles

- **Everything is sourced.** Every email, signal, and quote traces back to Pastel or a public page. Gaps are marked `[missing: x]`.
- **One job per skill.** Small, readable playbooks you can edit to fit your own motion.
- **Signals over lists.** A title match is not intent. Every lead carries the signal that put it there.
- **Just markdown.** No scripts to run; the only connection is the Pastel MCP.

MIT licensed.
