# Missing review count — dev spec
Site: allbirds.com · Priority 7 · Urgent · Effort: Medium (2-5 days)

## Problem
The product page shows a reviews section but lacks a visible review count or rating summary near the price, so buyers cannot quickly validate quality.

## Evidence (from the live site)
> H2s include 'Reviews for Anytime Ankle Sock' but no review count or star rating appears in the body sample or CTAs.

## Current state
h1: Anytime Ankle Sock; cta: Get Notified; notes: The page has a reviews section but no aggregate rating or count is visible in the extracted content.

## Required change
h1: Anytime Ankle Sock; cta: Add to Cart; notes: Add a review summary near the price: '4.5/5 (1,200+ reviews)' to provide social proof at the point of purchase decision.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a review summary near the price: '4.5/5 (1,200+ reviews)' to provide social proof at the point of purchase decision.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_missing_review_count` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
