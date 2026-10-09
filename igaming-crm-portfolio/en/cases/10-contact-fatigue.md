# Case 10 - Players get too many messages

> **In short:** I count the contact load per player across all campaigns at once, let only one campaign through when they overlap, set a frequency cap and check whether we lose money when there are fewer messages.

## Situation
*Made-up numbers for the exercise.*

- Twelve automated journeys and weekly newsletters run in parallel.
- Some active players get 15-20 messages a week by email, push and SMS.
- Unsubscribes doubled over the quarter, there are more and more spam complaints, and email deliverability is starting to suffer.

## How I approach it

Each journey was designed separately, and each one makes sense on its own. The problem shows up when they stack on the same player.

## What I would look at
- Messages per player per week, by channel and by lifecycle stage.
- Overlaps: how many players are in two or more journeys at the same time.
- Repeats: the same offer in several channels on the same day.
- Response by load level: conversion, unsubscribes and complaints among players who get 1-3, 4-7, 8+ messages a week.

## What I would do
1. **Frequency caps per player across all campaigns** (e.g. a maximum number of promo messages per week and per channel). The exact numbers depend on the product, market and player stage.
2. **A priority order** when a player qualifies for several journeys at once: compliance and service -> failed deposit recovery -> VIP -> onboarding / second deposit -> reactivation -> cross-sell. Only one promo journey at a time.
3. **Channel orchestration:** one message idea - one channel.
4. **Sunset rules:** players who haven't opened anything for 90 days move to a low-frequency list.

## How I would measure it
A 30-day test: the current contact strategy vs reduced load (caps + priorities), random split. I look at deposits, NGR, unsubscribes, complaints and engagement together. If NGR doesn't drop and unsubscribes do, the version with fewer messages wins.
