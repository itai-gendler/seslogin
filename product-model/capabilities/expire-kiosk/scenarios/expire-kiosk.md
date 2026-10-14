---
kind: primary
routes:
  web: Web
steps:
- text: Two weeks pass without the Kiosk making contact
  kind: condition
  unattended: true
  entities:
  - {entity: kiosk, effect: reads, facts: [Last contact, Expires]}
  contexts:
    web: {place: 'dashboard::location-dashboard::kiosks'}
- text: The Product stops accepting the Kiosk, which shows as expired
  kind: product
  entities:
  - {entity: kiosk, effect: changes, from: Active, to: Expired, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::kiosks'}
references:
- {kind: code, role: implementation, target: api/src/auth.rs#verify_signed_key}
- {kind: code, role: implementation, target: api/src/session_key.rs}
---

# A kiosk expires after two weeks without contact

## Trigger

A kiosk's computer is switched off or offline.

## Outcome

The kiosk is expired until an admin reactivates it.

## Edge cases

- Every contact pushes the expiry out by another two weeks.
- A kiosk set up with a code also stops working after two weeks without contact, and must be set up again.
