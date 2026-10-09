# Case 06 - Testing: do lapsed players need a bonus, or is content enough?

> **In short:** a control group plus several variants (full bonus, smaller bonus, content only) in the same channels. Judged on incremental NGR after bonus cost.

## Situation
*Made-up numbers for the exercise.*

- Around 4,000 players whose last deposit was 60-240 days ago.
- Current reactivation offer: "deposit €20, get a €20 bonus".
- The Head of CRM believes the bonus is necessary.

## How I approach it

There are two separate questions here, and they need different comparisons:
1. **Does contacting these players work at all?** That's each variant compared with a no-contact control group.
2. **Which variant works better for its money?** That's the variants compared with each other.

A lot of tests only compare A with B and never find out that neither is any better than doing nothing.

## Design

| Group | What they get | Share |
|---|---|---|
| Control | nothing | 25% |
| A | 100% deposit match up to €20 | 25% |
| B | 50% deposit match up to €10 | 25% |
| C | personal content, no bonus (games they played, new releases in that category) | 25% |

- **Same channel and timing for all variants** (email + push on day 0, reminder on day 3).
- **Random assignment** before anything is sent.
- **Exclusions before the split:** self-excluded, high RG risk, bonus abuse flags, players with an active bonus.
- **Primary KPI:** deposit within 14 days. **Decision metric:** 30-day incremental NGR per player. Plus bonus cost per *incremental* reactivation.

## What a typical result might look like and how I would decide

| Variant | Reactivation vs control | Bonus cost per incremental reactivation |
|---|---|---|
| A (€20) | highest | highest |
| B (€10) | a bit lower than A | about half of A |
| C (content) | clearly above control, but well below A and B | zero |

If the A vs B difference isn't significant, I wouldn't pay double for an effect I can't prove. By default I'd go with **B for the bulk of low and medium value players**, and A for high value players, where an extra reactivation is worth more. Then I'd rerun A vs B on a bigger sample before locking in the rule.
