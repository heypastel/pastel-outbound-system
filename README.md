<p align="center">
  <img src="assets/banner.png" alt="GPT-6 Astra Outbound System, for free — 20 skills, 12 agents, powered by Pastel" width="100%">
</p>

<p align="center">
  <b>20 skills that run the repetitive half of outbound, so you spend your time in the conversations.</b><br>
  Built for <b>GPT-6 Astra</b> in Codex · free and open source · powered by <a href="https://heypastel.com">Pastel</a>
</p>

<p align="center">
  <a href="#set-it-up-in-3-steps"><b>Set it up</b></a> ·
  <a href="#the-20-skills">The skills</a> ·
  <a href="#one-leads-journey">One lead's journey</a> ·
  <a href="#your-morning">Your morning</a>
</p>

---

Pastel watches LinkedIn for people who show buying intent: they ask their network for a tool, react to a competitor's launch, or post about the problem you solve. This system takes it from there. It checks they fit, finds the reason to reach out now, writes the message, warms them up on their own posts, launches the sequence when you say go, and sorts the replies.

You stay the one who decides. Every comment, invitation, and message waits for your yes.

## The 20 skills

| Stage | Skills |
|---|---|
| **Set up** | `outbound-brief` your one-page brief, filled from Pastel · `market-map` which market to work and what Pastel should watch · `command-center` runs the whole play · `morning-brief` today's five moves, drafted |
| **Catch intent** | `intent-radar` people who just did something that signals buying · `competitor-watch` who engages with your competitors, and what they complain about |
| **Qualify** | `fit-check` yes / maybe / no against your brief · `reach-check` can we reach them, and how · `why-now` the one reason to talk to them today · `buying-committee` who else matters at the account · `priority-rank` who gets today's LinkedIn slots |
| **Write** | `message-writer` invitation, opening message, variant B · `human-voice` makes every draft sound like you · `post-studio` LinkedIn posts that bring buyers to you |
| **Engage** | `social-warmup` comments on their posts before any DM · `campaign-launch` queues the Pastel sequence once you approve |
| **Convert** | `reply-desk` tags every reply and drafts the answer · `nudge` follow-ups worth reading · `call-ready` is this conversation ready for a call |
| **Learn** | `what-works` measures which signals and angles start real conversations |

You never call a skill by name: ask for what you want and Codex picks the right one.

## The team

In Codex, the skills are shared out between 12 agents that can work in parallel — one Detective per account, one Ghostwriter per industry:

**Chief of Staff** runs the play · **Cartographer** maps the market · **Radar** catches intent · **Gatekeeper** checks fit and reach · **Detective** finds why now and who else matters · **Ranker** sets priorities · **Ghostwriter** writes · **Storyteller** writes your posts · **Networker** warms people up · **Launcher** sends when you approve · **Concierge** handles replies · **Coach** tells you what works.

## One lead's journey

*An illustrative example.*

| When | What happens |
|---|---|
| **Mon 9:10** | Julia, Head of Growth at a 60-person SaaS, comments on a competitor's launch post. Pastel catches it. |
| **Mon 9:30** | Morning brief: `intent-radar` marks her 🟠, `fit-check` says yes, `why-now` notes her team is hiring two SDRs this month. |
| **Mon 9:31** | `priority-rank` gives her 64 — warm up first. `social-warmup` drafts a comment for her latest post. You approve it. |
| **Thu 9:30** | She liked your comment. `message-writer` drafts an invitation built on her hiring news. You say go. |
| **Thu 9:31** | `campaign-launch` queues visit → invitation → message once she accepts. |
| **Mon 14:02** | She replies: *"Timing's good actually, how does it work?"* `reply-desk` tags it hot; `call-ready` sees pain and power, and asks the one question about timing. |
| **Tue** | Call booked. `what-works` counts one more conversation for "competitor engagement". |

## Your morning

Ask *"Run my morning brief"* and get something like this *(illustrative example)*:

```text
Today — Tuesday
Sending: ok · New signals: 12 · Unread: 3 · Stuck: 0 · Posts: 5

1. Answer Sarah (VP Sales, 40-person SaaS) — she asked how pricing works
   > Happy to walk you through it. Most teams your size start with…
   Reply "go 1" to approve

2. Comment on Mark's post about SDR ramp time — 3 of your leads engaged with it
   > The ramp number that surprised us most was…
   Reply "go 2" to approve

3. First message to Julia (Head of Growth) — commented on a competitor's launch yesterday
   > Saw your take on their launch. Curious how you're handling…
   Reply "go 3" to approve
…
```

Five moves, drafted and ranked. Fifteen minutes of approving instead of two hours of prospecting.

## Set it up in 3 steps

### 1. Create your Pastel workspace

[Create a Pastel account](https://heypastel.com) and start your 7-day free trial. Add your website and connect the LinkedIn profile that will do the outreach.

Pastel's agents then do a first run on your market, which takes **30–45 minutes**. The system tells you if it's still running.

### 2. Install it in Codex

```bash
codex plugin marketplace add heypastel/pastel-outbound-system
codex plugin add pastel-outbound@pastel-outbound-system
```

The Pastel connection comes with the plugin. Codex asks you to sign in to Pastel the first time a skill needs it, and tells you if sending isn't enabled on your account yet.

<details>
<summary>Optional: add the 12 agents so research and writing run in parallel</summary>

```bash
git clone https://github.com/heypastel/pastel-outbound-system.git
mkdir -p ~/.codex/agents && cp pastel-outbound-system/team/*.toml ~/.codex/agents/
```

</details>

### 3. Ask for your first results

- *"Set up my outbound brief."*
- *"Who showed buying signals this week? Pick the best 20 and write their messages."*
- *"Run my morning brief."*

## How it behaves

- **You approve, it executes.** Drafts first, always. Autopilot exists, but only when you switch it on, and only above a minimum priority you choose.
- **Proof on every lead.** Each lead carries what they did, where, and when. Nothing is invented; unknowns are marked `[missing]`.
- **Yours to change.** Every skill is a readable file. Adjust the tone, the scoring, or the follow-up rhythm to match how you sell.

---

<p align="center">
  Stuck somewhere? <a href="https://www.linkedin.com/in/loupaudouy/">Ping me on LinkedIn</a>, I answer everyone.<br>
  <sub>MIT licensed · Built by <a href="https://heypastel.com">Pastel</a></sub>
</p>
