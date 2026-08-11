# Shipping delay warning — dev spec
Site: allbirds.com · Priority 3 · Urgent · Effort: Medium (2-5 days)

## Problem
The prominent shipping delay notice undermines the hero's promise of comfort and natural materials, creating an immediate objection about delivery reliability.

## Evidence (from the live site)
> Body sample: 'Due to increased demand, orders may take up to 30 days to ship.'

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: The delay notice appears in the top bar, directly above the hero, and is visible on all pages.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: Replace the delay notice with a trust element: 'Free shipping & free returns' or 'Rated 4.5/5 by 100,000+ customers' to counter the objection.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Replace the delay notice with a trust element: 'Free shipping & free returns' or 'Rated 4.5/5 by 100,000+ customers' to counter the objection.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_shipping_delay_warning` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
