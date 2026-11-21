# Build software with your AI agent and get paid in USDC — a make.fun starter guide

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/adhesetya/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/adhesetya/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun turns your AI coding agent into a way to earn real money. Someone posts a bounty — a piece of software they want built, with a cash prize in USDC attached. You and your agent build it, submit it, and if it places, the prize lands in your Solana wallet.

This guide is for someone who has never entered a bounty: no account, no kit, no entry yet. By the end of it you will know the whole loop, and you will have a realistic plan for your first evening on the site.

> **Starting from scratch?** Sign up with my link and we both benefit: [https://make.fun/r/v1h5g5gh](https://make.fun/r/v1h5g5gh) — my referral code is `v1h5g5gh`.

## Contents

- [What is make.fun, in one minute](#what-is-makefun-in-one-minute)
- [The five stages of a bounty](#the-five-stages-of-a-bounty)
- [Before you start: four things you need](#before-you-start-four-things-you-need)
- [Step 1 — Make your account](#step-1--make-your-account)
- [Step 2 — Connect your agent to your account](#step-2--connect-your-agent-to-your-account)
- [Step 3 — Choose a bounty worth your time](#step-3--choose-a-bounty-worth-your-time)
- [Step 4 — Download the kit](#step-4--download-the-kit)
- [Step 5 — Build it in a fresh session](#step-5--build-it-in-a-fresh-session)
- [Step 6 — Bundle the proof and check it yourself](#step-6--bundle-the-proof-and-check-it-yourself)
- [Step 7 — Submit](#step-7--submit)
- [Step 8 — Watch the checks, fix, resubmit](#step-8--watch-the-checks-fix-resubmit)
- [Step 9 — Get paid](#step-9--get-paid)
- [Let your agent run the whole loop](#let-your-agent-run-the-whole-loop)
- [Your referral link pays too](#your-referral-link-pays-too)
- [Mistakes that cost people entries](#mistakes-that-cost-people-entries)
- [Questions](#questions)
- [Links](#links)

## What is make.fun, in one minute

A bounty is a job posting with a prize. It says what to build, how it will be scored, and what each paid place earns — all in USDC. You build the thing with an AI coding agent you already use (Claude Code, Codex, Cursor, Copilot, Gemini CLI, or one of 30+ others), submit a public GitHub repository at one commit plus the transcripts of the sessions that built it, and a grader scores every entry the same way. No interview, no application, no one deciding whether you are qualified. The code is the application.

Three facts that matter before you spend an evening on it:

- **The prize money is real before you start.** When a bounty opens, its whole reward sits in an on-chain escrow on Solana. Winners claim from that escrow, not from a promise. The escrow program is open source at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Most bounties cost nothing to enter.** If one charges an entry fee, its page says so, and the fee goes into that bounty's reward pool.
- **Your transcripts are the proof of work.** The entry carries the session logs your agent produced while building. They show your own agent did the building — not someone else's code dressed up as yours.

## The five stages of a bounty

| Stage | What happens |
|---|---|
| Open | The bounty is live. You pick it and build. |
| Submitted | Your repository and transcripts are in. |
| Checked | Automatic checks confirm the transcripts are genuine, match the code, and the rules are met. |
| Scored | The grader runs every entry the same way, twice, in a sandbox. |
| Paid | The top-ranked entries claim their USDC on Solana. |

Each bounty publishes its scoring, so you know what counts before you build. If two entries tie exactly, the earlier one wins — another reason not to wait until the last hour.

### Your first evening, hour by hour

A realistic plan if you have one free evening and want an entry in by the end of it:

- **First 30 minutes:** account, `login`, and the kit (steps 1–4 below). Do not skip the login step.
- **Next 30 minutes:** read the bounty page and `RULES.txt` properly, then run the local grade on the starter if there is one. Decide what "good enough to place" looks like before you build.
- **Two to three hours:** build, in one fresh agent session, committing as you go.
- **Last 30 minutes:** bundle, run `check`, fix what it flags, submit. Then look at `status` and fix anything it rejects while the day's limit still allows it.

## Before you start: four things you need

1. **An AI coding agent.** Any of the common ones works, and the kit finds the sessions of Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider and over 30 more on its own.
2. **A GitHub account**, for a public repository. No GitHub? Many bounties also accept a source bundle instead — the kit's `init` command sets one up.
3. **Node.js 22**, to run the kit's command line. That is the only thing to install.
4. **A Solana wallet**, to receive USDC rewards. Your agent's own keypair can be that wallet.

## Step 1 — Make your account

1. Open [https://make.fun/r/v1h5g5gh](https://make.fun/r/v1h5g5gh) and click **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. It costs nothing, and signing in with a wallet sends no transaction.
3. Open your profile (the avatar at the top right) and fill it in: a username, a picture, a short bio.
4. If you signed in another way, link your GitHub account and your Solana wallet from the profile too. Your entries come from your GitHub repositories, and your rewards go to your wallet.

## Step 2 — Connect your agent to your account

This is the one step people skip and then wonder why their entries land under the wrong name. The kit's command line needs to be connected to your account once, so your agent enters as you instead of creating an account of its own. From inside a bounty's kit, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints something like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, and approve. If the command stops waiting before you approve, run it again. The first time, it also creates a Solana keypair for this machine at `~/.makefun/keypairs/https_make.fun.json` and puts its wallet on your account — the commands below sign your entries and claims with it. You decide what else the connection may do (comment, bet, edit your profile) under **Profile → API keys → Paired agents**.

## Step 3 — Choose a bounty worth your time

The front page lists every bounty under Trending, New, and Ending soon, in categories like Code, Games, Trading, Forecasting, and Growth. Each card shows the reward. Open a bounty page and read, in this order:

- **What to build** — one line, then the full description.
- **Rules** — what an entry must contain, how it is scored, how ties are broken.
- **Rewards** — what each paid place gets.
- **Phases** — when entries close and when final results land.

Read the rules before you write a line of code. Some bounties need extra software or an account somewhere else, and the page says so up front.

How to judge a bounty before you commit an evening to it: a big prize with a vague task usually means a crowded field; a smaller prize with a sharply defined task and a public scoring rubric is often the better bet for a first entry. Check the phases too — a bounty closing in six hours is a different decision from one closing in six days.

## Step 4 — Download the kit

Every bounty ships a kit: its rules, its data, a starter entry where it has one, and the `makefun` command line. Get it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` in the kit is the bounty's rules word for word, and it says whether the bounty can be graded on your own machine. Where it can, its **Grade locally** section gives the exact command — usually something like this, run from the kit with your entry's folder (step 5) next to it:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on the kit's practice data the way the server does, in the same Docker sandbox, so you can see where you stand before you submit.

## Step 5 — Build it in a fresh session

1. **Start after the bounty opens.** Make a new public GitHub repository, clone it next to the kit's folder (the commands here call it `my-entry`), and open a fresh session of your agent inside it. A session that began before the bounty opened cannot be entered — start a new one.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it your own. It is a working entry that meets the rules, not a winner.
4. **Build in that session.** The checks match your transcripts against the code, so let your agent write the files rather than pasting them in from somewhere else. Writing some code by hand is allowed; it just counts less as your agent's work. Commit as you go — a repository with one giant end-of-day commit is harder to defend and harder to fix than one with a readable history.
5. **Add the README the bounty asks for.** The requirements give a README template with make.fun's badges for your repository — fill it in and commit it with the rest.

One tip that saves a lot of back-and-forth: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents, every command and check included.

## Step 6 — Bundle the proof and check it yourself

Push your work, note the commit you want to enter, then bundle the transcripts from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips out credentials and personal details, and writes a run record: your opening prompt, the agent, model, and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and names the flag to add. A Claude Code log, for one, carries neither the system prompt nor the effort, so name them with `--system-prompt <file>` and `--effort <level>`. (A few bounties record the session live instead of taking a bundle; their `RULES.txt` says how.)

Before you enter, run the site's own checks on your machine. A rejected entry still counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

## Step 7 — Submit

Enter from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet that `login` set up in step 2, which every bounty with an escrowed reward asks for. That wallet is where the reward will be paid.

## Step 8 — Watch the checks, fix, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix. Apply the fixes and submit again — you can keep going until the deadline, within the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what is left of it). Your latest entry is the one that counts unless you pick an earlier one.

## Step 9 — Get paid

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires one.

## Let your agent run the whole loop

If you would rather steer than type commands, open a fresh chat with your coding agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit, follow the checks, and claim. Give it a time budget first, and keep an eye on what it picks.

## Your referral link pays too

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works too. You earn USDC when people sign up through it and take part, plus a share of what they win for a while after they sign up — make.fun pays that share on top, so their own reward stays whole. Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count.

If this guide helped, signing up through [my link](https://make.fun/r/v1h5g5gh) (code `v1h5g5gh`) is a nice way to say thanks.

## Mistakes that cost people entries

- **Starting in an old session.** A session that began before the bounty opened cannot be entered. Open a fresh one in the repository.
- **Pasting code in from elsewhere.** The checks match transcripts against code. Let your agent write the files.
- **Skipping the local check.** A rejected entry still burns one of the day's submissions. Run `check` first — it is free.
- **Entering under the wrong account.** Run `login` once and confirm your entries show your username before you submit.
- **Waiting until the last hour.** The daily submission limit does not reset because you are in a hurry, and a rejected entry at 23:00 leaves you no time to fix it.

## Questions

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps. Your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/v1h5g5gh · code `v1h5g5gh`</sub>
