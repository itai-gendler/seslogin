---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to sign in without an email address and confirms on their device
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'dashboard::sign-in::login'}
- text: The Product recognises the Passkey and signs its User in
  kind: product
  actor: user
  entities:
  - {entity: passkey, effect: reads, facts: []}
  - {entity: user, effect: reads, facts: [Enabled]}
  contexts:
    web: {place: 'dashboard::sign-in::login'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#finish_passkey_login}
---

# Sign in with a passkey

## Trigger

A user with a passkey opens the dashboard.

## Outcome

The user is signed in.
