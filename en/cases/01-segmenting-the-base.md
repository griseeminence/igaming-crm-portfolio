# Case 01 - The CRM team sends everyone the same promo. Segment the base

> **In short:** score every depositor on recency, frequency and amount. Then group them into a few segments the team can actually work with. Then give each segment its own goal, incentive policy and guardrail metric - so bonus money goes exactly where it can change player behaviour.

## Situation
*Made-up numbers for the exercise, not real data.*

- Online casino, around 10,000 depositors over the last year.
- Every Friday all recent depositors get the same reload bonus: 50% up to €50.
- We've heard that roughly 5% of players bring in about three quarters of NGR, and bonus cost keeps growing.
- The Head of CRM wants a segmentation the team can really use.

## How I approach it

First of all we decide what decision the segmentation has to support: *who should get which contact and which incentive.*

In this case there should be only a few segments, they should be stable over time, clear to the team and tied to an action.

RFM works for this: Recency, Frequency, Monetary.

Platforms like Optimove already have similar logic built in: first the lifecycle stage, and inside it a split by behaviour and value.

## Method

| Dimension | Question | Score |
|---|---|---|
| **R**ecency | How long since the last deposit? | business thresholds: ≤7 days -> 5, ≤30 -> 4, ≤60 -> 3, ≤120 -> 2, more -> 1 |
| **F**requency | How many deposits in the last 180 days? | thresholds: 20+ -> 5, 8+ -> 4, 4+ -> 3, 2+ -> 2, 1 -> 1 |
| **M**onetary | How much deposited in 180 days? | quintiles |

**Why thresholds for R and F, not quintiles.** Classic RFM splits the base into five equal groups. That breaks when many players have the same value: thousands of players with exactly one deposit get randomly cut into different scores. Business thresholds are stable, easy to explain ("no deposit for 30 days") and match the way CRM rules are written. For M, where values are widely spread, quintiles work fine.

**Why M on deposits, not on NGR.** NGR depends on luck: a player who just won big has negative NGR for the period, even if they're a valuable customer. Deposits reflect intent and budget. I look at NGR separately, next to the segments, and don't put it into the score. Two players with deposits of €50 and €5,000 need a completely different approach.

## What I would do with each segment

| Segment | Who | Goal | What we do | Guardrail |
|---|---|---|---|---|
| Champions | recent and frequent | protect, recognise | service, early access, VIP contact; **no blanket bonuses** | any reward only through a holdout |
| Loyal | frequent, slightly "less recent" | increase frequency | personal content; cheap rewards only after a test | early warning on slowdown |
| Potential loyalists | recent, medium frequency | build a habit | missions, streaks, game recommendations | no more than one promo a week |
| New / promising | first deposits | second deposit | post-FTD journey | no promos before KYC |
| Need attention / about to sleep | starting to cool down | don't let them go | content first, a light offer if content didn't work | exclude high RG risk |
| At risk | used to be frequent, now quiet | win back value | personal offer with a deadline, medium and high value only | mandatory holdout |
| Can't lose them | used to be very frequent, gone quiet | personal win-back | host call, individual offer after RG/AML check | compliance first |
| Hibernating, lost | long ago and rarely | cheap reactivation or goodbye | automated content, no SMS | protect email sender reputation |

## What I expect to see and why it matters
As a rule, a small group of frequent players brings in most of the NGR. If that's the case, two things follow:
1. **Protecting Champions matters more than any mass promo.** Losing a few of them costs more than a mass campaign brings in.
2. **The Friday reload is probably paying the wrong people.** Champions deposit on Fridays anyway, and Lost players don't react to €50. The bonus mostly lands where it changes nothing.

I'd also count players with negative lifetime NGR, i.e. those who got more back in wins and bonuses than they lost. With blanket bonuses this group usually grows.

## How I would measure it
The value of segmentation shows up in tests: segment-based vs blanket, with a random holdout in each.
For the Friday reload, the first thing I'd run is a "reload vs no reload" test among Champions. If deposits don't drop, the savings start straight away.
