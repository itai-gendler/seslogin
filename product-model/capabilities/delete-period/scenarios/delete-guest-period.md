---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses Delete beside a guest's entry
  kind: actor
  actor: user
  entities:
  - {entity: guest-period, effect: reads, facts: [Guest name]}
  - {entity: guest, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
- text: The Product deletes the Guest period
  kind: product
  actor: user
  entities:
  - {entity: guest-period, effect: removes, from: Signed out}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_period}
---

# Delete a guest period

## Trigger

A guest entry was a mistake.

## Outcome

The guest entry is gone.
