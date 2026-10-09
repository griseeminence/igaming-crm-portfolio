# Failed deposit recovery

> **In short:** the player has already decided to pay, but the payment didn't go through. They don't need persuading, they need help: explain the reason, offer another payment method, bring in support. No bonuses, and for some decline reasons no messages at all. The goal is a successful deposit within 24 hours.

## Workflow in Customer.io

![Workflow: failed deposit](../../workflows/05-failed-deposit-recovery.png)

## Task

A failed deposit is the most expensive moment in the funnel: the intent is there, but the money didn't arrive. Many people whose first attempt fails never try again. It hits the first deposit hardest, when the player isn't attached to the product yet.

**Hypothesis:** a clear explanation of the reason and an alternative payment method in the first hours after a decline lift the share of successful deposits without any incentive.

## Campaign card

| Parameter | Value |
|---|---|
| Type | triggered, event-based |
| Trigger | `deposit_failed` and no successful deposit within 30 minutes |
| Re-entry | yes, but no more than once every 24 h; after 3 failures within 24 h - no messages, RG/Risk review |
| Goal (conversion) | `deposit_made` within 24 h |
| Exit | successful deposit, self-exclusion or time-out, 72 hours |
| Priority | right after service and compliance messages, above all promos. While the player is here, promo steps of other campaigns pause for 24 h |
| Channels | in-app or push, email, invitation to support chat |
| Holdout | 10% on CRM messages only; the cashier's own retry stays for everyone |
| Owners | CRM (messages), payments (decline rate, payment methods), support (chat) |

## What we do by decline reason

| Reason | What we do |
|---|---|
| Technical error, timeout, provider outage | retry flow: "try again", link to the cashier |
| 3-D Secure failed or interrupted | short guide to confirming the payment in the banking app, retry |
| Bank declined without explanation | other payment methods available in the player's country |
| Method not supported, method limit exceeded | alternatives and limits for each method |
| **Insufficient funds** | **no messages** |
| **Bank blocks gambling payments** | **no messages** and no alternatives |
| **The player's own deposit limit kicked in** | **no messages** |
| **Suspected fraud, AML restriction** | **no messages**, task for Risk |

Repeated failures (3 or more within 24 hours) together with other markers (rising deposit frequency, night sessions) go for an RG review.

## Journey

| # | When | Channel / block | Content | Send condition |
|---|---|---|---|---|
| 0 | event | Filter | `decline_reason` on the "no messages" list -> exit without contact | |
| 1 | +30 min | In-app (if the player is on site) or push | "Payment didn't go through": the reason in plain words, one-tap retry | no successful deposit |
| 2 | +2 h | Email (service) | Other payment methods in their country, their limits and processing times | no deposit |
| 3 | +24 h | Email or chat invitation | "Need help finishing your deposit?" with a direct way into support | no deposit, the player hasn't contacted support on their own |
| 4 | 72 h | Exit | The original campaign (onboarding, second deposit) carries on | |

There are no bonuses at any step. The messages are service by nature and contain no promo.

## Measurement

| Metric | What it shows |
|---|---|
| **Primary:** successful deposit within 24 h of the failure, test vs control | whether the journey works |
| First deposit rate among players whose first attempt failed | contribution to onboarding |
| Support contacts per failure | whether the messages help or create extra load |
| Decline rate by payment method and bank | for the payments team |
| **Guardrails:** zero messages after declines on the "no messages" list; RG risk changes | safety |

- **Design:** 10% holdout on CRM messages only.
- **Volumes are usually small**, so I read results once a quarter.
- **Audit:** once a month a sample of sent messages is checked against `decline_reason`, the target is zero errors.
