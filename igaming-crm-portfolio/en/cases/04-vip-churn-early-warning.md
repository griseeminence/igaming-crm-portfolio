# Case 04 - VIP players are leaving

> **In short:** I compare each VIP with their own usual rhythm, spot the slowdown early and pass the signal to the manager for a service call. A bonus only if the call didn't help.

## Situation
*Made-up numbers for the exercise.*

- Around 250 active VIPs (deposits from €2,500 over 90 days).
- Right now the alert fires when a VIP hasn't deposited for 14 days.
- By then many players have already moved to a competitor, and the call looks like an attempt to catch up.
- The VIP team can make about 25-30 personal contacts a week.

## How I approach it

I compare each VIP with their own behaviour - not with general metrics, because there's a risk of getting an irrelevant result.

## Signals

| Signal | What it compares | Why |
|---|---|---|
| Deposit frequency | deposits in the last 14 days vs the 28 days before | slows down first |
| Activity | active days in the last 14 days vs the 28 days before | some players keep logging in but stop depositing, others the other way round |
| Stake | stakes in the last 14 days vs the 28 days before | stakes get smaller before players leave |
| "Overdue" ratio | days since last deposit ÷ the player's usual gap between deposits | 2 means the player has missed roughly one usual deposit |

A simple score, 0-6 points:

| Condition | Points |
|---|---|
| Deposit frequency below half of normal | 2 |
| Activity below half of normal | 1 |
| Stake below half of normal | 1 |
| Overdue ratio above 2 | 2 |

High risk - 4 points or more.

## How I would check the score before launch

Take weekly snapshots from past months. On each snapshot, calculate the triggers using only data up to that day, then look at who actually stopped depositing in the next 30 days.

Then I compare the score with the 14-day rule on three things:
- **precision:** how many of the flagged VIPs actually left;
- **recall:** how many of the VIPs who left were flagged;
- **lead time:** how many days earlier the score fired.

**What I expect:** the score fires earlier and catches more of the leavers, but with more false alarms; the 14-day rule is more precise but late. That trade-off is fine here because the action is cheap.

## What I would do

1. **Score ≥ 4 -> host contact within 48 hours.** Service, asking how things are going, a relevant event or game. **No bonus.** It's cheap.
2. **14 days without a deposit -> win-back journey.** A personal offer, but only after an RG and AML check.
3. **RG check before any action.**

## How I would measure it
A 50/50 test among high-risk VIPs: host call vs no call. Primary KPI - deposit within 30 days. Secondary - 60-day NGR per VIP.
