---
kind: primary
routes:
  web: Web
steps:
- text: The User renames one of their passkeys
  kind: actor
  actor: user
  entities:
  - {entity: passkey, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'dashboard::location-dashboard::passkeys'}
- text: The Product saves the Passkey's new name
  kind: product
  actor: user
  entities:
  - {entity: passkey, effect: changes, facts: [Name]}
  contexts:
    web: {place: 'dashboard::location-dashboard::passkeys'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#rename_passkey}
---

# Rename a passkey

## Trigger

A user wants to tell their passkeys apart.

## Outcome

The passkey shows its new name.
