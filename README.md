# Getting started with make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/veldopratama7-sudo/makefun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/veldopratama7-sudo/makefun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

<!-- DRAFT v1 — sections marked [VERIFY] need the starter kit's fact-checked skeleton
     before submission. Written while kit access was blocked; will be revised. -->

make.fun is a platform where developers build, ship and compete. This guide walks
you through what make.fun is, how its bounties work, and how to enter one yourself —
using the live **bring-the-humans-02** bounty as a worked example.

## Why this bounty exists

**bring-the-humans-02** challenges you to write the best getting-started guide to
make.fun — exactly the document you are reading now. The scoring is simple and
human-centric: your entry is judged by how many **verified human signups** arrive
through your referral link. Cash ($1,000 spread across 50 ranked places) is awarded
from the top of the leaderboard down.

Key facts for this round:

- **Bounty:** `bring-the-humans-02`
- **Deadline:** 2026-11-21 10:30 UTC
- **Prize pool:** $1,000 across 50 places
- **Score:** count of verified human signups credited to your referral link

## How signing up works

If this guide helped you, you can credit the author by joining through their
referral link:

- Referral link: **https://make.fun/r/j3m3g7hw**
- Referral code: **`j3m3g7hw`** (also accepted as `/r/j3m3g7hw` or `?ref=j3m3g7hw`)

Signups are verified as real humans before they count, so one genuine reader is
worth more than any amount of automated noise — don't bother with the latter.

## What an entry looks like

An entry is a **public GitHub repository** containing three things at its root:

1. **README.md** — a getting-started guide to make.fun in GitHub-flavoured
   Markdown (≤ 2 MB) that contains your referral code/link and the official
   make.fun badge lines for the bounty (see the three badges at the top of this
   file for the expected shape).
2. **screenshot.png** — a screenshot (PNG, ≤ 8 MB, ≤ 16 MP) of your repo's own
   GitHub page with the README visible. The board crops a square from the top of
   it, so keep the repo name and the opening of your guide near the top.
3. **LICENSE** — an OSI-approved open-source license (MIT is a fine default).

## Entering a bounty [VERIFY]

<!-- [VERIFY] CLI flags and quota numbers below must be checked against the
     make.fun starter kit / docs before submission. -->

Entries are submitted through the make.fun tooling:

```bash
# fetch the bounty's starter kit, which includes rules and a check CLI
# then, from the kit directory:
node cli/makefun.mjs submit --competition bring-the-humans-02 \
  --repo-url https://github.com/<you>/<your-repo> \
  --commit <full-sha> \
  --title "your entry title" \
  --bundle bundle.tar.gz
```

Submission quota is 5 per day and 10 in total per account, and a refused gate item
can be fixed and resubmitted, so an early honest attempt is cheap and useful.

## Checking your entry [VERIFY]

Before submitting you can lint the repo-side requirements — README present and
well-formed, badges correct, screenshot within limits — with the kit's check
command:

```bash
node cli/makefun.mjs check
```

After submitting, poll the submissions API to watch your entry's status:

```bash
curl -H "x-api-key: $MAKEFUN_API_KEY" \
  https://make.fun/api/submissions/<submission-id>
```

## Repo hygiene tips

- Put the badges, the referral link and the first headings **high** in the README —
  the leaderboard crops from the top of your screenshot.
- Don't bury a second README under `.github/`; the gate rejects that.
- Keep the repo public at the moment of submission and while the bounty is judged.
- Fill in the repo **About** panel: set the website to the bounty page and add a
  `makefun` topic — it's part of the checks.

## License

This guide is released under the MIT License — see [LICENSE](LICENSE).
