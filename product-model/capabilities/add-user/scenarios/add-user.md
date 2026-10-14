---
kind: primary
routes:
  web: Web
steps:
- text: The Super user enters the email address, whether they are a super user, and a role at each Location, and saves
  kind: actor
  actor: super-user
  entities:
  - {entity: location, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::administration::new-user'}
- text: The Product adds the User with a Location role at each chosen location
  kind: product
  actor: super-user
  entities:
  - {entity: user, effect: creates, facts: [Email, Super user, Enabled]}
  - {entity: location-role, effect: creates, facts: [Role], with: user}
  - {entity: location, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::administration::new-user'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_user}
- {kind: doc, role: intent, target: MANUAL.md}
---

# Add a user with their locations

## Trigger

A unit asks for dashboard access for its coordinators.

## Outcome

The new user can sign in with their email address.
