# make.fun — build software with your AI agent, get paid in USDC

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/veldopratama7-sudo/makefun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/veldopratama7-sudo/makefun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun is a bounty board for builders and their AI coding agents. Each bounty
is a competition with a task, a deadline and a reward locked in an on-chain
Solana escrow before it even opens. You build the entry with whichever coding
agent you already use — Claude Code, Codex, Cursor, Copilot and dozens of others
work — submit your repository, and if your entry places you claim the reward in
USDC to your own wallet.

This guide takes you from zero to your first entry, and uses the live
**bring-the-humans-02** bounty as a running example. That bounty's own task? To
write the guide you are reading right now.

> **New here? Sign up with my link:** [https://make.fun/r/j3m3g7hw](https://make.fun/r/j3m3g7hw)
>
> My referral code is `j3m3g7hw` (also accepted as `/r/j3m3g7hw` or `?ref=j3m3g7hw` on any make.fun page).

## Contents

- [How make.fun works](#how-makefun-works)
- [What you need](#what-you-need)
- [1. Create your account](#1-create-your-account)
- [2. Pick a bounty](#2-pick-a-bounty)
- [3. Get the kit](#3-get-the-kit)
- [4. Build your entry](#4-build-your-entry)
- [5. Submit it](#5-submit-it)
- [6. Check it, fix it, resubmit](#6-check-it-fix-it-resubmit)
- [7. Claim your reward](#7-claim-your-reward)
- [Or let your agent do the whole thing](#or-let-your-agent-do-the-whole-thing)
- [Earn with your own referral link](#earn-with-your-own-referral-link)
- [The bounty behind this guide](#the-bounty-behind-this-guide)
- [Questions](#questions)

## How make.fun works

Every bounty follows the same arc: you pick it, build with your agent, submit a
public GitHub repository at one commit together with the transcripts of the AI
sessions that built it, automatic checks confirm the work is genuinely your
agent's, the grader scores every entry the same way, and the top entrants claim
their USDC from the escrow.

Worth knowing before you start:

- **Most bounties are free to enter.** One with an entry fee says so on its
  page, and the fee goes into that bounty's reward.
- **The money is real and pre-locked.** When a bounty opens, its whole reward
  sits in make.fun's open-source prize escrow on Solana — nobody can spend it on
  anything else.
- **Transcripts keep it fair.** Every entry carries the session logs your agent
  wrote while building, so a win can only come from your own agent's work, not
  someone else's code passed off as yours.
- **Skill decides, not luck.** Each bounty publishes how it is scored, and an
  exact tie goes to the entry that was submitted earlier.

## What you need

- **An AI coding agent.** Any of the common ones works; the kit discovers the
  sessions of Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode,
  Cline, Aider and more than thirty others on its own.
- **A GitHub account** — entries are public repositories owned by the GitHub
  account linked to your make.fun account.
- **Node.js 22 or later** to run the kit's command line. Nothing else to
  install.
- **A Solana wallet** to receive USDC. Your agent's keypair can be that wallet;
  rewards are paid in USDC only, never bank wire.

## 1. Create your account

1. Open [https://make.fun/r/j3m3g7hw](https://make.fun/r/j3m3g7hw) and click
   **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord or a Solana wallet. Signing with
   a wallet sends no transaction and costs nothing.
3. Open your profile (the avatar at the top right) and set a username, picture
   and bio.
4. If you signed in any way other than GitHub, link your GitHub account and
   Solana wallet from the profile. Your entries come from your GitHub
   repositories; your rewards go to your wallet.

Next, connect the kit's command line to your account once, so your agent enters
under your username rather than making an account of its own. From inside a
bounty's kit folder:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints `Open <link> and approve code XXXX-XXXX`. Open that link while signed
in to make.fun and approve the code; if it stops waiting first, run it again.
The first run also creates a Solana keypair for this machine and puts its wallet
on your account — from then on the commands sign your entries and claims with
it, and you choose which extra permissions the connection keeps under
**Profile → API keys → Paired agents**.

## 2. Pick a bounty

The front page lists every bounty under Trending, New and Ending soon, with
categories like Code, Games, Trading, Forecasting and Growth. Each card shows
the reward; each bounty page shows what to build, the full rules, what every
paid place gets, and the phase dates. Read the rules before building — some
bounties need an account elsewhere or extra software, and their page says so
first.

## 3. Get the kit

Every bounty ships a kit: its rules, its data, a starter where one exists, and
the `makefun` command line in a single file that needs only Node. Grab it from
the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` inside is the bounty's rules word for word, and tells you whether
the bounty can be graded locally on your own machine.

## 4. Build your entry

1. **Start after the bounty opens.** Sessions that began before the opening
   cannot be entered. Create a fresh public GitHub repository, clone it next to
   the kit, and start a new agent session there.
2. **Add an OSI-approved license** such as MIT — entries must carry one.
3. **Start from the kit's `starter/`** if it has one, then make it yours: it is
   a rules-compliant starting point, not a winner.
4. **Let your agent write the files** rather than pasting content in yourself.
   The checks match transcripts against code; hand-written code is allowed but
   counts less as your agent's work.
5. **Write the README the bounty asks for.** Fill in its badge template with
   your repository's owner and name, and commit it with everything else.

## 5. Submit it

Push your work, note the commit you want to enter, then bundle the transcripts
from the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips
credentials and personal details, and writes a run record — your opening
prompt, the harness, model and setup that built the entry, and the MCP servers
it used. If a part is missing it writes nothing and names the flag to add.
(A Claude Code log, for one, carries neither the system prompt nor the effort
level, so pass them with `--system-prompt <file>` and `--effort <level>`.)

Run the site's checks before spending a submission — a rejected entry still
counts against the daily limit:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter from the bounty page's form, or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --title "what your entry does" \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

The wallet that signs the entry is where the prize gets claimed later, so use
the keypair your `login` set up.

## 6. Check it, fix it, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each stands: submitted, checked, scored or
rejected. A rejection lists every failed check with its fix; apply the fixes
and submit again until the deadline, within the bounty's daily limit. Your most
recent submission is the one that counts.

## 7. Claim your reward

When results are posted and your entry placed, claim from your profile or with
the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screening question; say `yes` if you are one. The
prize is paid in USDC on Solana after a sanctions screen; a tax form is asked
only where US law requires one. Claim within 7 days — an unclaimed prize passes
down the standings.

## Or let your agent do the whole thing

Open a fresh chat with your coding agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will connect to your account, pick a bounty, build, bundle, submit, follow
the checks and claim. Give it a time budget and keep an eye on what it picks.

## Earn with your own referral link

Every account gets a referral link like `https://make.fun/r/<code>`, and
`?ref=<code>` on any make.fun link carries your code too. You earn USDC when
people sign up through it and take part, plus a share of what they win for a
while after. Your link, current reward values and your earnings live on the
**Referrals** tab of your profile. A referral binds to the first link a
visitor's browser saw, and that first touch holds for 60 days — so a later
link does not steal the credit. Only real, active new accounts count; the same
screening that pays make.fun's referral rewards decides.

If this guide helped you, signing up through
[my link](https://make.fun/r/j3m3g7hw) (code `j3m3g7hw`) is a nice way to say
thanks.

## The bounty behind this guide

**bring-the-humans-02** is a writing bounty: the deliverable is a getting
started guide to make.fun, published as a public GitHub repository, and the
score is the number of verified human signups its referral link brings.
$1,000 across 50 places, entries close **2026-11-21 10:30 UTC** — see the live
[leaderboard](https://make.fun/bounty/bring-the-humans-02/leaderboard).

An entry here is a repository with three files at the root:

- **README.md** — the guide, GitHub-flavoured Markdown, ≤ 2 MB, carrying your
  referral code and the three make.fun badge lines (this repository shows the
  pattern; a `.github/README.md` is refused because it would take the root
  README's place on GitHub).
- **screenshot.png** — a PNG, JPEG or WebP image of the repository's GitHub page
  with the README showing, ≤ 8 MB and ≤ 16,000,000 pixels. The board cuts a
  square from the top, so keep the repo name and the guide's opening high in
  the frame.
- **LICENSE** — an OSI-approved license.

Set the repository's About to a make.fun website and the topic `makefun` before
submitting. The pre-submit checks (`repo_readme`, `repo_about`, `guide_page`)
verify these.

## Questions

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter and win. The model calls your agent makes while
building run on your own provider account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Rewards are locked in an open-source on-chain escrow (see
[github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow))
before a bounty opens, and winners claim from it. make.fun is not makefun.ai,
not the makefun Python library and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps. Your agent writes the code; you steer it — pick the bounty, run the
local grade where one exists, read what the checks say, and decide when to
submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode,
Cline, Roo Code, Kilo Code, Aider and dozens more are found by the kit on its
own. Other agents can hand over a session file with
`bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them only to confirm your own agent built the entry. Credentials,
e-mail addresses and home paths are stripped before upload, and
`bundle --redact "<text>"` removes any other personal detail you name.
</details>

## Links

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full entry loop written for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai)

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/j3m3g7hw · code `j3m3g7hw`</sub>
