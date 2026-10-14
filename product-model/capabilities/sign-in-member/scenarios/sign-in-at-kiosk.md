---
kind: primary
routes:
  web: Web
steps:
- text: The Member enters their member ID on the scan screen
  kind: actor
  actor: member
  entities: []
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
- text: The Product finds the Member by member ID
  kind: product
  actor: member
  entities:
  - {entity: member, effect: reads, facts: [Member ID]}
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
- text: The Member has no open Period at this Location
  kind: condition
  entities:
  - {entity: period, effect: reads, facts: []}
  - {entity: location, effect: reads, facts: []}
  - {entity: member, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
- text: The Product opens a Period for the Member at the Kiosk's Location
  kind: product
  actor: member
  entities:
  - {entity: period, effect: creates, to: Signed in, facts: [Start time, Signed in at]}
  - {entity: kiosk, effect: reads, facts: []}
  - {entity: location, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
- text: The Member sees their name and sign-in time on the scan screen
  kind: actor
  actor: member
  entities:
  - {entity: member, effect: reads, facts: [Given name, Surname]}
  - {entity: period, effect: reads, facts: [Start time]}
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_register2}
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanController.tsx}
---

# Sign in at a kiosk

## Trigger

A member arrives at the unit.

## Outcome

The member is signed in at the location and appears on every kiosk there that shows who is here.

## Edge cases

- The member ID is trimmed before it is looked up.
