# Competing hero CTAs — dev spec
Site: allbirds.com · Priority 1 · Urgent · Effort: Medium (2-5 days)

## Problem
Two primary CTAs in the hero split user focus and dilute the main conversion path.

## Evidence (from the live site)
> Hero section contains both 'SHOP MEN' and 'SHOP WOMEN' CTAs, with no single dominant action.
> H1: 'Wildly Comfortable. Super Natural.' CTAs: 'SHOP MEN' and 'SHOP WOMEN' with no subhead visible in the crawl.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN | SHOP WOMEN; notes: Both CTAs are equally prominent, forcing users to choose a gender before exploring products.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Single primary CTA to browse all products, with secondary gender links in nav.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Single primary CTA to browse all products, with secondary gender links in nav.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_competing_hero_ctas` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
