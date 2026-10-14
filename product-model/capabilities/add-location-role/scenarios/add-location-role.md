---
kind: primary
routes:
  web: Web
steps:
- text: The Super user adds a Location to a user and picks Admin or Read only, and saves
  kind: actor
  actor: super-user
  entities:
  - {entity: location, effect: reads, facts: [Name]}
  - {entity: user, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'dashboard::administration::user'}
- text: The Product gives the User the Location role
  kind: product
  actor: super-user
  entities:
  - {entity: location-role, effect: creates, facts: [Role]}
  - {entity: user, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::administration::user'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_user}
- {kind: code, role: implementation, target: web/src/admin/components/LocationRolesField.tsx}
---

# Give a user a role at a location

## Trigger

A coordinator starts helping another unit.

## Outcome

The user reaches that location's dashboard.
