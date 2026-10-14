---
kind: alternative
routes:
  web: Web
steps:
- text: The Member enters their member ID away from their home unit
  kind: actor
  actor: member
  entities: []
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
- text: The Product opens a Period for the Member at the Kiosk's Location
  kind: product
  actor: member
  entities:
  - {entity: period, effect: creates, to: Signed in, facts: [Start time, Signed in at]}
  - {entity: kiosk, effect: reads, facts: []}
  - {entity: member, effect: reads, facts: [Home unit]}
  - {entity: location, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_register2}
- {kind: doc, role: intent, target: MANUAL.md}
---

# Sign in at another unit's kiosk

## Trigger

A member visits another unit.

## Outcome

The period is on the visited location's activity and on the member's own activity; their home unit is unchanged.

## Edge cases

- A member still signed in at another location is signed in here as well; each location's period is closed only at that location.
