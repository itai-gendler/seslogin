---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses Remind beside an incomplete period
  kind: actor
  actor: user
  entities:
  - {entity: period, effect: reads, facts: [Start time]}
  contexts:
    web: {place: 'dashboard::location-dashboard::incomplete-periods'}
- text: The Product emails the Member a "Forgot to sign out?" reminder with a link to close the Period
  kind: product
  actor: user
  entities:
  - {entity: member, effect: reads, facts: [Given name, Email]}
  - {entity: period, effect: reads, facts: [Start time, Category]}
  - {entity: location, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'dashboard::location-dashboard::incomplete-periods'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#build_period_still_open_reminder_email}
---

# Remind a member who forgot to sign out

## Trigger

A member is still signed in after leaving.

## Outcome

The member can sign themselves out after the fact.
