---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses Delete beside an incomplete period
  kind: actor
  actor: user
  entities:
  - {entity: period, effect: reads, facts: [Start time]}
  contexts:
    web: {place: 'dashboard::location-dashboard::incomplete-periods'}
- text: The Product deletes the Period
  kind: product
  actor: user
  entities:
  - {entity: period, effect: removes, from: Signed in}
  contexts:
    web: {place: 'dashboard::location-dashboard::incomplete-periods'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_period}
---

# Delete a period that is still signed in

## Trigger

A sign-in was a mistake.

## Outcome

The member drops off the location's kiosks at once.
