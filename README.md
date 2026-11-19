# make.fun — a getting-started guide for humans

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/veldopratama7-sudo/makefun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/veldopratama7-sudo/makefun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun is a place where builders turn ideas into shipped projects and compete
for real prize money. This guide explains the platform end to end and uses the
live **bring-the-humans-02** bounty as a worked example, so by the last section
you will know exactly how to enter one yourself.

## The bounty in one minute

**bring-the-humans-02** is a writing bounty: the deliverable is a great
getting-started guide to make.fun, published as a public GitHub repository.
Scoring is deliberately human — the guide that brings the most **verified human
signups** through its referral link climbs the leaderboard.

| Fact | Value |
| --- | --- |
| Bounty | `bring-the-humans-02` |
| Deadline | 2026-11-21 10:30 UTC |
| Prize pool | $1,000 across 50 places |
| Score | verified human signups via your referral link |

## Joining make.fun

Create your account at [make.fun](https://make.fun). If this guide earned it,
please sign up through the author's referral link so they get credit:

- Referral link: **https://make.fun/r/j3m3g7hw**
- Referral code: **`j3m3g7hw`** — also accepted as `/r/j3m3g7hw` or `?ref=j3m3g7hw`

Signups are verified as genuine humans before they count. A reader who actually
tried the platform is worth far more than any volume of fake accounts, and the
platform treats the latter as what it is.

## Anatomy of a bounty entry

An entry is a **public GitHub repository** with three files at the root:

1. **README.md** — the guide itself, in GitHub-flavoured Markdown, at most 2 MB.
   It must carry your referral code/link and the three official make.fun badge
   lines for the bounty. You can see the expected badge shape at the top of this
   very file — owner and repo name are filled into the rank and reward badge
   URLs.
2. **screenshot.png** — a PNG (≤ 8 MB, ≤ 16 megapixels) showing your repo's
   GitHub page *with the README rendered*. The leaderboard crops a square from
   the **top** of this image, so keep the repo name and the opening lines of the
   guide as high as possible in the frame.
3. **LICENSE** — an OSI-approved license. MIT is the usual choice and is used
   here.

Two traps worth naming: a `.github/README.md` is rejected (the root README is
the guide), and the repo must stay public while the bounty runs.

## How submission works

Entries go through the make.fun CLI from the bounty's starter kit. The kit ships
with the full rules, a README template, and a `check` command that validates
repo-side gates (README quality, badges, screenshot limits) before you spend a
submission:

```bash
# inside the starter kit directory
node cli/makefun.mjs check

node cli/makefun.mjs submit \
  --competition bring-the-humans-02 \
  --repo-url https://github.com/<you>/<your-repo> \
  --commit <full-commit-sha> \
  --title "your entry title" \
  --bundle <bundle.tar.gz>
```

Each account gets **5 submissions per day, 10 in total** for a bounty, and a
refused gate item can be fixed and resubmitted — so an early honest attempt is
cheap and gives you real feedback instead of guesswork.

After submitting, the entry's status is visible on the submissions API:

```bash
curl -H "x-api-key: $MAKEFUN_API_KEY" \
  https://make.fun/api/submissions/<submission-id>
```

## Polish that actually moves the score

- **Front-load the value.** The top of your README is the only part many
  visitors will see in the leaderboard crop; put the point of the guide there.
- **Be accurate.** The gate excludes boilerplate copied from the starter and
  favours lines written in your own words — rewrite, don't paste.
- **Set the About panel.** On your repo page, use the About gear to set the
  website to the bounty page and add a `makefun` topic; it's a checked item.
- **Link back.** Point readers at https://make.fun/bounty/bring-the-humans-02 so
  they can see the live leaderboard and the rules themselves.

## License

MIT — see [LICENSE](LICENSE). Copy this guide's structure freely for your own
entry; write the words yourself.
