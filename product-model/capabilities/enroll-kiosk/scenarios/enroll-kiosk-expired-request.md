---
kind: validation
routes:
  web: Web
steps:
- text: The User opens the enrollment page from a QR code the computer no longer shows
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'dashboard::location-dashboard::enroll-kiosk'}
- text: The Product says the request has expired and asks for a rescan
  kind: condition
  entities:
  - {entity: kiosk, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::enroll-kiosk'}
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs#pending_enrollment_key}
---

# Scan a QR code that is no longer waiting

## Trigger

The computer was switched off or the scan is old.

## Outcome

No kiosk is created.
