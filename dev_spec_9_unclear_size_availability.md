# Unclear size availability — dev spec
Site: allbirds.com · Priority 9 · Urgent · Effort: Medium (2-5 days)

## Problem
The product page for Anytime Ankle Sock shows a 'Get Notified' CTA without clear size options, potentially confusing users about availability and blocking immediate purchase.

## Evidence (from the live site)
> The product page CTAs include 'Get Notified' and 'Learn More', but the direct_signals show size_selector: true and add_to_cart: false, indicating the size selector exists but the add-to-cart button is not present, possibly due to out-of-stock or pre-order state.

## Current state
h1: Anytime Ankle Sock; cta: Get Notified; notes: No explicit 'Add to Cart' button; 'Get Notified' suggests item is unavailable, but size selector is present, causing ambiguity.

## Required change
h1: Anytime Ankle Sock; cta: Add to Cart; notes: If the item is in stock, ensure an 'Add to Cart' button is visible. If out of stock, clearly state 'Out of Stock' and provide a 'Notify Me' option, avoiding mixed signals.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN If the item is in stock, ensure an 'Add to Cart' button is visible. If out of stock, clearly state 'Out of Stock' and provide a 'Notify Me' option, avoiding mixed signals.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_unclear_size_availability` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
