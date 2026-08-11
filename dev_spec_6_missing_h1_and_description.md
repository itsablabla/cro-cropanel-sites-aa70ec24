# Missing H1 and description — dev spec
Site: allbirds.com · Priority 6 · High · Effort: Medium (2-5 days)

## Problem
The Shop All page has no H1 or meta description, leaving visitors without context and hurting SEO and clarity.

## Evidence (from the live site)
> H1 count is 0 on /collections/shop-all-26; meta_description is null; body starts with 'SHOP ALL '26' as a title but it's not an H1.

## Current state
cta: Apply filters; notes: The page title 'SHOP ALL '26' is present but not marked as H1; no descriptive text to help visitors understand the range.

## Required change
h1: Shop All Shoes & Apparel; cta: Apply filters; notes: Add a meta description and a short intro: 'Explore our full collection of comfortable, sustainable shoes and apparel for men and women.' This improves clarity and SEO.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a meta description and a short intro: 'Explore our full collection of comfortable, sustainable shoes and apparel for men and women.' This improves clarity and SEO.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_missing_h1_and_description` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
