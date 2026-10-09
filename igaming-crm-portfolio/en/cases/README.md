# Cases: Solving CRM Problems

Each case starts with a situation (the numbers are made up), then goes through my reasoning, what I would do and how I would measure it.

| # | Case | What it shows |
|---|---|---|
| 01 | [Everyone gets the same promo. Segment the base.](01-segmenting-the-base.md) | RFM, policy per segment, where to spend the bonus budget |
| 02 | [Retention dropped](02-retention-dropped.md) | cohorts, traffic mix |
| 03 | [First-to-second deposit conversion collapsed](03-second-deposit-collapsed.md) | the first week, payments, welcome offer economics |
| 04 | [VIPs are leaving](04-vip-churn-early-warning.md) | early warning signals, precision and recall |
| 05 | [Win-back: how to read a campaign report](05-reading-a-campaign-report.md) | response vs incremental effect, significance, ROI |
| 06 | [Bonus or content? Design the test.](06-bonus-vs-content-test.md) | A/B/n with a control group, cost per incremental result |
| 07 | [Bonus cost +35%, NGR flat](07-bonus-cost-up-ngr-flat.md) | bonus P&L, wagering economics, cannibalisation |
| 08 | [Cross-sell from sports to casino](08-cross-sell-sports-to-casino.md) | product propensity, cannibalisation, RG limits |
| 09 | [Engagement up, revenue down](09-engagement-up-revenue-down.md) | the funnel from click to NGR, the right KPI |
| 10 | [Players get too many messages](10-contact-fatigue.md) | frequency caps, campaign priorities |

## The framework I use for any of them

1. **State the problem precisely.** Not "retention is bad", but "M1 retention of May-July depositors fell from 50% to 47%".
2. **Define who we're talking about.** New players, VIPs, sports, one GEO?
3. **Break it down** by GEO, product, channel, lifecycle stage, value, time.
4. **Rule out causes outside CRM:** payments, KYC, product outages, acquisition, seasonality.
5. **Segment.** "All inactive players" have different reasons and different value.
6. **Check eligibility:** can we message this player, and should we.
7. **Write a hypothesis** that a test can disprove.
8. **Design the intervention:** the smallest one that could work.
9. **Pick the channel** based on the player's stage and how urgent the message is.
10. **Fix the KPI before launch:** one primary metric, a window, guardrail metrics.
11. **Set up a control group.**
12. **Analyse:** is it better than control, by how much, can we trust it, how much money after costs, which segment drove it, can we get the same for less, scale or stop?

## Rules:
- First understand *why*, and only then decide *what to send*.
- First whether we *can* message the player, then whether we *should*, and only then *what* we send.
