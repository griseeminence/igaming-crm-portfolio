# Case 05 - Win-back campaign

> **In short:** I compare the test group with the control group, check that the difference isn't random, and work out whether the extra money covers the bonus cost.

## Situation
*Made-up numbers for the exercise.*

A reactivation campaign ran for 30 days with a 95% / 5% split.

| | Test group | Control group |
|---|---|---|
| Players | 9,500 | 500 |
| Deposited within 30 days | 3,040 | 135 |
| Active (placed a bet) on day 30 | 2,233 | 100 |
| NGR excluding this campaign's bonuses | €220,000 | €10,000 |
| Campaign bonus cost | €24,000 | €0 |

The marketing summary says: "3,040 players reactivated, the campaign brought in €220k".

## How I read it: nine questions in order

**1. Is the test group better than control?**
Deposit rate: 3,040 / 9,500 = **32.0%** vs 135 / 500 = **27.0%**.

**2. By how much?**
+5.0 percentage points in absolute terms; 5 / 27 = **+18.5%** in relative terms.

**3. How many deposits did the campaign actually cause?**
If the test group had behaved like control: 9,500 × 27% = 2,565 depositors. Actual: 3,040. Difference: 3,040 - 2,565 = **475 extra deposits**.

**4. Is it statistically convincing?**
Two-proportion z-test: z ≈ 2.34, **p ≈ 0.02**. At the usual 5% level, unlikely to be chance.
Activity on day 30: 23.5% vs 20.0%, z ≈ 1.81, **p ≈ 0.07**. The direction is positive.

**5. How much money did it bring in?**
Per player: €220,000 / 9,500 = €23.16 vs €10,000 / 500 = €20.00. Expected revenue of the test group without the campaign: 9,500 × €20 = €190,000. **Incremental revenue before bonuses ≈ €30,000.**

But €3 per player could also be noise: revenue per player is widely spread, and the control group has only 500 people. So €30,000 is an estimate, not an exact number.

**6. What did it cost?**
€24,000 in bonuses (plus a bit on channels).

**7. Is the contribution positive?**
€30,000 - €24,000 = **€6,000.** The bonus ate 80% of what the campaign brought in.

**8. What's the ROI?**
(30,000 - 24,000) / 24,000 = **25%**

**9. Can we get the same effect for less?**
That needs one more test: do lapsed players need a bonus, or is content enough?

## My conclusion: rework and scale selectively
There's enough evidence not to shut the campaign down, but not enough to roll it out to everyone. I'd keep the audience logic, the trigger, the multichannel journey and the control group. And I'd change the incentive size, eligibility by value tier, the channel mix and contact frequency.
