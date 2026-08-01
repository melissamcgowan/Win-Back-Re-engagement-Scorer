# Win-Back Re-engagement Scorer

An interactive tool that ranks churned customer accounts by likelihood of successful reactivation, then weighs that likelihood against account value to show a retention team where a win-back motion should actually spend its effort first.

**[Live demo →](#)** (https://melissamcgowan.github.io/Win-Back-Re-engagement-Scorer)

## Why I built this

Ranking churned accounts by "most recent" or "highest MRR" alone tends to waste outreach on the wrong accounts; a high-value account that churned to a competitor is a much worse bet than a mid-size account that left over a support issue that's since been fixed. This project models that distinction directly, so the output is a prioritized action list, not just a sorted table.

## How the scoring works

Each churned account gets a composite score (0–100) built from four weighted factors:

| Factor | Weight | Why it matters |
|---|---|---|
| **Churn reason reversibility** | 35% | Price/support-driven churn is far more winnable than a competitor switch or a fundamental product-fit gap |
| **Recency window** | 25% | Reactivation likelihood peaks 4–10 months after churn; too soon and the reason is still raw, too late and the account has moved on |
| **Pre-churn engagement depth** | 25% | Accounts that were genuinely using the product before they left have more to reactivate than accounts that were already disengaged |
| **Tenure before churn** | 15% | Longer relationships carry more equity and familiarity to rebuild from |

Accounts are grouped into three tiers — **Hot**, **Warm**, **Cool** — each with a distinct recommended outreach cadence and offer strategy, visible by clicking into any row.

The headline visual is a **priority quadrant**: win-back likelihood on one axis, account value (MRR at churn) on the other, dot size scaled to MRR. It reframes the question from "who's most likely to come back" to "where does effort actually pay off," which is the real question a retention team is trying to answer.

## Tech

Single-file HTML/CSS/JS - no build step, no dependencies. Data is synthetic, generated with a seeded random function so results are reproducible. Scoring weights are illustrative and would be calibrated against real historical win-back outcomes in production.

## Part of a larger portfolio

This is one piece of a broader set of AI-powered customer success tools — health scoring, churn prediction, save-play automation, QBR reporting, and more. See the [full portfolio index](https://github.com/melissamcgowan) for the rest.
