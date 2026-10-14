---
kind: validation
routes:
  web: Web
steps:
- text: The User saves a period whose end is not after its start
  kind: actor
  actor: user
  entities:
  - {entity: period, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::new-period'}
- text: The Product refuses and no Period is recorded
  kind: condition
  actor: user
  entities:
  - {entity: period, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::new-period'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_period}
---

# Record a period that ends before it starts

## Trigger

The times were swapped.

## Outcome

Nothing is recorded.
