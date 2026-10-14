---
kind: alternative
routes:
  web: Web
steps:
- text: The User scans the QR code of a computer that was a kiosk, and saves it for a location and name
  kind: actor
  actor: user
  entities:
  - {entity: kiosk, as: earlier, effect: reads, facts: [Device key]}
  - {entity: location, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'dashboard::location-dashboard::enroll-kiosk'}
- text: The Product releases the computer from its earlier Kiosk, wherever that kiosk is
  kind: product
  actor: user
  entities:
  - {entity: kiosk, as: earlier, effect: changes, from: Active, to: Replaced, facts: [Device key]}
  contexts:
    web: {place: 'dashboard::location-dashboard::enroll-kiosk'}
- text: The Product creates the new Kiosk bound to the computer's key
  kind: product
  actor: user
  entities:
  - {entity: kiosk, as: new, effect: creates, to: Active, facts: [Name, Mode, Guests, Quick pick categories, Who's here, Device key, Expires]}
  contexts:
    web: {place: 'dashboard::location-dashboard::enroll-kiosk'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#enroll_session}
---

# Enroll a computer that is already a kiosk

## Trigger

A kiosk was set up as the wrong kiosk or at the wrong location.

## Outcome

The computer works as the new kiosk; the earlier entry stays listed as replaced at its own location.

## Edge cases

- The user is told nothing about the earlier kiosk, which may belong to a location they cannot see.
