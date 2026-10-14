---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes one of their passkeys
  kind: actor
  actor: user
  entities:
  - {entity: passkey, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'dashboard::location-dashboard::passkeys'}
- text: The Product deletes the Passkey
  kind: product
  actor: user
  entities:
  - {entity: passkey, effect: removes}
  contexts:
    web: {place: 'dashboard::location-dashboard::passkeys'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_passkey}
---

# Delete a passkey

## Trigger

A device is lost or replaced.

## Outcome

The passkey no longer signs anyone in.
