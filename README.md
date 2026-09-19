<p align="center">
  <img src="assets/banner.png" alt="GPT-6 Astra Outbound System, for free — 17 skills, 14 agents, powered by Pastel" width="100%">
</p>

<p align="center">
  <b>We're giving away our complete outbound system.</b><br>
  17 skills covering almost every repetitive part of outbound, built for <b>GPT-6 Astra</b> in Codex.
</p>

<p align="center">
  <a href="#set-it-up-in-3-steps"><b>Set it up in 3 steps</b></a> ·
  <a href="#meet-your-outbound-team">Meet the team</a> ·
  <a href="#what-a-morning-looks-like">See a morning</a> ·
  <a href="https://heypastel.com">Pastel</a>
</p>

---

Your AI outbound team finds the people who just showed buying intent on LinkedIn, researches them, writes messages that don't sound like AI, runs the sequences, and sorts the replies. It prepares the work; you approve it over coffee.

It runs on your live data through the **[Pastel](https://heypastel.com) MCP**: the leads Pastel's agents find from buying signals, your LinkedIn inbox, and your sequences.

## Meet your outbound team

14 specialists, 17 skills. Each one has a single job.

| | Teammate | Their job | Skills |
|---|---|---|---|
| 🧭 | **Orchestrator** | Runs the whole motion and hands you the morning plan | `outbound-os` `daily-brief` |
| 🎯 | **Strategist** | Decides who to go after, and sets Pastel to watch them | `target-accounts` `icp-context-setup` |
| 📡 | **Signal Scout** | Spots people who just showed buying intent, with proof | `find-signals` |
| ✅ | **Fit Checker** | Keeps only the people who match your ideal customer | `icp-filter` |
| 🔍 | **Researcher** | Finds the one reason to talk to each person now | `account-research` |
| 📇 | **Reachability Checker** | Makes sure every lead can be contacted, never guesses emails | `contact-data` |
| 📊 | **Scorer** | Ranks everyone by how likely they are to buy this week | `intent-score` |
| ✍️ | **Copywriter** | Writes the invitation and first message, then strips the AI tone | `linkedin-copy` `de-slop` |
| 💬 | **Social Seller** | Comments on their posts so they know your name before the DM | `post-engagement` |
| 🚀 | **Sequencer** | Queues the visit, invitation, and message once you approve | `launch-sequence` |
| 📥 | **Inbox Manager** | Reads every reply and drafts the answer | `inbox-triage` |
| 🔁 | **Nurturer** | Follows up with something useful, three touches max | `follow-up` |
| 🤝 | **Qualifier** | Checks a hot lead is worth a call before it hits your calendar | `qualify-meeting` |
| 📈 | **Analyst** | Tells you which signals and messages actually turn into conversations | `pipeline-report` |

## How they work together

1. 📡 The **Signal Scout** spots someone who just commented on a competitor's post.
2. ✅ The **Fit Checker** confirms they match your ideal customer.
3. 🔍 The **Researcher** finds why they'd care right now.
4. 📊 The **Scorer** ranks them against everyone else this week.
5. ✍️ The **Copywriter** drafts an invitation that sounds like you.
6. ✋ **You approve** — nothing reaches a prospect without your yes.
7. 🚀 The **Sequencer** sends it through Pastel, within LinkedIn's daily limits.
8. 📥 The **Inbox Manager** catches the reply, and the 🤝 **Qualifier** turns it into a call.

Not ready to buy yet? The 💬 **Social Seller** warms them up on their posts first. And every week, the 📈 **Analyst** tells the 🎯 **Strategist** what to aim at next.

## What a morning looks like

Ask *"Run my daily brief"* and you get something like this *(illustrative example)*:

```text
Today — Tuesday
Sending: ok · New signals: 12 · Unread replies: 3 · Stuck: 0

1. Answer Sarah (VP Sales, 40-person SaaS) — she asked how pricing works
   > Happy to walk you through it. Most teams your size start with…
   Reply "go 1" to send

2. Comment on Mark's post about SDR ramp time — 3 of your leads engaged with it
   > The ramp number that surprised us most was…
   Reply "go 2" to post

3. First message to Julia (Head of Growth) — commented on a competitor's launch yesterday
   > Saw your take on their launch. Curious how you're handling…
   Reply "go 3" to queue

…
```

Five moves, drafted and ranked. You spend fifteen minutes approving instead of two hours prospecting.

## Set it up in 3 steps

### 1. Create your Pastel workspace

[Create a Pastel account](https://heypastel.com) and start your 7-day free trial. Add your website and connect the LinkedIn profile that will do the outreach.

Pastel's agents then do a first run on your market, which takes **30–45 minutes**. The system tells you if the first run is still going.

### 2. Install it in Codex

```bash
codex plugin marketplace add heypastel/pastel-outbound-system
codex plugin add pastel-outbound@pastel-outbound-system
```

The Pastel connection comes with the plugin: Codex asks you to sign in to Pastel the first time a skill needs it, and tells you if sending isn't enabled on your account yet.

<details>
<summary>Optional: install the 14 teammates as Codex agents, so research and writing run in parallel</summary>

```bash
git clone https://github.com/heypastel/pastel-outbound-system.git
mkdir -p ~/.codex/agents && cp pastel-outbound-system/agents/*.toml ~/.codex/agents/
```

</details>

### 3. Ask for your first results

No commands to learn — just ask Codex:

- *"Set up my ICP context."*
- *"Who showed buying signals this week? Pick the best 25 and write their messages."*
- *"Run my daily brief."*

## Principles

- **Nothing goes out without your yes.** Every comment, invitation, and message is drafted for review first. Autopilot exists, but only if you turn it on, with a minimum score.
- **Every lead comes with proof.** A job title is not intent. Each lead carries the signal that surfaced it — what they did, where, and when. Nothing is invented.
- **Plain files you can read and edit.** Just markdown, no scripts. Change the tone, the scoring, or the follow-up rhythm to fit how you sell.

<details>
<summary>All 17 skills, one by one</summary>

| # | Skill | Does |
|---|---|---|
| 1 | `outbound-os` | Orchestrates everything: picks the route, passes leads between skills, owns sign-off |
| 2 | `icp-context-setup` | Writes your ICP brief from your Pastel workspace + 6 questions |
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

</details>

---

<p align="center">
  Stuck somewhere? <a href="https://www.linkedin.com/in/loupaudouy/">Ping me on LinkedIn</a>, I answer everyone.<br>
  <sub>MIT licensed · Built by <a href="https://heypastel.com">Pastel</a></sub>
</p>
