---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Kiosks
  kind: actor
  actor: user
  entities:
  - {entity: kiosk, effect: reads, facts: [Name, Last contact, Device key, Expires, Diagnostics]}
  contexts:
    web: {place: 'dashboard::location-dashboard::kiosks'}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/SessionsList.tsx}
---

# Check on a location's kiosks

## Trigger

A user checks the unit's kiosks are working.

## Outcome

The user sees each kiosk's health; admins also see unused setup codes.
