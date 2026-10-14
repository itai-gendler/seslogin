---
kind: validation
routes:
  web: Web
steps:
- text: The User confirms on their device
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'dashboard::sign-in::login'}
- text: The device's passkey is not one the Product accepts, or its user is disabled
  kind: condition
  entities:
  - {entity: passkey, effect: reads, facts: []}
  - {entity: user, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::sign-in::login'}
- text: The Product refuses and the page offers the emailed code instead
  kind: condition
  entities:
  - {entity: user, effect: reads, facts: [Enabled]}
  contexts:
    web: {place: 'dashboard::sign-in::login'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#finish_passkey_login}
---

# Passkey sign-in fails

## Trigger

The passkey was deleted or the user disabled.

## Outcome

The user is not signed in.
