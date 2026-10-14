---
kind: primary
routes:
  web: Web
steps:
- text: The Super user opens a location, changes its name, enabled flag or NITC settings and saves
  kind: actor
  actor: super-user
  entities:
  - {entity: location, effect: reads, facts: [Name, Enabled, NITC export from, Complete NITC events on export]}
  contexts:
    web: {place: 'dashboard::administration::location'}
- text: The Product saves the Location
  kind: product
  actor: super-user
  entities:
  - {entity: location, effect: changes, facts: [Name, Enabled, NITC export from, Complete NITC events on export]}
  contexts:
    web: {place: 'dashboard::administration::location'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_location}
---

# Change a location's settings

## Trigger

A unit starts exporting training to NITC.

## Outcome

The location's periods from the export date are exported.
