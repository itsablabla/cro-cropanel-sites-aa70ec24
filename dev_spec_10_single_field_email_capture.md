# Single-field email capture — dev spec
Site: allbirds.com · Priority 10 · High · Effort: Medium (2-5 days)

## Problem
The homepage email signup form asks only for an email address, which is the minimum viable field set, but it lacks a trust layer (e.g., privacy note, incentive) which may increase friction and reduce signups.

## Evidence (from the live site)
> Form on homepage has 1 input, no labels, submit button 'Sign Up'.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Sign Up; notes: Single email field, no visible privacy policy link or incentive mentioned near the form.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Sign Up for 10% Off; notes: Add a clear incentive (e.g., 'Get 10% off your first order') and a privacy note ('We respect your privacy. Unsubscribe anytime.') to reduce friction and increase signup rate.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a clear incentive (e.g., 'Get 10% off your first order') and a privacy note ('We respect your privacy. Unsubscribe anytime.') to reduce friction and increase signup rate.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_single_field_email_capture` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
