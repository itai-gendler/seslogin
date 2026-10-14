---
kind: primary
routes:
  web: Web
steps:
- text: The User opens the kiosk part of SES Activity on the computer and enters the six-digit setup code
  kind: actor
  actor: user
  entities:
  - {entity: kiosk, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::setup::kiosk-setup'}
- text: The Product sets the Kiosk up on this computer for its location and uses up the code
  kind: product
  actor: user
  entities:
  - {entity: kiosk, effect: changes, from: Awaiting setup, to: Active, facts: [Setup code]}
  - {entity: location, effect: reads, facts: []}
  contexts:
    web: {place: 'kiosk::setup::kiosk-setup'}
- text: The computer shows the kiosk's scan or status screen
  kind: condition
  entities:
  - {entity: kiosk, effect: reads, facts: [Mode]}
  contexts:
    web: {place: 'kiosk::setup::kiosk-setup'}
references:
- {kind: code, role: implementation, target: api/src/auth.rs#issue_token_for_scan_code}
- {kind: code, role: implementation, target: web/src/kiosk/components/KioskSetupForm.tsx}
---

# Set up a kiosk with its setup code

## Trigger

A user has created a kiosk in the dashboard and is at the computer that will be the kiosk.

## Outcome

The computer is the location's kiosk and the setup code no longer works.

## Edge cases

- If the computer stays switched off for two weeks the kiosk has to be set up again from scratch.
