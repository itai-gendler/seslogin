---
kind: validation
routes:
  web: Web
steps:
- text: The Guest submits the guest dialog with no name, or a name or reason that is too long
  kind: actor
  actor: guest
  entities: []
  contexts:
    web: {place: 'kiosk::enrolled::guests'}
- text: The Product refuses and no Guest period is opened
  kind: condition
  entities:
  - {entity: guest-period, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::enrolled::guests'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_guest_sign_in}
---

# Sign in a guest without a name

## Trigger

The name was left empty.

## Outcome

Nobody is signed in.

## Edge cases

- A name is at most 100 characters and a reason at most 500.
