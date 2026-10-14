---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete beside a kiosk and confirms
  kind: actor
  actor: user
  entities:
  - {entity: kiosk, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'dashboard::location-dashboard::kiosks'}
- text: The Product deletes the Kiosk
  kind: product
  actor: user
  entities:
  - {entity: kiosk, effect: removes, from: Active}
  contexts:
    web: {place: 'dashboard::location-dashboard::kiosks'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_session}
---

# Delete a kiosk

## Trigger

A computer is retired.

## Outcome

The computer no longer works as a kiosk; periods it recorded keep their kiosk.
