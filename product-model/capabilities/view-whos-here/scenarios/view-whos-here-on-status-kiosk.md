---
kind: primary
routes:
  web: Web
steps:
- text: The Member looks at the Status screen
  kind: actor
  actor: member
  entities:
  - {entity: member, effect: reads, facts: [Given name, Surname]}
  - {entity: period, effect: reads, facts: [Start time]}
  - {entity: guest-period, effect: reads, facts: [Guest name, Start time]}
  contexts:
    web: {place: 'kiosk::enrolled::status'}
- text: The list updates as people sign in and out at the Location
  kind: condition
  entities:
  - {entity: location, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::enrolled::status'}
references:
- {kind: code, role: implementation, target: web/src/kiosk/pages/Status.tsx}
- {kind: code, role: implementation, target: web/src/kiosk/components/LivePeriodsProvider.tsx}
---

# Watch who's here on a Status kiosk

## Trigger

A member wants to see who is at the unit.

## Outcome

Everyone signed in at the location is listed with how long they have been there, and a count.
