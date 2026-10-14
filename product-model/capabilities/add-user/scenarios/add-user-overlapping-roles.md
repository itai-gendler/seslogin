---
kind: validation
routes:
  web: Web
steps:
- text: The Super user saves a user who would be both Admin and Read only at one Location
  kind: actor
  actor: super-user
  entities:
  - {entity: location, effect: reads, facts: []}
  - {entity: user, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::administration::new-user'}
- text: The Product refuses
  kind: condition
  entities:
  - {entity: location-role, effect: reads, facts: [Role]}
  contexts:
    web: {place: 'dashboard::administration::new-user'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#validate_user_grants}
---

# Give a user two roles at one location

## Trigger

A location was picked twice.

## Outcome

No user is added.
