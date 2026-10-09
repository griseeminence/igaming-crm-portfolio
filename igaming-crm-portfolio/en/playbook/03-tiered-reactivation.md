# Tiered reactivation: cooling -> at risk -> dormant

> **In short:** a win-back for players who stopped depositing. Content first, money only if content didn't work, the biggest offer only for players whose return is worth it. A random control group is mandatory. The goal is a deposit within 30 days.

## Workflow in Customer.io

![Workflow: reactivation](../../workflows/03-tiered-reactivation.png)

## Task

Lapsing players are the biggest group CRM can reach, and many of them come back on their own. If 30% of the people we messaged came back, that doesn't mean the campaign brought back 30%: it brought back the difference between them and the control group. A win-back should spend contacts and bonuses only where they change the result.

## Campaign card

| Parameter | Value |
|---|---|
| Type | triggered, on segment entry |
| Entry | last deposit 14-90 days ago (the 14-day point is tuned on the natural return curve) |
| Re-entry | no more than once every 60 days |
| Goal (conversion) | `deposit_made` within 30 days of entry |
| Exit | deposit -> *Priority*; self-exclusion or time-out; RG High; day 45 -> *Low frequency* |
| Priority | below onboarding, second deposit and VIP; above cross-sell |
| Channels | email, push, SMS; VIP manager for high value |
| Holdout | 15% at entry; 25% for high value |
| Owner | CRM; the VIP team handles the high tier |

## Audience, eligibility and exclusions

- **Value tier at entry** (`value_tier`, based on deposits over the previous 90 days): low, medium, high. Thresholds are set from the base distribution, e.g. bottom 50%, next 40%, top 10%.
- **Excluded:** RG High (also an exit condition); players already in the VIP win-back journey, players under Risk/AML review.
- **No bonus steps:** abuse flag, RG Medium (they only get content).
- **Preconditions on every message**, including SMS and push via webhook: `self_excluded != true`, `rg_risk_tier != High`, no active time-out.

## Journey

**Entry and split**

| # | Block | What happens |
|---|---|---|
| 0 | Segment entry | the player moved into *Cooling* (14-90 days without a deposit) |
| 0a | Random split | 85% - journey, 15% - control (75/25 for high value); group written to `winback_group` |
| 0b | Control | gets nothing for 45 days, deposits counted the same way |
| 0c | Branch by `value_tier` | low / medium / high |

**Steps by tier**

| Day | Low value | Medium value | High value |
|---|---|---|---|
| 0 | Email: personal game content (new releases in their favourite category) | Email: "how are you doing?" + personal content | Task for the VIP manager; personal email from the manager |
| 3 | Email: game recommendation | Email: game recommendation | Call or message from the manager |
| 7 | - | Push: no-deposit free spins with a win cap | Free spins agreed by the manager |
| 10 | - | Email: personal reload, 48 h expiry, terms next to it | Personal offer from the manager |
| 14 | - | SMS: last nudge | Manager follows up |
| 21 | Email: new releases digest | Email: game challenge (gamification) | Manager leads |
| 30 | - | Email: "we miss you" + a stronger offer if the previous ones didn't work | Manager leads |
| 35 | - | SMS or push: last contact, different format | - |
| 45 | Exit -> *Low frequency* | Exit -> *Low frequency* | Manager review: keep personal contact or move to *Low frequency* |

Each step is sent only if the player still hasn't deposited and passes the preconditions. If RG risk goes up to High mid-journey, the next step isn't sent and the player exits.

## Offers

- **Free spins instead of cashback.** Free spins give a small, limited reason to try a game again. Cashback returns part of the losses, and that can push people to chase them.
- **Step by step.** The incentive grows only if the cheap step didn't work.
- **Offer size** is chosen by a test. By default the cheapest option that works; a bigger one for more valuable players.
- **Low value** gets content only: a bonus there costs more than the returning player brings in.

## Measurement

| Metric | What it shows |
|---|---|
| **Primary:** deposit within 30 days, test vs control, in percentage points | the real effect of the journey |
| The same on day 7 and day 14 | how fast the effect builds up |
| Incremental NGR per test group player minus channel cost | whether the journey pays off |
| Deposits over 60 days after returning | whether the player stayed or came for one offer |
| Bonus cost per incremental return | the price of the result |
| **Guardrails:** unsubscribes, spam complaints, RG risk changes | the cost for the base and for the player |
