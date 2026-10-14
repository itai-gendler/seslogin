---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete beside a period
  kind: actor
  actor: user
  entities:
  - {entity: period, effect: reads, facts: [Start time, End time]}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
- text: The Product deletes the Period
  kind: product
  actor: user
  entities:
  - {entity: period, effect: removes, from: Signed out}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_period}
---

# Delete a period

## Trigger

A period was recorded by mistake.

## Outcome

The period no longer counts anywhere and is withdrawn from the NITC export.
