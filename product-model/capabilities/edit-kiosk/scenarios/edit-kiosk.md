---
kind: primary
routes:
  web: Web
steps:
- text: The User opens a kiosk, changes its name, mode or options and saves
  kind: actor
  actor: user
  entities:
  - {entity: kiosk, effect: reads, facts: [Name, Mode, Guests, Quick pick categories, Who's here, Health check URL, Diagnostics]}
  contexts:
    web: {place: 'dashboard::location-dashboard::kiosk'}
- text: The Product saves the Kiosk's settings, which the kiosk picks up
  kind: product
  actor: user
  entities:
  - {entity: kiosk, effect: changes, facts: [Name, Mode, Guests, Quick pick categories, Who's here, Health check URL]}
  contexts:
    web: {place: 'dashboard::location-dashboard::kiosk'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_session}
- {kind: code, role: implementation, target: web/src/admin/components/SessionForm.tsx}
---

# Change a kiosk's settings

## Trigger

A unit wants guests signed in, or a second screen showing who is here.

## Outcome

The kiosk behaves according to its new settings.
