# Free shipping threshold hidden — dev spec
Site: allbirds.com · Priority 4 · Urgent · Effort: Low (0.5-2 days)

## Problem
The homepage hero promotes 'Wildly Comfortable. Super Natural.' without any mention of the $100 free shipping threshold, which is only disclosed in the sitewide banner and cart, creating an expectation gap for first-time visitors.

## Evidence (from the live site)
> Homepage hero H1: 'Wildly Comfortable. Super Natural.'; sitewide banner: 'Free ground shipping on orders over $100'; cart drawer: 'Spend more to earn free shipping! Shipping $5.00'.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: No mention of shipping threshold or costs on the hero; only in the top banner and cart.

## Required change
h1: Wildly Comfortable. Super Natural. Free Shipping Over $100.; cta: SHOP MEN / SHOP WOMEN; notes: Add a subheading or badge on the hero to set expectations for free shipping threshold, reducing cart abandonment.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a subheading or badge on the hero to set expectations for free shipping threshold, reducing cart abandonment.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_free_shipping_threshold_hidden` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
