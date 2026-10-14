---
kind: primary
routes:
  web: Web
steps:
- text: The Super user changes a user's role at a Location and saves
  kind: actor
  actor: super-user
  entities:
  - {entity: location-role, effect: reads, facts: [Role]}
  - {entity: location, effect: reads, facts: [Name]}
  - {entity: user, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::administration::user'}
- text: The Product saves the Location role
  kind: product
  actor: super-user
  entities:
  - {entity: location-role, effect: changes, facts: [Role]}
  contexts:
    web: {place: 'dashboard::administration::user'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_user}
---

# Switch a user between Admin and Read only

## Trigger

A user should view but no longer change, or the reverse.

## Outcome

The user's abilities at the location follow the new role.
