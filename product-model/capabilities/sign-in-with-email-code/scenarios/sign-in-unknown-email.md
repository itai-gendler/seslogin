---
kind: edge
routes:
  web: Web
steps:
- text: The User enters an address that belongs to no user, or to a disabled one
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'dashboard::sign-in::login'}
- text: The Product answers exactly as for a real address but sends no code
  kind: condition
  entities:
  - {entity: user, effect: reads, facts: [Enabled]}
  contexts:
    web: {place: 'dashboard::sign-in::login'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#request_auth_code}
---

# Ask for a code for an address that cannot sign in

## Trigger

Someone without dashboard access tries to sign in.

## Outcome

No code is sent and the page does not reveal whether the address is known.
