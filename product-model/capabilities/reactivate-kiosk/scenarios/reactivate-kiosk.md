---
kind: primary
routes:
  web: Web
steps:
- text: The expired kiosk's computer is switched on and showing its QR code
  kind: condition
  entities:
  - {entity: kiosk, effect: reads, facts: [Expires]}
  contexts:
    web: {place: 'dashboard::location-dashboard::kiosks'}
- text: The User chooses Reactivate beside the kiosk and confirms
  kind: actor
  actor: user
  entities:
  - {entity: kiosk, effect: reads, facts: [Name, Device key]}
  contexts:
    web: {place: 'dashboard::location-dashboard::kiosks'}
- text: The Product reactivates the Kiosk for two more weeks once the computer makes contact
  kind: product
  actor: user
  entities:
  - {entity: kiosk, effect: changes, from: Expired, to: Active, facts: [Expires]}
  contexts:
    web: {place: 'dashboard::location-dashboard::kiosks'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#reactivate_session}
---

# Bring an expired kiosk back

## Trigger

A kiosk sat switched off for more than two weeks.

## Outcome

The kiosk comes back online within a few minutes with the same name and settings.

## Edge cases

- If the computer does not make contact soon after, the reactivation lapses.
