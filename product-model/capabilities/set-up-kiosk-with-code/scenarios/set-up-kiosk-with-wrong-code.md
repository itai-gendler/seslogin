---
kind: validation
routes:
  web: Web
steps:
- text: The User enters a code that is wrong, already used or belongs to a deleted kiosk
  kind: actor
  actor: user
  entities:
  - {entity: kiosk, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::setup::kiosk-setup'}
- text: The Product refuses and the computer stays a setup screen
  kind: condition
  entities:
  - {entity: kiosk, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::setup::kiosk-setup'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#auth_session}
---

# Enter a code that does not set up a kiosk

## Trigger

The code was mistyped or has already been used.

## Outcome

Nothing is set up; the computer still asks for a code.
