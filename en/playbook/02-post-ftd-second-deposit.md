# First deposit -> second deposit

> **In short:** the first week after the first deposit decides whether the player stays. The journey explains the bonus and wagering, gives a reason to come back without money, and only at the end, and only to those who didn't come back, offers a small reload. The goal is a second deposit (STD) within 7 days.

## Workflow in Customer.io

![Workflow: second deposit](../../workflows/02-post-ftd-second-deposit.png)

## Task

The first deposit can be curiosity or bonus hunting. The second shows that the player liked the product enough to pay again. CRM teams usually treat STD as the earliest reliable sign of a player's future value. If the second deposit doesn't happen in the first days, it rarely happens later.

**Hypothesis:** a clear bonus, a first-week habit and personal recommendations lift STD more than an early reload, and cost less.

## Campaign card

| Parameter | Value |
|---|---|
| Type | triggered, event-based |
| Trigger | `ftd_completed` |
| Re-entry | no |
| Goal (conversion) | `deposit_made` (second deposit) within 7 days |
| Exit | second deposit -> *Priority* (with a thank-you); self-exclusion, time-out or `deposit_limit_hit` -> exit with no messages; 7 days without a deposit -> *Cooling* |
| Priority | same as onboarding: above reactivation and cross-sell |
| Channels | email, in-app, push, SMS (once, at the end) |
| Holdout | permanent 10% at FTD, group stored in `std_group` |
| Owner | CRM; VIP team for large first deposits |

## Audience, eligibility and exclusions

- **Entry:** all new depositors.
- **No deposit-linked offers:** RG risk Medium or High.
- **No bonuses at all:** bonus abuse flag.
- **Exit on `deposit_limit_hit`:** a player who has hit their own limit.

## Journey

| # | When | Channel / block | Content | Send condition |
|---|---|---|---|---|
| 1 | +1 h | Email; push only if the email isn't opened within 4 h | Thanks for the deposit; if a bonus was taken - how wagering works, how much is left, which games count | everyone; bonus block only with `bonus_granted` |
| 1a | +1 h | Message to the VIP manager | Large first deposit: personal welcome within 24 h | `first_deposit_amount` above threshold |
| 2 | day 1 | In-app | First-week mission that doesn't need a deposit (e.g. try three different games) | active on site |
| 3 | day 2 | Branch | `wagering_completed`? | had a bonus |
| 3a | day 2 | Email | Bonus wagered: what to try next (no new offer) | wagering complete |
| 3b | day 2 | Email | Wagering progress: how much is left, how not to lose the bonus | wagering not complete |
| 4 | days 3-4 | Push | Personal game or market recommendation based on the first session | `product_preference` known |
| 5 | day 5 | Email | Most popular this week, new releases | no second deposit |
| 6 | day 6 | SMS or push | Small reload: one product, simple terms | no second deposit, RG Low, no abuse flag, not a large first deposit; for SMS - SMS consent and daytime |
| 7 | by day 7 | Wait for goal | second deposit -> *Priority*; no -> *Cooling*, exit | |

**Thank-you for the second deposit** is a separate small campaign on the `deposit_made` event with `deposit_count = 2`: an in-app "thank you" and, if the player is eligible, a few free spins. It lives separately because the main journey ends at the moment of the deposit.

## Offers

- Reload only on day 6 and only for those who didn't come back. An early reload mostly pays players who would have deposited anyway.
- One product per offer, low wagering, key terms next to it.
- No new bonus for a player who is still wagering the first one.

## Measurement

| Metric | What it shows |
|---|---|
| **Primary:** STD within 7 days | whether the journey works |
| STD within 30 days | if the gap at 30 days is much smaller than at 7, the journey mostly speeds up deposits that would have happened anyway |
| 30-day NGR per player | money after bonuses |
| Bonus cost per new depositor | what the result costs |

- **Design:** permanent 10% holdout at FTD. New versions are tested 50/50 against the current one inside the test group.
- **Revenue per player is skewed by a few big players**, so for money I calculate a bootstrap interval: a single average is easy to be fooled by here.
- **Separate test:** day-6 SMS reload vs no bonus. If STD is the same without it, the reload goes.
- **Reporting:** weekly 7-day STD by FTD cohort; monthly 30-day numbers and incrementality.
