---
kind: primary
routes:
  web: Web
steps:
- text: The kiosk offers guests
  kind: condition
  entities:
  - {entity: kiosk, effect: reads, facts: [Guests]}
  - {entity: guest, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
- text: The Guest opens the guest dialog and enters their name and, if they like, the reason for the visit
  kind: actor
  actor: guest
  entities: []
  contexts:
    web: {place: 'kiosk::enrolled::guests'}
- text: The Product opens a Guest period at the Kiosk's Location
  kind: product
  actor: guest
  entities:
  - {entity: guest-period, effect: creates, to: Signed in, facts: [Guest name, Comment, Start time, Signed in at]}
  - {entity: location, effect: reads, facts: []}
  - {entity: kiosk, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::enrolled::guests'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_guest_sign_in}
---

# Sign in a guest by name

## Trigger

A visitor arrives at the unit.

## Outcome

The guest is signed in and appears on the lists of who is here.
