---
kind: primary
routes:
  web: Web
steps:
- text: The User names the kiosk, chooses its mode and options and saves
  kind: actor
  actor: user
  entities:
  - {entity: location, effect: reads, facts: []}
  - {entity: kiosk, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::new-kiosk'}
- text: The Product creates the Kiosk with a six-digit setup code
  kind: product
  actor: user
  entities:
  - {entity: kiosk, effect: creates, to: Awaiting setup, facts: [Name, Mode, Guests, Quick pick categories, Who's here, Health check URL, Setup code]}
  contexts:
    web: {place: 'dashboard::location-dashboard::new-kiosk'}
- text: The User reads the setup code to enter on the computer
  kind: actor
  actor: user
  entities:
  - {entity: kiosk, effect: reads, facts: [Setup code]}
  contexts:
    web: {place: 'dashboard::location-dashboard::new-kiosk'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_session}
- {kind: code, role: implementation, target: web/src/admin/components/SessionCreatedInterstitial.tsx}
---

# Create a kiosk and get its setup code

## Trigger

A unit has a computer to use as a kiosk.

## Outcome

The kiosk waits for its code to be entered on a computer.
