---
kind: primary
routes:
  web: Web
steps:
- text: The Guest finds their name among the guests signed in and chooses Sign out
  kind: actor
  actor: guest
  entities:
  - {entity: guest-period, effect: reads, facts: [Guest name, Start time]}
  contexts:
    web: {place: 'kiosk::enrolled::guests'}
- text: The Product closes the Guest period at this Kiosk
  kind: product
  actor: guest
  entities:
  - {entity: guest-period, effect: changes, from: Signed in, to: Signed out, facts: [End time, Signed out at]}
  - {entity: kiosk, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::enrolled::guests'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_guest_sign_out}
---

# Sign out a guest from the list

## Trigger

A visitor leaves.

## Outcome

The guest period is closed and the guest drops off the lists of who is here.

## Edge cases

- A guest already signed out, or whose entry was deleted, cannot be signed out again.
