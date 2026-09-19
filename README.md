# GPT-6 Astra Outbound System

**Our complete outbound system, free. 17 skills covering almost every repetitive part of outbound.**

Built for **GPT-6 Astra** in Codex. Every skill runs on your live data through the **[Pastel](https://heypastel.com) MCP**: the leads Pastel's agents find from LinkedIn buying signals, your posts inbox, your LinkedIn conversations, and your sequences.

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

Plus a **14-person team** of Codex custom agents — Orchestrator, Strategist, Signal Scout, Fit Checker, Researcher, Reachability Checker, Scorer, Copywriter, Social Seller, Sequencer, Inbox Manager, Nurturer, Qualifier, Analyst — so research and writing run in parallel.

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

## Set it up in 3 steps

### 1. Create your Pastel workspace

[Create a Pastel account](https://heypastel.com) and start your 7-day free trial. Add your website and connect the LinkedIn profile that will do the outreach.

Pastel's agents then do a first run on your market, which takes **30–45 minutes**. Start here and install while it works — the system tells you if the first run is still going.

### 2. Install it in Codex

```bash
codex plugin marketplace add heypastel/pastel-outbound-system
codex plugin add pastel-outbound@pastel-outbound-system
```

The Pastel connection comes with the plugin: Codex asks you to sign in to Pastel the first time a skill needs it. The system checks your Pastel permissions at the start of every session and tells you if sending isn't enabled yet.

Optional — the 14 agents, for parallel research and writing:

```bash
git clone https://github.com/heypastel/pastel-outbound-system.git
mkdir -p ~/.codex/agents && cp pastel-outbound-system/agents/*.toml ~/.codex/agents/
```

### 3. Ask for your first results

No commands to learn — just ask Codex:

- *"Set up my ICP context."*
- *"Who showed buying signals this week? Pick the best 25 and write their messages."*
- *"Run my daily brief."* — every morning, five moves with drafts ready.

Without Pastel, the skills can still research and draft, but they have no leads, signals, inbox, or sending.

## Principles

- **Everything is sourced.** Every email, signal, and quote traces back to Pastel or a public page. Gaps are marked `[missing: x]`.
- **One job per skill.** Small, readable playbooks you can edit to fit your own motion.
- **Signals over lists.** A title match is not intent. Every lead carries the signal that put it there.
- **Just markdown.** No scripts to run; the only connection is the Pastel MCP.

Stuck somewhere? [Ping me on LinkedIn](https://www.linkedin.com/in/loupaudouy/), I answer everyone.

MIT licensed.
