---
kind: primary
routes:
  web: Web
steps:
- text: The Super user opens a user, changes the email, Super, Dev or Enabled settings and saves
  kind: actor
  actor: super-user
  entities:
  - {entity: user, effect: reads, facts: [Email, Super user, Developer, Enabled]}
  contexts:
    web: {place: 'dashboard::administration::user'}
- text: The Product saves the User
  kind: product
  actor: super-user
  entities:
  - {entity: user, effect: changes, facts: [Email, Super user, Developer, Enabled]}
  contexts:
    web: {place: 'dashboard::administration::user'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_user}
---

# Change a user's sign-in details

## Trigger

A user's address changes or they leave.

## Outcome

A disabled user can no longer sign in by any means until enabled again.
