# Win-Back Re-engagement Scorer

An interactive tool that ranks churned customer accounts by likelihood of successful reactivation, then weighs that likelihood against account value to show a retention team where a win-back motion should actually spend its effort first.

**[Live demo →](#)** (https://melissamcgowan.github.io/Win-Back-Re-engagement-Scorer)

## Why I built this

Ranking churned accounts by "most recent" or "highest MRR" alone tends to waste outreach on the wrong accounts. A high-value account that churned to a competitor is a much worse bet than a mid-size account that left over a support issue that's since been fixed. This project models that distinction directly, so the output is a prioritized action list, not just a sorted table.

## How the scoring works

Each churned account gets a composite score (0 to 100) built from four weighted factors:

| Factor | Weight | Why it matters |
|---|---|---|
| **Churn reason reversibility** | 35% | Price/support-driven churn is far more winnable than a competitor switch or a fundamental product-fit gap |
| **Recency window** | 25% | Reactivation likelihood peaks 4 to 10 months after churn. Too soon and the reason is still raw, too late and the account has moved on |
| **Pre-churn engagement depth** | 25% | Accounts that were genuinely using the product before they left have more to reactivate than accounts that were already disengaged |
| **Tenure before churn** | 15% | Longer relationships carry more equity and familiarity to rebuild from |

Accounts are grouped into three tiers, Hot, Warm, and Cool, each with a distinct recommended outreach cadence and offer strategy, visible by clicking into any row.

The headline visual is a **priority quadrant**: win-back likelihood on one axis, account value (MRR at churn) on the other, dot size scaled to MRR. It reframes the question from "who's most likely to come back" to "where does effort actually pay off," which is the real question a retention team is trying to answer.

## Program design: cadence and outreach by tier

The scorer identifies who to prioritize. This section outlines what happens next for each tier: intent, sequencing, and goals for each touchpoint, not finished copy. Think of it as a playbook skeleton a Retention Specialist could execute from directly.

### Hot Tier (score 68+): Save now, offer-led

**Goal:** Convert while the reactivation window is open. These accounts have high reversibility churn reasons and were genuinely engaged before they left, so the cost of moving slowly is the window closing.

**Owner:** Retention Specialist, direct 1:1 outreach (not automated)

**Timeline:**
| Day | Touch | Intent |
|---|---|---|
| 0 | Phone call attempt | Reopen the relationship personally before anything goes in writing. Signals the account matters enough for a human, not a sequence. |
| 0 to 1 | Email 1 (if no call connect) | Low-pressure reconnect, acknowledge the relationship ended, no ask yet. Goal: get a reply, not a reactivation. |
| 5 | Phone call #2 / voicemail + email 2 | Introduce the reactivation offer, tied specifically to their churn reason (see crosswalk below). |
| 10 | Email 3 | Light urgency plus an easy next step (calendar link, not a form). |
| 14 | Final call attempt | Last direct touch before the account drops to Warm-tier nurture. |

**Call script, intent not verbatim:**
- **Open:** Reference the relationship directly, not generically ("You were with us for X months"). Signals this isn't a mass campaign.
- **Discovery:** Ask what's changed since they left, not "why did you leave." Forward-looking, not re-litigating the breakup.
- **Value reminder:** Reference something specific they used to do in-product, tied to their pre-churn engagement data. Proof this isn't a cold call.
- **Offer:** Lead with the offer type matched to churn reason (below), framed as solving their stated reason, not as a discount for its own sake.
- **Close:** One clear next step, a scheduled onboarding call or a trial reactivation, not "let us know."

**Email intent (not drafted copy):**
- Email 1: warm, no ask, "thinking of you" energy
- Email 2: names the offer, ties it to their specific churn reason
- Email 3: adds urgency (offer expiration or capacity framing) plus a frictionless next step

### Warm Tier (score 42 to 67): Nurture, then soft offer

**Goal:** Rebuild enough relationship equity that an offer lands later, rather than leading with one now. These accounts are winnable but the reason or timing is less clear-cut than Hot tier.

**Owner:** Scaled Adoption Specialist, semi-automated with a manual review checkpoint

**Timeline:**
| Week | Touch | Intent |
|---|---|---|
| 1 | Email 1, value/content | No ask. Share something relevant to why they originally bought (a feature update, a use-case story). Reintroduce value before asking for anything. |
| 3 | Email 2, light check-in | Low-key, human-toned "how's it going." Gauge responsiveness before investing more. |
| 6 | Email 3, soft offer | Only sent if prior two got any engagement (open/click/reply). Offer is softer than Hot tier, a free trial period, not a discount. |
| 8 | Route to Retention Specialist for manual review | If any signal of interest, promote to a live conversation; if not, downgrade toward Cool-tier monitoring. |

**Call script (only if promoted from email engagement), intent:**
- **Open:** Reference the specific thing they engaged with (opened the offer email, clicked a link). Shows this isn't blind outreach.
- **Discovery:** Light-touch, confirm whether their original churn reason still applies.
- **Offer:** Present, don't push. Warm tier hasn't earned urgency framing yet.

### Cool Tier (score below 42): Monitor only

**Goal:** Stay visible at near-zero cost, and stay ready to react if a positive signal appears. Don't spend Retention Specialist time here.

**Owner:** CS Ops, automated only

**Cadence:**
- Included in a quarterly win-back digest email (batched, not personalized), general product update framing, no offer
- No outbound calls
- Watch-list only: if a positive signal appears (site visit, referral, review mention, a former champion resurfacing at a new company), auto-promote the account to Warm tier for manual pickup

### Churn-reason-to-offer crosswalk

| Churn reason | Messaging angle | Offer type |
|---|---|---|
| Price / budget | Flexibility, not just discount | Revised pricing tier or payment terms |
| Support issue | Proof the issue is resolved | Dedicated onboarding/support lap, no discount needed |
| Lost champion | Rebuild relationship with new stakeholder | Fresh onboarding walkthrough for the new contact |
| Low engagement | Reintroduce value they never saw | Guided re-onboarding, not a discount |
| Product fit gap | Only pursue if the gap has since closed | Feature-specific demo of what's changed |
| Switched to competitor | Lowest priority, only revisit on a real signal | None until they re-engage first |

### What to track

- **Save/reactivation rate by tier:** validates whether the scorer's tiering is actually predictive
- **Time-to-reactivate:** how long from first touch to signed reactivation, by tier
- **Revenue recovered vs. revenue at risk:** ties the program back to the GRR/revenue-retention framing leadership cares about
- **Touch-to-conversion ratio:** flags whether a tier's cadence is over- or under-invested relative to its return

## Tech

Single-file HTML/CSS/JS, no build step, no dependencies. Data is synthetic, generated with a seeded random function so results are reproducible. Scoring weights are illustrative and would be calibrated against real historical win-back outcomes in production.

## Part of a larger portfolio

This is one piece of a broader set of AI-powered customer success tools: health scoring, churn prediction, save-play automation, QBR reporting, and more. See the [full portfolio index](https://github.com/melissamcgowan) for the rest.
