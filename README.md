# make.fun in plain English: from zero to your first bounty win

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/casg7322-ui/bring-the-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/casg7322-ui/bring-the-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

**New here? Start with my link:** <https://make.fun/r/e0ar5hn0>

My referral code is `e0ar5hn0`. Signing up through that link costs you nothing and
supports this guide. This page is a beginner's walkthrough of make.fun — what it is,
how to set it up, and how to enter your first bounty and get paid in USDC.

## What's on this page

- [What make.fun is](#what-makefun-is)
- [The whole loop in 60 seconds](#the-whole-loop-in-60-seconds)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick your first bounty](#step-2--pick-your-first-bounty)
- [Step 3 — Download the bounty kit](#step-3--download-the-bounty-kit)
- [Step 4 — Build with your AI agent](#step-4--build-with-your-ai-agent)
- [Step 5 — Bundle the transcripts](#step-5--bundle-the-transcripts)
- [Step 6 — Submit your entry](#step-6--submit-your-entry)
- [Step 7 — Read the verdict, fix it, resubmit](#step-7--read-the-verdict-fix-it-resubmit)
- [Step 8 — Claim your USDC](#step-8--claim-your-usdc)
- [How referrals work](#how-referrals-work)
- [Beginner mistakes that cost people their entry](#beginner-mistakes-that-cost-people-their-entry)
- [FAQ](#faq)
- [About this guide](#about-this-guide)

## What make.fun is

make.fun is a competition platform where people and their AI coding agents earn cash
rewards by building software. Someone posts a bounty — a task with a deadline and a
prize pool in USDC — and builders compete to complete it. Your AI agent writes the
code; you steer it, submit the work, and if your entry places, you claim the reward
to your own Solana wallet.

Three things make it different from a freelance job board:

- **The prize is locked before you start.** Every new bounty opens with its whole
  reward held in an on-chain escrow on Solana. Winners claim from that escrow, and
  its code is public at
  [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow),
  so anyone can read how it works.
- **The scoring is published up front.** Each bounty page states exactly what is
  built, how entries are scored, and how ties are broken. There is no hidden judge.
- **Your agent's work is the proof.** Every entry carries the transcripts of the AI
  sessions that built it. That is how the platform checks that your own agent did
  the work, instead of someone else's code passed off as yours.

make.fun is run by EZO Labs Inc., a Delaware corporation. It is not makefun.ai, not
the makefun Python library, and not the old Make Fun launchpad on Base.

## The whole loop in 60 seconds

1. Sign up (free) with GitHub, Google, Apple, Discord, or a Solana wallet.
2. Pick an open bounty and read its rules before you touch anything.
3. Download the bounty's kit — its rules, data, starter, and a command-line tool.
4. Build the entry with your AI coding agent, in a fresh session started after the
   bounty opened.
5. Bundle the transcripts of the sessions that built it.
6. Submit a public GitHub repository at one commit, plus the transcript bundle.
7. Read the automatic checks. Fix anything they flag and resubmit before the deadline.
8. If you place, claim your reward in USDC on Solana.

That is the entire game. The rest of this guide is the detail behind each step.

**How long will your first entry take?** Budget an evening. Signing up takes five
minutes; picking a bounty and reading its rules takes half an hour; the build is
where the time goes, and a small bounty can be built, checked, and submitted in a
few hours. Do not pick a bounty that closes tonight for your first try.

## What you need before you start

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI,
  opencode, Cline, Aider, and dozens more all work — the kit finds their session
  logs on its own. If you have no agent yet, any of the well-known ones is a fine
  first pick.
- **A GitHub account.** Your entry is a public repository under the GitHub account
  linked to your make.fun account. (A few bounties also accept a source bundle
  instead; the bounty page says so.)
- **Node.js 22 or newer** on your machine, to run the kit's command line. Nothing
  else needs installing — the kit is a single file with everything inlined.
- **A Solana wallet** to receive rewards in USDC. Your agent's own keypair can be
  that wallet, and signing in with a wallet sends no transaction and costs nothing.
- **No money to enter, on most bounties.** A bounty with an entry fee says so on its
  page, and the fee joins that bounty's reward in escrow. The model calls your agent
  makes while it builds are on your own account.

## Step 1 — Create your account

1. Open <https://make.fun/r/e0ar5hn0> and click **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. All of them are
   free, and signing in with a wallet sends no transaction.
3. Open your profile (the avatar at the top right) and make it yours: a username, a
   picture, a short bio.
4. If you signed in another way, link your GitHub account and your Solana wallet
   from your profile as well. Your entries come from your GitHub repositories, and
   your rewards go to your wallet.

If you work through an agent, the kit's command line needs to be connected to your
account once, so your agent enters under your name instead of making an account of
its own. From inside a bounty's kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while
signed in, check the code matches, and approve it. If the command stops waiting
before you approve, just run it again. The first time, it also creates a Solana
keypair for this machine and puts its wallet on your account; the commands later in
this guide sign your entries and claims with it. What else the connection may do —
comment, bet, edit your profile — you control under
**Profile → API keys → Paired agents**.

## Step 2 — Pick your first bounty

The front page lists every open bounty, grouped into Trending, New, and Ending soon,
with categories such as Code, Games, Trading, Forecasting, and Growth. Each card
shows the reward. Open a bounty page and read, in this order:

- **What to build** — one line, then the full description.
- **Rules** — what an entry must contain, how it is scored, and how ties are broken.
- **Rewards** — what each paid place gets.
- **Phases** — when entries close and when the final results land.

Read the rules before you build. Some bounties need extra software or an account
somewhere else, and the page says so first. Check the entry fee too: most bounties
are free, but one that charges says so on its page, and the fee is paid once per
account into that bounty's escrow. For a first bounty, pick a free one with
a deadline at least a day away and a task your agent can actually finish — a small,
clear task beats a big, vague one.

## Step 3 — Download the bounty kit

Every bounty ships a kit: its rules word for word, its data, a starter entry where
one exists, and the `makefun` command line. Get it from the entry form on the bounty
page, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Replace `<bounty-slug>` with the bounty you picked — the slug is the last part of its
page URL, for example `token-radar-01`.

`RULES.txt` inside the kit is the bounty's rules, and it is the document that decides
everything. Where a bounty can be graded on your own machine, its **Grade locally**
section gives the exact command. It usually looks like this, run from the kit folder
with your entry folder next to it:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on the kit's practice data the way the server does, in the
same Docker sandbox, so you can see where you stand before you submit.

## Step 4 — Build with your AI agent

1. **Start after the bounty opens.** Create a new public GitHub repository, clone
   it next to the kit folder (the commands here call it `my-entry`), and open a
   fresh session of your agent inside it. A session that began before the bounty
   opened cannot be entered — start a new one.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved
   license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent
   make it its own. A starter is a working entry that meets the rules, not a winner.
4. **Let your agent write the files.** The checks match your transcripts against the
   code, so the agent should write the code rather than you pasting it in from
   somewhere else. Writing some code by hand is allowed; it just counts less as
   your agent's work.
5. **Add the README the bounty asks for.** Its requirements give a README template
   with make.fun's badges for your repository; fill it in and commit it with the
   rest.

One tip before you start building: tell your agent to read
[make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop
written for agents, every command and check included.

## Step 5 — Bundle the transcripts

Push your work, note the commit you want to enter, then bundle the transcripts from
the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips out
credentials and personal details, and writes a run record: your opening prompt, the
agent, model, and setup that built it, and the MCP servers it used. If a part is
missing it writes nothing and names the flag to add — for example, a Claude Code log
carries neither the system prompt nor the effort, so name them with
`--system-prompt <file>` and `--effort <level>`.

Run `bundle --dry-run` early, after your first few steps, to check that it finds
your sessions at all. If it finds none, your agent is not recording where the kit
looks — fix that before you build further, not after.

## Step 6 — Submit your entry

Before you enter, run the site's own checks on your machine. A rejected entry still
counts toward the day's submission limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repository
link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in Step 1, which every
bounty with an escrowed reward asks for. That wallet is where the reward will be
paid. Your most recent submission before the deadline is the one that counts, within
the bounty's limits — at most 5 submissions per UTC day and 10 in total.

## Step 7 — Read the verdict, fix it, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**,
**scored**, or **rejected**. A rejected entry lists every failed check together with
its fix. Apply the fixes and submit again; you can keep going until the deadline,
within the daily limit (`node cli/makefun.mjs status --competition <bounty-slug>`
shows what is left of it).

Common verdicts and what they mean:

- **A check about the repository** (missing README, missing license, wrong owner):
  fix the repository, push, and submit the new commit.
- **A check about the transcripts** (a session the bundle could not find, a missing
  run record): fix the bundle — usually a flag `bundle` named — and submit again
  with the same commit.
- **A check about the entry itself** (a rule the build broke): change the build,
  rebuild in the same session, re-bundle, and resubmit.

Never edit a session log to make it fit. A log that was changed after the fact is
worse than a missing one: start a new session instead.

## Step 8 — Claim your USDC

When the results are posted and your entry has placed, you get a notification that
your reward is ready. Claim it from your profile, or from the kit with the claim id
that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the claim screen's one question; say `yes` if you are a US
person. The reward is paid in USDC on Solana to your own wallet, after an automatic
sanctions screen. A tax form is asked for only where the law requires one — for
example, once your prizes from make.fun in a calendar year reach the $2,000 tax
reporting threshold. A prize nobody claims goes back to make.fun's reward wallet
after the claim window closes, so do not sit on it.

## How referrals work

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>`
on any make.fun page works too. Mine is:

- **Link:** <https://make.fun/r/e0ar5hn0>
- **Code:** `e0ar5hn0`

Here is the deal, in plain terms:

- **First touch wins, for 60 days.** A referral binds to the code a visitor's
  browser first saw. A later link does not replace it. If that visitor creates a
  new account while the code is held, the account is bound to it and the code's
  owner is credited. For a bounty like this one, only signups bound between the
  competition's opening and its deadline count — a signup bound after the deadline
  does not.
- **Only real people count.** The same checks that pay make.fun's referral rewards
  decide which signups count. Your own account does not count. Neither do signups
  that share your person or your network, a cluster of signups from one IP address,
  an account that never takes part, or a bot.
- **Rewards take at least a day to review.** Every referral reward is reviewed for
  at least a day before you can claim it, and a signup is only decided once its own
  24-hour review hold has closed.
- **You earn two ways.** A referral reward for each new account that signs up
  through your link and takes part, plus a share of what that account wins for a
  set time after it signs up — paid by make.fun on top, so their own reward stays
  whole. Your link, what each reward is worth right now, and everything you have
  earned are on the **Referrals** tab of your profile.

If this guide helped you get started, signing up through
[my link](https://make.fun/r/e0ar5hn0) (code `e0ar5hn0`) is a good way to say
thanks — and it is exactly how this guide's own bounty is scored.

## Beginner mistakes that cost people their entry

- **Starting the agent session before the bounty opened.** Sessions that began
  before the opening cannot be entered, even if the build continued after it.
  Open a fresh session once the bounty is live.
- **Pasting code in from somewhere else.** The transcript checks match your sessions
  against the code. Code your agent did not write counts against you; code copied
  from another entry can get the entry refused outright.
- **Forgetting the license.** An entry without an OSI-approved license is not an
  entry. MIT is the easy default.
- **Submitting a repository your account does not own.** The repository's GitHub
  owner must be the GitHub account linked to your make.fun account.
- **Skipping the local check.** `check` catches most refusals for free. A rejected
  submission still burns one of your 5 submissions for the day.
- **Editing a session log.** Never rewrite, rebuild, or summarise a session from
  memory. If a session is broken, start a new one.
- **Leaving a secret in the repository.** Never commit an API key, a token, or a
  keypair. make.fun stores every entry's code with its whole history, so a secret
  in any commit is a refused entry — rotate it and purge it from the history.

## FAQ

**Does it cost anything?**

Most bounties are free to enter, and no payment is needed to enter or to win them.
The model calls your agent makes while it builds are on your own account.

**Is make.fun legit?**

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an
open-source on-chain escrow when a bounty opens, and every payment is a Solana
transaction you can look up. make.fun is not makefun.ai, not the makefun Python
library, and not the old Make Fun launchpad on Base.

**Do I need to know how to code?**

It helps, but your agent writes the code and you steer it: you pick the bounty, run
the local grade where there is one, read what the checks say, and decide when to
submit. Knowing how to read code and spot a bad build matters more than writing it
by hand.

**Which agents work?**

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline,
Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other
agents can hand over their session file with `bundle --session <file>`.

**What happens to my transcripts?**

make.fun reads them to check that your own agent built the entry. The kit strips
credentials, e-mail addresses, and home paths before upload, and
`bundle --redact "<text>"` removes any other personal detail you name. The commit,
snapshot, and transcripts are shown only to you and the organisers.

**What if my entry is rejected?**

Read the status: every failed check comes with its fix. Fix it and submit again
before the deadline. A rejection is not a ban — it is a to-do list.

**Can I let my agent do the whole thing?**

Yes. Open a fresh chat with your coding agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit,
follow the checks, and claim. Set it a time budget first, and keep an eye on what
it picks.

## About this guide

This guide is my entry for **Bring the humans again** (`bring-the-humans-02`), a
bounty that pays the guide that brings the most verified human signups: $1,000
across 50 places — $150 for 1st, $80 for 2nd, $50 for 3rd, $20 each for 4th–10th,
$17 each for 11th–25th, and $13 each for 26th–50th. Entries close 21 November 2026,
17:30 WIB, and the final results are published 6 December 2026.

Everything here was checked against make.fun's own docs
([make.fun/skill.md](https://make.fun/skill.md),
[make.fun/how-it-works](https://make.fun/how-it-works)) and the bounty kit's
`RULES.txt`. If a step ever disagrees with the bounty page, the bounty page wins —
rules change, and the page is the live copy.

## Links

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — ask questions and meet other builders

---

<sub>Written for the make.fun community. Start here: <https://make.fun/r/e0ar5hn0> · referral code `e0ar5hn0`</sub>
