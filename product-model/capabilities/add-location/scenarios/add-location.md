---
kind: primary
routes:
  web: Web
steps:
- text: The Super user enters a name and, optionally, the date NITC export starts, and saves
  kind: actor
  actor: super-user
  entities: []
  contexts:
    web: {place: 'dashboard::administration::new-location'}
- text: The Product adds the Location
  kind: product
  actor: super-user
  entities:
  - {entity: location, effect: creates, facts: [Name, Enabled, NITC export from]}
  contexts:
    web: {place: 'dashboard::administration::new-location'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_location}
---

# Add a location

## Trigger

A unit not yet synced from SES needs a location.

## Outcome

The location can be given users and kiosks.
