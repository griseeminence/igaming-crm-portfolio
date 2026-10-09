# Case 02 - Retention dropped

> **In short:** It's worth checking the CRM journeys. But before touching them, check whether the players themselves have changed. A drop in an overall metric often means the traffic mix has shifted.

## Situation
*Made-up numbers for the exercise.*

- M1 retention (share of a month's new depositors who play again on days 30-59) was around 50% for the March-April cohorts and 47% for the May-July cohorts.
- The onboarding journey hasn't changed since March.
- In May marketing launched a big campaign.
- The Head of CRM asks: why has our onboarding stopped working?

## How I approach it

Retention can drop because the product got worse, payments broke, the journey stopped firing or different people came in. CRM is only one of these causes. I go through them in order and start with the cheapest check: who are our new players?

**Step 1. Make sure the drop is real.** If you compare the July cohort with March before everyone has reached day 59, the "drop" is just missing time. We compare only complete cohorts.

**Step 2. Split by acquisition channel.** Let's say I see:

| Channel | Share of new depositors, Mar-Apr | Share, May-Jul | M1, Mar-Apr | M1, May-Jul |
|---|---|---|---|---|
| Paid social | 7% | 20% | 30% | 31% |
| All other channels | 93% | 80% | 51% | 51% |

Within channels retention barely moved. The mix changed: a low-retention channel grew from 7% to 20% of new players.

**Step 3. Decompose the change.**
- *Mix* = Σ (new share - old share) × old retention: what would have happened if only the shares had changed.
- *Rate* = Σ old share × (new retention - old retention): what would have happened if only retention within channels had changed.

In this example almost all of the drop (around 2.5 points) is the mix effect.

**Step 4. Standardise.** Recalculate each month's retention as if the channel shares had stayed at the March-April level. If that line is flat, the journey is fine.

## What I would do
1. **Give paid social players their own onboarding:** a lighter first session, more product content in the first week, same bonus. Low-intent traffic that gets offered more money turns into bonus hunting.
2. **A joint decision with the marketing team.** Paid social should be judged on M1 and 90-day NGR per player. Cost per first deposit says little here: a cheap FTD that never comes back isn't actually cheap.

## If it's not the mix
Then we look further: failed payments and declined deposits, KYC issues, product outages, welcome offer changes, whether the journey is actually being sent (deliverability, broken triggers) and seasonality (the end of a big football tournament shifts sports retention every time).

## How I would measure the fix
The paid social track goes into a 50/50 test against the current journey, among paid social players only. Primary KPI: M1 retention. Secondary: 30-day NGR per player.
