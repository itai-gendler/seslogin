---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Add a passkey and confirms on their device
  kind: actor
  actor: user
  entities:
  - {entity: passkey, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::passkeys'}
- text: The Product saves the Passkey for the User
  kind: product
  actor: user
  entities:
  - {entity: passkey, effect: creates, facts: [Name, Added]}
  - {entity: user, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::passkeys'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#finish_passkey_registration}
---

# Add a passkey in settings

## Trigger

A user wants faster sign-in.

## Outcome

The user can sign in with the passkey.
