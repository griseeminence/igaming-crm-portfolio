# Playbook - six lifecycle campaigns and their journeys

This is my working iGaming CRM playbook: six campaigns that take a player from sign-up to VIP. Each document combines a brief (why the campaign exists, who it's for, how we measure it) and a detailed journey: steps, timings, channels, conditions, branches and handing the player on.

## Six campaigns

| # | Campaign | Player stage | Primary KPI |
|---|---|---|---|
| 1 | [Onboarding: sign-up -> first deposit](01-onboarding-to-ftd.md) | new registration | FTD within 7 days |
| 2 | [First deposit -> second](02-post-ftd-second-deposit.md) | new depositor | second deposit (STD) within 7 days |
| 3 | [Tiered reactivation](03-tiered-reactivation.md) | cooling / at risk / dormant | deposit within 30 days vs control |
| 4 | [Event-driven VIP cycle](04-event-driven-vip.md) | VIP | VIP retention, NGR per VIP |
| 5 | [Failed deposit recovery](05-failed-deposit-recovery.md) | anyone whose payment failed | successful deposit within 24 h |
| 6 | [Cross-sell: sports -> casino](06-sportsbook-to-casino-cross-sell.md) | sports-only player | first casino bet within 14 days |

## How the campaigns connect

No journey ends in a dead end: the player either reaches the goal and moves to the next stage, or goes into a cheaper, rarer flow.

| From | Event | To |
|---|---|---|
| Sign-up | `signup` | Onboarding |
| Onboarding | first deposit (`ftd_completed`) | Second deposit |
| Onboarding | 7 days without a deposit | *Sleepers* (rare content newsletter) |
| Any campaign | `deposit_failed` and no successful deposit within 30 min | Failed deposit, the original campaign carries on |
| Second deposit | second deposit | *Priority* (active players, normal communication) |
| Second deposit | 7 days without a deposit | *Cooling*; into "Reactivation" once 14 days have passed since the last deposit |
| Active player (non-VIP) | 14 days without a deposit (the exact point is tuned on the natural return curve) | Reactivation |
| Reactivation | deposit | *Priority* |
| Reactivation | 45 days in the journey without a deposit | *Low frequency* (once a month or quarter) |
| Any | reached the VIP threshold | VIP cycle |
| Active sports-only player | cross-sell conditions met | Cross-sell |

**States the journeys refer to:**
- *Priority* - active depositors, get normal product communication;
- *Cooling* - players who have started to cool down, the entry into reactivation;
- *Sleepers* - registered but never deposited; rare content, no bonuses;
- *Low frequency* - long-lapsed depositors; one send a month or a quarter.

## Shared rules for all campaigns

### 1. Eligibility for contact, always in this order
1. **Can we message them?** No self-exclusion and no active time-out. There's consent for this product (casino or sports) and this channel. The product is available in the player's jurisdiction.
2. **Should we?** RG risk isn't High. At Medium, no deposit-linked offers and no urgency. A bonus abuse flag means content only. An open fraud or AML review means zero promos.
3. **Journey rules.** Exit on the goal event. Only one promo journey at a time. A shared frequency cap across all campaigns.

RG and self-exclusion checks sit **on every promo message**.

### 2. Priority when a player qualifies for several campaigns
compliance and service -> failed deposit -> VIP -> onboarding / second deposit -> reactivation -> cross-sell.

Service and transactional messages don't count towards frequency caps and aren't blocked by promo journeys.

### 3. Frequency and send times
- no more than 1 promo message a day and 4 a week per player across all channels;
- SMS no more than once a week, only with separate consent;
- push and SMS only during the day in the player's local time (e.g. 09:00-21:00, or stricter if the market requires it);
- one message idea - one channel, no duplicates on the same day;
- in-app prompts that the player only sees during their own session don't count towards the cap.

### 4. Offers
- One product per incentive: a casino bonus or a sports free bet, not a combined one.
- Key terms (wagering, expiry, max bet, win cap) sit right next to the offer.
- No bonus for: RG High (and at Medium no deposit-linked offers), abuse flag, players under review, players right after a failed deposit.

### 5. Measurement
- Primary KPI, window and holdout size are fixed **before launch**.
- A random holdout on promo steps (usually 5-15%; more if the group is small or the baseline conversion is low). Everyone gets service and transactional messages.
- Group membership is written to a profile attribute (e.g. `winback_group = control`). Then the test/control comparison can be calculated at any time, regardless of where the player is in the journey.
- Decisions are made on incremental NGR (which already includes bonus cost) minus channel cost.
- I read results on day 7 and day 30: that shows whether the campaign creates player actions or only speeds up ones that would have happened anyway.
- If the audience is small (VIPs, failed deposits), results are accumulated over a quarter: a month doesn't give enough data.

### 6. Launch and monitoring
Before each campaign goes live:
1. Run test profiles through every branch: verified / not, with bonus / without, RG Low / Medium / High, self-excluded, no SMS consent.
2. Check that the goal exit actually works and a player doesn't get "make a deposit" after depositing.
3. Check personalisation with empty fields (name, favourite game): every field needs a default value.
4. Send all messages to an internal test list, check links, UTM tags, mobile rendering.
5. Get copy and offers signed off by compliance.
6. For the first 48 hours watch send volumes, bounces and complaints.

### 7. Who owns what

| Role | Area |
|---|---|
| CRM | journey logic, segments, copy, tests, reporting |
| VIP managers | personal contact with VIPs, decisions on personal offers |
| Responsible gambling / compliance | eligibility rules, RG flags, copy sign-off |
| Risk / AML | reviews, restrictions, source of funds |
| Payments | decline rate, payment methods |
| Analytics | data, attributes, incrementality calculation |

## Channels

| Channel | Best for | Cost and risk |
|---|---|---|
| In-app / on site | prompts during the session, first-week habits | free, only reaches active players |
| Push | short event-based reminders | free, players turn notifications off if overloaded |
| Email | details, personalisation, offer terms | cheap, needs a clean base to stay out of spam |
| SMS | the last nudge for valuable players | paid per message, strict consent requirements |
| VIP manager | relationship, service, win-back | most expensive, VIPs only |

The channel steps up with the stage: while the player is active, in-app and push do the work, email is for details, SMS comes last.

## Data

| Type | Data |
|---|---|
| Events | `signup`, `kyc_verified`, `deposit_made`, `deposit_failed`, `ftd_completed`, `withdrawal_made`, `bonus_granted`, `wagering_completed`, `self_excluded`, `time_out`, `deposit_limit_set`, `kyc_rejected`, `deposit_limit_hit`, `vip_tier_changed`, `vip_risk_tier_changed`, `casino_first_bet` |
| Attributes | `kyc_status`, `ftd_completed`, `deposit_count`, `last_deposit_at`, `last_deposit_status`, `lifecycle_stage`, `rfm_segment`, `vip_tier`, `product_preference`, `rg_risk_tier`, `self_excluded`, `deposit_limit_set`, `bonus_abuse_flag`, `wagering_completed`, `decline_reason` on the `deposit_failed` event, `acquisition_channel`, `first_deposit_amount`, `value_tier`, `vip_risk_tier`, `consent_casino` / `consent_sports`, `under_review`, `days_since_deposit`, `profile_completed`, `open_bets_count` and `next_fav_match_at` |
