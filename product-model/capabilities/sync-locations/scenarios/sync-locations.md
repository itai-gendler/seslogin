---
kind: primary
routes:
  web: Web
steps:
- text: The nightly sync of SES units runs
  kind: condition
  unattended: true
  entities: []
  contexts:
    web: {place: 'dashboard::administration::locations'}
- text: The Product adds a Location for each SES unit, headquarters or zone it does not have and renames those whose SES name changed
  kind: product
  entities:
  - {entity: location, as: new, effect: creates, facts: [Name, Enabled, SES headquarters]}
  - {entity: location, as: existing, effect: changes, facts: [Name]}
  contexts:
    web: {place: 'dashboard::administration::locations'}
references:
- {kind: code, role: implementation, target: api/src/location_sync.rs#run}
---

# Bring SES units in as locations

## Trigger

SES opens or renames a unit.

## Outcome

Every SES unit, headquarters and zone has a location named as in SES, with Unit added to a unit's name where it lacks it.
