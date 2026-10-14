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
    web: {place: 'dashboard::location-dashboard::period'}
- text: The Product refuses and the Period keeps its times
  kind: condition
  actor: user
  entities:
  - {entity: period, effect: reads, facts: [Start time, End time]}
  contexts:
    web: {place: 'dashboard::location-dashboard::period'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_period_time_category}
---

# Save a period that ends before it starts

## Trigger

The times were swapped.

## Outcome

Nothing changes.
