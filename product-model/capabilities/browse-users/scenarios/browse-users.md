---
kind: primary
routes:
  web: Web
steps:
- text: The Super user opens Users
  kind: actor
  actor: super-user
  entities:
  - {entity: user, effect: reads, facts: [Email, Last access, Super user]}
  - {entity: location-role, effect: reads, facts: [Role]}
  contexts:
    web: {place: 'dashboard::administration::users'}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/UserList.tsx}
---

# Look through the users

## Trigger

A super user checks who has access.

## Outcome

The super user sees every user.
