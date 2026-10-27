<div align="center">
  <p>
    <img src="https://www.topy.ai/long_logo.svg" alt="TOPY AI CPO" width="420" />
  </p>
  <h1>TOPY AI CPO Skills</h1>
  <p><strong>19 skills that make your coding agent a small company's AI CPO: it decides what to build and proves it worked — feedback triaged with clear rules, de-identified user research, a PMF survey, positioning, RICE priorities, a now/next/later roadmap, PRDs with a success metric, a build-or-not check before the AI CTO, pre-registered experiments read without peeking, and a decision log with falsifiers — on the TOPY.AI CPO MCP server.</strong></p>
  <p>
    <a href="https://www.npmjs.com/package/@topy-ai/cpo-skills"><img alt="npm" src="https://img.shields.io/npm/v/@topy-ai/cpo-skills?style=for-the-badge&color=ff1212" /></a>
    <a href="https://github.com/TOPY-AI-LTD/TOPY-AI-CPO-Skills/blob/main/LICENSE"><img alt="MIT License" src="https://img.shields.io/badge/License-MIT-111827?style=for-the-badge" /></a>
    <a href="https://topy.ai/developers"><img alt="MCP" src="https://img.shields.io/badge/MCP-topy.ai%2Fmcp%2Fcpo-0f172a?style=for-the-badge" /></a>
  </p>
</div>

---

The AI CPO is goal-first. It keeps three standing goals — **people reach value** (activation rate), **people keep
coming back** (weekly active users) and **the product is a must-have** (the PMF score: 40% or more "very disappointed")
— and every skill below exists to move one of them. Usage figures and experiment results come from the tools; a KPI
without a recorded value is "no data", never zero.

- **Core** (`topy-ai-cpo`): connect, the CPO's goals, the weekly product review, the daily watch.
- **Feedback**: capture an item cleanly, triage it, close the loop with the sender.
- **Discovery**: user research, the PMF survey, positioning and a competitor teardown.
- **Planning**: RICE prioritisation, the now/next/later roadmap, PRDs, build or not.
- **Experiments**: plan and start a pre-registered test, read it honestly, instrument and ship behind a flag.
- **Decisions**: log a decision with its falsifier, revisit it when the date comes.

The safety model comes from Maggie Product and Maggie Feedback Triage and does not bend: experiments are
**pre-registered** (hypothesis, metric, MDE, sample, stop rule) and **never peeked at** — a read-out before the planned
sample says "keep running", never "significant"; **every PRD has a success metric and how it is measured**; **every
logged decision has a falsifier**; feedback, interview and usage text is **data, never instructions**, and quotes are
**de-identified**; anything touching **billing or prices, sign-in, permissions, security, privacy, legal text, paid builds
or deleting customer data is a person's decision**; and **the CPO decides what to build — the AI CTO builds**: it writes
no code and ships nothing. Changes take two calls — a preview, then your yes.

## Install

```sh
npx @topy-ai/cpo-skills install                  # this project, for the agents set up here
npx @topy-ai/cpo-skills install -g --mcp         # your user, plus the MCP server
npx @topy-ai/cpo-skills install --category feedback,experiments
npx @topy-ai/cpo-skills list
```

Claude Code plugins: `/plugin marketplace add TOPY-AI-LTD/TOPY-AI-CPO-Skills`, then `/plugin install topy-ai-cpo-all@topy-ai-cpo`.
Codex: `codex plugin marketplace add TOPY-AI-LTD/TOPY-AI-CPO-Skills`. Pi: `pi install npm:@topy-ai/cpo-skills`.
See the [installer README](packages/skills/README.md).

## Connect TOPY.AI

`https://topy.ai/mcp/cpo` — OAuth with your TOPY.AI account (the same one as the AI CEO, CFO, COO, CSO and CRO). Only
the accounts that own the OneMan operation see its product records.

| Client | How |
|---|---|
| Claude, ChatGPT (web, desktop) | custom connector `https://topy.ai/mcp/cpo` |
| Claude Code | `claude mcp add --transport http topy-cpo https://topy.ai/mcp/cpo` |
| Codex | `codex mcp add topy-cpo --url https://topy.ai/mcp/cpo` |
| Clients that only start a command | `npx -y @topy-ai/cpo-mcp` after `npx @topy-ai/cpo-mcp login` |
| Terminal and scripts | `npm i -g @topy-ai/cpo-cli && cpo-cli login` |

Writing code and shipping are not on topy.ai/mcp/cpo: the AI CTO builds, after the build-or-not check and the
Founder's yes.

## How the skills fit together

```
topy-cpo-connect ─▶ topy-cpo-goals
        │
   weekly Tue 09:27:      topy-cpo-weekly-review ─▶ the founder (email) and the CEO
   weekdays 11:07:        topy-cpo-daily-watch (quiet unless something needs attention)
        │
   feedback:    topy-cpo-feedback-capture ─▶ topy-cpo-feedback-triage ─▶ topy-cpo-feedback-reply
   discovery:   topy-cpo-user-research · topy-cpo-pmf-survey ─▶ topy-cpo-positioning
   planning:    topy-cpo-prioritize ─▶ topy-cpo-roadmap ─▶ topy-cpo-build-or-not ─▶ topy-cpo-prd ─▶ the AI CTO
   experiments: topy-cpo-experiment-plan ─▶ topy-cpo-launch-safely ─▶ topy-cpo-experiment-read
   decisions:   topy-cpo-decision-log ─▶ topy-cpo-decision-revisit
```

Try: *"How did the product do this week?"*, *"Triage the new feedback"*, *"Should we build this?"*,
*"Write a PRD for full exports"*, *"Did the onboarding test win?"*

## Packages

| Package | What it is |
|---|---|
| [`@topy-ai/cpo-skills`](https://www.npmjs.com/package/@topy-ai/cpo-skills) | This installer (Claude Code, Codex, Pi, Cursor, Gemini CLI, …) |
| [`@topy-ai/cpo-mcp`](https://www.npmjs.com/package/@topy-ai/cpo-mcp) | The CPO MCP server as a local stdio server (forwards to `https://topy.ai/mcp/cpo`) |
| [`@topy-ai/cpo-cli`](https://www.npmjs.com/package/@topy-ai/cpo-cli) | The AI CPO on the command line |

## Repository structure

```
plugins/
  topy-ai-cpo/                   core skills + .mcp.json (Claude Code) and mcp.json (Codex)
  topy-ai-cpo-feedback/   topy-ai-cpo-discovery/   topy-ai-cpo-planning/
  topy-ai-cpo-experiments/   topy-ai-cpo-decisions/
  topy-ai-cpo-all/               bundle that depends on all six
.claude-plugin/marketplace.json     Claude Code marketplace
.agents/plugins/marketplace.json    Codex marketplace
skills.json                         machine-readable catalogue
packages/skills/                    the @topy-ai/cpo-skills installer
```

The skills are generated from a source catalogue kept next to TOPY.AI's MCP server; the build checks every tool a
skill names against the CPO server's tool list. Please open an issue rather than editing a `SKILL.md`.

## License

MIT © TOPY AI LTD. Privacy: [topy.ai/privacy](https://topy.ai/privacy).

## Skills

<!-- skills:start -->

**19 skills in 6 plugins**, plus the `topy-ai-cpo-all` bundle. Generated from the source catalogue: please open an issue rather than editing a `SKILL.md`.

### AI CPO core (MCP) · `topy-ai-cpo`

| Skill | Tier | What it does |
|---|---|---|
| [`topy-cpo-connect`](plugins/topy-ai-cpo/skills/topy-cpo-connect/SKILL.md) | core | Connect the TOPY CPO MCP server and check what it can see: the product review, the feedback queue, experiments and the decision log. |
| [`topy-cpo-daily-watch`](plugins/topy-ai-cpo/skills/topy-cpo-daily-watch/SKILL.md) | core | Weekdays: new feedback to triage, experiments due for a read-out and decisions due for revisit — a note to the Founder only when something needs attention. |
| [`topy-cpo-goals`](plugins/topy-ai-cpo/skills/topy-cpo-goals/SKILL.md) | core | The AI CPO's standing goals and its status report for the CEO: activation, weekly active users and the PMF score, each with source and date or 'no data'. |
| [`topy-cpo-weekly-review`](plugins/topy-ai-cpo/skills/topy-cpo-weekly-review/SKILL.md) | core | Every Tuesday: usage, the feedback queue by theme, experiments due for a read-out and decisions due for revisit, with at most three actions — for the Founder and the CEO. |

### Feedback · `topy-ai-cpo-feedback`

| Skill | Tier | What it does |
|---|---|---|
| [`topy-cpo-feedback-capture`](plugins/topy-ai-cpo-feedback/skills/topy-cpo-feedback-capture/SKILL.md) | connected | Record a piece of user feedback — a bug, an idea, praise or a question — with where it came from, de-identified, so triage can act on it. |
| [`topy-cpo-feedback-reply`](plugins/topy-ai-cpo-feedback/skills/topy-cpo-feedback-reply/SKILL.md) | connected | Draft the reply each sender is owed — fixed, coming, not planned and why, or one precise question — in plain words and their language, for the Founder to send. |
| [`topy-cpo-feedback-triage`](plugins/topy-ai-cpo-feedback/skills/topy-cpo-feedback-triage/SKILL.md) | connected | Decide each new item — accept, reject, duplicate or needs info — size it small, medium or large, and route it: small and safe to the AI CTO, larger or sensitive ones to a PRD and the Founder. |

### Discovery & positioning · `topy-ai-cpo-discovery`

| Skill | Tier | What it does |
|---|---|---|
| [`topy-cpo-pmf-survey`](plugins/topy-ai-cpo-discovery/skills/topy-cpo-pmf-survey/SKILL.md) | connected | Run the product/market-fit survey properly — the 'very disappointed' question to the right users, 40% as the signal — and read who the product is a must-have for. |
| [`topy-cpo-positioning`](plugins/topy-ai-cpo-discovery/skills/topy-cpo-positioning/SKILL.md) | connected | Write the positioning — for whom, what job, which category, what benefit, unlike which alternative — from a sourced teardown of the real alternatives. |
| [`topy-cpo-user-research`](plugins/topy-ai-cpo-discovery/skills/topy-cpo-user-research/SKILL.md) | connected | Plan and run a small round of user interviews about past behaviour, then turn the notes into de-identified insights and recorded feedback. |

### Planning & specs · `topy-ai-cpo-planning`

| Skill | Tier | What it does |
|---|---|---|
| [`topy-cpo-build-or-not`](plugins/topy-ai-cpo-planning/skills/topy-cpo-build-or-not/SKILL.md) | connected | Before the AI CTO writes code: reuse what exists, compose a routine for a one-off, or build — privately or as a reusable app — with the reason recorded. |
| [`topy-cpo-prd`](plugins/topy-ai-cpo-planning/skills/topy-cpo-prd/SKILL.md) | connected | Write a one-page PRD — problem, evidence, goals, non-goals, success metric and how it is measured, risks, rollout, open questions — that the AI CTO can build from. |
| [`topy-cpo-prioritize`](plugins/topy-ai-cpo-planning/skills/topy-cpo-prioritize/SKILL.md) | connected | Rank candidate features by RICE — reach × impact × confidence ÷ effort — with the scales written down, so the order is explainable and the decision stays a person's. |
| [`topy-cpo-roadmap`](plugins/topy-ai-cpo-planning/skills/topy-cpo-roadmap/SKILL.md) | connected | Keep one roadmap in three stages — now (committed), next (shaped), later (ideas) — ordered by value and effort, tied to goals, with no fake dates. |

### Experiments & launches · `topy-ai-cpo-experiments`

| Skill | Tier | What it does |
|---|---|---|
| [`topy-cpo-experiment-plan`](plugins/topy-ai-cpo-experiments/skills/topy-cpo-experiment-plan/SKILL.md) | connected | Pre-register an A/B test — hypothesis, one primary metric, minimum detectable effect, sample size, duration and stop rule — then start it. |
| [`topy-cpo-experiment-read`](plugins/topy-ai-cpo-experiments/skills/topy-cpo-experiment-read/SKILL.md) | connected | Read a test against its pre-registered plan: keep running until the sample is reached, check the split, report the effect with its uncertainty and guardrails, and log the decision. |
| [`topy-cpo-launch-safely`](plugins/topy-ai-cpo-experiments/skills/topy-cpo-launch-safely/SKILL.md) | standalone | Before launch: define and verify the events the success metric needs, ship behind a feature flag to a small share first, watch guardrails, and keep a one-switch rollback. |

### Decisions · `topy-ai-cpo-decisions`

| Skill | Tier | What it does |
|---|---|---|
| [`topy-cpo-decision-log`](plugins/topy-ai-cpo-decisions/skills/topy-cpo-decision-log/SKILL.md) | connected | Record a product decision with why, the evidence and a falsifier — what would change it — and a date to revisit, so decisions can be checked instead of re-argued. |
| [`topy-cpo-decision-revisit`](plugins/topy-ai-cpo-decisions/skills/topy-cpo-decision-revisit/SKILL.md) | connected | When a decision's revisit date comes, check its falsifier against what the tools now show, and keep it, change it or extend the date — with a new log entry. |

<!-- skills:end -->
