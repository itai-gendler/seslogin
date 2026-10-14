---
kind: validation
routes:
  web: Web
steps:
- text: The Member sets a sign-out time before the sign-in time and submits
  kind: actor
  actor: member
  entities: []
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
- text: The Product refuses and keeps the sign-out screen open
  kind: condition
  entities:
  - {entity: period, effect: reads, facts: [Start time]}
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_sign_out}
---

# Give a sign-out time before the sign-in time

## Trigger

The member mis-set a time.

## Outcome

The period stays open until the member gives a valid pair of times.
