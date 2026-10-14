---
kind: validation
routes:
  web: Web
steps:
- text: The User tries to reactivate a kiosk set up with a code, a replaced kiosk, or one whose computer is not showing its QR code
  kind: actor
  actor: user
  entities:
  - {entity: kiosk, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'dashboard::location-dashboard::kiosks'}
- text: The Product refuses and says what to do instead
  kind: condition
  entities:
  - {entity: kiosk, effect: reads, facts: [Device key]}
  contexts:
    web: {place: 'dashboard::location-dashboard::kiosks'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#reactivate_session}
---

# A kiosk that cannot be reactivated

## Trigger

The kiosk is not one that can come back this way.

## Outcome

Nothing changes; a code kiosk has to be set up again from scratch.
