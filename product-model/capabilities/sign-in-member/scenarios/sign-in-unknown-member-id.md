---
kind: validation
routes:
  web: Web
steps:
- text: The Member enters a member ID
  kind: actor
  actor: member
  entities: []
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
- text: No Member has that member ID and the scan screen says so
  kind: condition
  entities:
  - {entity: member, effect: reads, facts: [Member ID]}
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
references:
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanController.tsx}
---

# Enter an unknown member ID

## Trigger

A member mistypes their ID or is not yet on any roster.

## Outcome

Nobody is signed in; the scan screen shows the unknown member ID.

## Edge cases

- A member ID shorter than eight digits is refused at the kiosk before it is looked up.
