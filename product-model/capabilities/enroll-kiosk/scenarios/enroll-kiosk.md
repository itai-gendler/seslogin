---
kind: primary
routes:
  web: Web
steps:
- text: The computer shows its enrollment QR code
  kind: condition
  entities: []
- text: The User scans the QR code with their phone and checks the device key matches the one on the computer
  kind: actor
  actor: user
  entities:
  - {entity: kiosk, effect: reads, facts: [Device key]}
  contexts:
    web: {place: 'dashboard::location-dashboard::enroll-kiosk'}
- text: The User chooses the Location, names the kiosk, chooses its mode and options and saves
  kind: actor
  actor: user
  entities:
  - {entity: location, effect: reads, facts: [Name]}
  - {entity: kiosk, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::enroll-kiosk'}
- text: The Product creates the Kiosk bound to the computer's key, expiring after two weeks without contact
  kind: product
  actor: user
  entities:
  - {entity: kiosk, effect: creates, to: Active, facts: [Name, Mode, Guests, Quick pick categories, Who's here, Device key, Expires]}
  contexts:
    web: {place: 'dashboard::location-dashboard::enroll-kiosk'}
- text: The computer switches to its kiosk screen within a few seconds
  kind: condition
  entities:
  - {entity: kiosk, effect: reads, facts: []}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#enroll_session}
- {kind: code, role: implementation, target: web/src/enroll/SessionEnroll.tsx}
- {kind: code, role: implementation, target: web/src/kiosk/components/KioskEnrollment.tsx}
---

# Enroll a kiosk by scanning its QR code

## Trigger

A unit sets up a kiosk without typing a code on it.

## Outcome

The computer is the location's kiosk.
