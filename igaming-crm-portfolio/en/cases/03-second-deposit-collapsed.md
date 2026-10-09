# Case 03 - First-to-second deposit conversion collapsed

> **In short:** the second deposit is decided in the first week, so I look at what happens in those days, split players by what we know about them at the moment of the first deposit, and close the leak with triggered journeys.

## Situation
*Made-up numbers for the exercise.*

- Last quarter 45% of new depositors made a second deposit within 7 days. This quarter it's 36%.
- The welcome bonus was changed from 100% up to €100 with 35x wagering to 100% up to €200 with 35x wagering.
- Some players complain about declined card payments.

## How I approach it

The second deposit (STD) matters because it's the first proof that the player liked the product enough to pay again. One deposit can be curiosity or an attempt to grab a bonus.

First I check three things: when second deposits usually happen, who exactly doesn't get to the second one, and what changed over the same period.

**When.** The second deposit comes in the first days after the first. If it hasn't happened by day 30, the chances after that are small. So the journey has to work on days 0-7, and any delay in the first messages is expensive.

**Who.** I split new depositors by what we know at the moment of their FTD:
- size of the first deposit (a small first deposit usually means a lower STD rate)
- whether they took the welcome bonus and how far they are with wagering
- product of the first session (casino or sports)
- acquisition channel
- whether there was a failed payment before or after the FTD

**What changed:** Let's assume two options.
1. **The welcome bonus got bigger.** With 35x wagering on €200, many players lose their deposit while trying to wager through the bonus, see there's still a long way to go, and leave. A bigger bonus can also attract more bonus hunters who never planned to come back.
2. **Declined card payments.** A player who tries to make a second deposit and gets declined is lost exactly at the moment they wanted to pay.

## What I would do

1. **Check payments first.** Decline rate by payment method, before and after. If declines went up, it's a payments problem - we start there because it's faster and cheaper.
2. **Launch a failed deposit journey:** trigger `deposit_failed` with no successful deposit within 30 minutes. We give the player: a clear explanation of the decline, other payment methods, support.
3. **Test the welcome offer change.** Old offer vs new, random split at registration. Primary KPI: STD within 7 days and 30-day NGR per depositor.
4. **Segment the post-FTD journey.**
   - Players who placed a bet after the FTD: standard onboarding.
   - Players who deposited but didn't bet within 6 hours: a contextual push and a game recommendation.
   - Small first deposits: a first week focused on content.
   - Large first deposits: a personal welcome from the VIP team instead of a reload.

## How I would measure it
- A permanent 10% holdout on the post-FTD journeys.
- Primary KPI: STD within 7 days. Secondary: STD within 30 days.
- Money: 30-day NGR per player. A few big players shift the average a lot, so I also look at the median.
