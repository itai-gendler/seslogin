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
- text: The Member has an open Period at this Location
  kind: condition
  entities:
  - {entity: member, effect: reads, facts: [Member ID]}
  - {entity: period, effect: reads, facts: [Start time]}
  - {entity: location, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
- text: The Member picks a Category from the list
  kind: actor
  actor: member
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
- text: The Member checks the sign-in and sign-out times and submits
  kind: actor
  actor: member
  entities:
  - {entity: period, effect: reads, facts: [Start time]}
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
- text: The Product closes the Period with the category and times at this Kiosk
  kind: product
  actor: member
  entities:
  - {entity: period, effect: changes, from: Signed in, to: Signed out, facts: [End time, Category, Signed out at]}
  - {entity: kiosk, effect: reads, facts: []}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::enrolled::sign-out'}
- text: The scan screen shows the member signed out with their times
  kind: condition
  entities:
  - {entity: period, effect: reads, facts: [Start time, End time]}
  - {entity: member, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::enrolled::scan'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_sign_out}
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanScreenCategories.tsx}
---

# Sign out at a kiosk

## Trigger

A member leaves the unit.

## Outcome

The period is closed with its category; the member drops off every list of who is here.

## Edge cases

- A member may sign in at one kiosk and out at another kiosk of the same location.
- The sign-out can be cancelled before it is submitted; the member stays signed in.
