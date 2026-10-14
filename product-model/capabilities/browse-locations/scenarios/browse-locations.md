---
kind: primary
routes:
  web: Web
steps:
- text: The Super user opens Locations
  kind: actor
  actor: super-user
  entities:
  - {entity: location, effect: reads, facts: [Name, Enabled, Last successful member sync, NITC export from]}
  contexts:
    web: {place: 'dashboard::administration::locations'}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/LocationList.tsx}
---

# Look through every location

## Trigger

A super user checks the locations.

## Outcome

The super user sees every location and which ones sync and export.
