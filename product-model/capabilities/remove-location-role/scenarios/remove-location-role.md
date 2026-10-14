---
kind: primary
routes:
  web: Web
steps:
- text: The Super user removes a Location from a user and saves
  kind: actor
  actor: super-user
  entities:
  - {entity: location-role, effect: reads, facts: [Role]}
  - {entity: location, effect: reads, facts: [Name]}
  - {entity: user, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::administration::user'}
- text: The Product removes the Location role
  kind: product
  actor: super-user
  entities:
  - {entity: location-role, effect: removes}
  contexts:
    web: {place: 'dashboard::administration::user'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_user}
---

# Take away a user's role at a location

## Trigger

A user no longer helps a unit.

## Outcome

The user no longer reaches that location.
