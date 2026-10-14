---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses Delete beside a kiosk marked Replaced
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
  - {entity: kiosk, effect: removes, from: Replaced}
  contexts:
    web: {place: 'dashboard::location-dashboard::kiosks'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_session}
---

# Delete a replaced kiosk entry

## Trigger

The record of a replaced kiosk is no longer needed.

## Outcome

The entry is gone.
