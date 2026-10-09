# Cross-sell: sports -> casino

> **In short:** introduce casino to sports players who already show some interest in it, at a moment when they're not busy with a match. Content first, then a small casino-only incentive. The decision is made on the player's total NGR (sports + casino), so we don't mistake moving money around for growth.

## Workflow in Customer.io

![Workflow: cross-sell](../../workflows/06-sportsbook-to-casino-cross-sell.png)

## Task

Players who use both products often look more valuable. But that might only mean that engaged players simply try more things. It doesn't follow from the correlation that pushing casino on a pure bettor will make them more valuable. Cross-sell only makes sense if it creates extra value. If money just moved from sports to casino, we haven't earned anything.

## Campaign card

| Parameter | Value |
|---|---|
| Type | scheduled wave by segment, once a week, on a quiet day |
| Entry | sports only: almost all bets (e.g. 95%+) over 60 days on sports; active in the last 14 days; consent for casino marketing |
| Re-entry | no more than once every 90 days |
| Goal (conversion) | first casino bet (`casino_first_bet`) within 14 days |
| Exit | first casino bet; self-exclusion or time-out; RG risk went up; day 14 |
| Priority | lowest among promo campaigns; doesn't start if the player is in any other promo journey |
| Channels | in-app, email, push |
| Holdout | 20% (baseline conversion is low, so a bigger control is needed) |
| Owner | CRM; the RG team signs off the exclusion criteria |

## Audience, eligibility and exclusions

**Start with the warmest segments:**

| Segment | Expected response | What we do |
|---|---|---|
| Already visited the casino (demo, one session) | highest interest | first wave |
| Bet on sports often, especially live | engaged, fast games might work for them | second wave, if the first one paid off |
| Bet only at weekends, around big events | low interest | leave them alone |
| High-value sports players | careful: core revenue could take a hit | only after results from the first waves and with the VIP team's agreement |

## Journey

| # | When | Channel / block | Content | Send condition |
|---|---|---|---|---|
| 0 | entry | Random split | 80% - journey, 20% - control; group in `xsell_group` | |
| 1 | day 0, quiet moment | In-app | "Discover casino" tile: games close to sports interests (live game shows, fast games) | on site, no open live bets |
| 2 | day 2 | Email | "New to casino?": how the lobby works, demo games, how to set casino limits separately | no casino bet |
| 3 | day 5 | Push | A few casino-only free spins, simple terms, separate from any sports offers | no casino bet, RG Low, no abuse flag |
| 4 | day 14 | Exit | Converted players move to normal communication that takes the new product into account | |

## Offers

- One product per incentive. Free spins are a casino-only offer, with no shared sports and casino bonus.
- The incentive only at step 3, and only for those who didn't try casino after the content.
- Small size and a win cap: the point is to let them try.

## Measurement

| Metric | What it shows |
|---|---|
| **Primary:** first casino bet within 14 days | whether the introduction works |
| **Decision metric:** total NGR per player (sports + casino) over 60 days, test vs control | whether the campaign creates value |
| Sports NGR on its own, test vs control | whether there's cannibalisation |
| **Guardrails:** moves between RG tiers among converted players, opt-outs from casino marketing | harm and annoyance |

- **How to read it:** if casino NGR went up by exactly as much as sports went down, the campaign created nothing.
- **20% holdout**, the decision is made no earlier than 60 days after the wave.
- **Reporting:** conversion by wave weekly, money and RG after 60 days.
