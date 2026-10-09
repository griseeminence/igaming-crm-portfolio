# Responsible gambling and bonus abuse

> CRM's first question: "can we message this player?", the second: "should we?", and only the third: "what do we send?"

## Why this is part of a CRM portfolio
CRM controls the audience. If a self-excluded player or a group of abusers got a promo, there's a problem in the workflow, the sends or the logic.

I've done training in AML, KYC and fraud prevention (SumSub, Casino Guru Academy). I use what I learned there in CRM work.

## Part 1. Harm markers

The UK Gambling Commission, in its guidance on customer interaction ([Customer interaction guidance](https://www.gamblingcommission.gov.uk/guidance/customer-interaction-guidance-for-remote-gambling-licensees-formal-guidance)), splits indicators of harm into seven areas. I use them as a checklist because they describe behaviour well:

| Area | Examples of what to look for |
|---|---|
| a. Spend | spend well above the player's own usual level |
| b. Patterns of spend | sharp increases, gambling binges, deposits right after payday |
| c. Time | long sessions, a lot of play at night |
| d. Gambling behaviour | chasing losses, erratic betting, several products at once |
| e. Customer-led contact | complaints about losses, asking for bonuses after losing |
| f. Use of gambling management tools | raising limits, repeated time-outs, past self-exclusion |
| g. Account indicators | repeated failed deposits, many payment methods, reversing withdrawals to keep playing |

### A simple marker score
| Marker | Area | Points |
|---|---|---|
| Deposits doubled vs the player's own recent average (and above a minimum amount) | a/b | 2 |
| Three or more deposits in a day, more than once a month | b/d | 2 |
| A large share of sessions start between midnight and 6 am | c | 1 |
| Session length twice the player's usual | c | 1 |
| Contacted support about losses | e | 3 |
| Raised a deposit limit | f | 2 |
| Repeated time-outs | f | 2 |
| Several failed deposits in a month | g | 1 |
| Reversed a withdrawal | g | 2 |
| Three or more payment methods in a month | g | 1 |

- **High (5+):** promos stop; any interaction is decided by the safer gambling team.
- **Medium (2-4):** no time-limited or deposit-linked offers, lower frequency.
- **Low (<2):** normal mode.

The thresholds are illustrative. In a real company they belong to the safer gambling team and are calibrated on its own cases.

### Why these markers and these weights
- **Reversed withdrawals and many payment methods** say a lot: the player takes back money they'd already decided to withdraw, or is looking for a way round declines and limits.
- **Contact about losses** gets the most points because it's the player telling us directly.
- **Raising a limit** weighs more than setting one. Setting a limit is healthy behaviour; raising it after losses is a sign of risky behaviour.
- **Night play and longer sessions** are weaker on their own, since some people just play late, but they strengthen other signals.

## Part 2. Suppression policy: who we don't message

1. **Self-exclusion** -> no marketing at all.
2. **No consent for this product and channel** -> nothing goes to that channel.
3. **RG risk High** -> promos stop, safer gambling interaction instead.
4. **Bonus abuse flag** -> no bonuses; content is fine.
5. **RG risk Medium** -> no time-limited or deposit-linked offers; no more than one promo a week.
6. **Journey rules** -> exit on conversion, a shared frequency cap across all campaigns, campaign priority.

## Part 3. Bonus abuse

Typical schemes:
- several accounts for the same welcome bonus
- deposit - bonus - minimum wagering - withdrawal
- wagering on games with the lowest house edge
- referral schemes with fake friends
- groups that share devices and cards.

| Signal | Points | Why this weight |
|---|---|---|
| Shared device with another depositor | 1 | Families and couples share devices too |
| Shared payment card or wallet with another depositor | 2 | Much rarer among honest players |
| Withdrew within 72 h of completing bonus wagering, only one or two deposits | 2 | The classic "take it and go" pattern |
| Most casino bets during wagering are on low-edge table games | 1 | Typical of cheap bonus wagering |
| Bonus withdrawal is large relative to own deposits | 1 | The bonus is the main source of gain |
| Active for only a few days | 1 | No interest in the product itself |

- **4+ points:** no bonuses (the account stays open; whether to close it is the fraud team's call).
- **2-3 points:** manual review.
- **Linked accounts:** we link accounts with a shared device or payment method and look at the clusters. Three or more accounts on one card is a much stronger signal than two people on one laptop.

Abuser groups adapt: they change devices, use VPNs and imitate normal play. I'd run new rules in "flag only" mode for a couple of months, compare the flags with the fraud team's decisions, and only then let them block anything.
