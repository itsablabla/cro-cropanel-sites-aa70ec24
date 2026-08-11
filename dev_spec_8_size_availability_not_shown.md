# Size availability not shown — dev spec
Site: allbirds.com · Priority 8 · Urgent · Effort: Medium (2-5 days)

## Problem
Product pages do not display size availability upfront, forcing users to click through to select a size, which can lead to disappointment and abandonment when their size is out of stock.

## Evidence (from the live site)
> Product page for 'Anytime Ankle Sock' has CTA 'Get Notified' (likely for out-of-stock sizes) and 'Learn More' but no visible size selector or availability indicators in the initial view; size selector is present in the DOM (direct_signals: size_selector: true) but not surfaced in the body sample.

## Current state
h1: Anytime Ankle Sock; cta: Get Notified / Learn More; notes: Size availability is not shown until user interacts with the size selector; out-of-stock sizes may trigger 'Get Notified'.

## Required change
h1: Anytime Ankle Sock; cta: Add to Cart; notes: Display size availability (e.g., checkmarks or 'Low stock' badges) next to each size option to set expectations and reduce friction.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Display size availability (e.g., checkmarks or 'Low stock' badges) next to each size option to set expectations and reduce friction.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_size_availability_not_shown` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
