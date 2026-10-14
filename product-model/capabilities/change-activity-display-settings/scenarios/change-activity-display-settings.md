---
kind: primary
routes:
  web: Web
steps:
- text: The User turns showing virtual time separately on or off and saves
  kind: actor
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Disaggregate virtual periods]}
  contexts:
    web: {place: 'dashboard::location-dashboard::activity-display'}
- text: The Product saves the User's choice
  kind: product
  actor: user
  entities:
  - {entity: user, effect: changes, facts: [Disaggregate virtual periods]}
  contexts:
    web: {place: 'dashboard::location-dashboard::activity-display'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_my_disaggregate_virtual_periods}
---

# Show virtual time separately

## Trigger

A coordinator reports on-site and remote time apart.

## Outcome

The user's totals, dashboard and daily email split virtual time out.
