# Vague hero copy — dev spec
Site: allbirds.com · Priority 2 · Urgent · Effort: Low (0.5-2 days)

## Problem
The hero headline and subhead are generic and don't address the visitor's specific intent, causing them to leave without engaging.

## Evidence (from the live site)
> H1: 'Wildly Comfortable. Super Natural.' CTAs: 'SHOP MEN' and 'SHOP WOMEN' with no subhead visible in the crawl.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: No subhead present; the hero is feature-led and doesn't speak to the visitor's frustration (e.g., finding comfortable, sustainable shoes that fit well).

## Required change
h1: Shoes That Feel Like Nothing. Made From Nature.; cta: Shop Best Sellers; notes: Add a subhead: 'Find your perfect fit with our comfy, sustainable shoes. Free shipping & returns.' This directly addresses comfort and sustainability while guiding to a specific action.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a subhead: 'Find your perfect fit with our comfy, sustainable shoes. Free shipping & returns.' This directly addresses comfort and sustainability while guiding to a specific action.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_vague_hero_copy` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
