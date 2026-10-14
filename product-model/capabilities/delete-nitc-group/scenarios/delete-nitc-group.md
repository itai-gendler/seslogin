---
kind: primary
routes:
  web: Web
steps:
- text: The Super user deletes an NITC group
  kind: actor
  actor: super-user
  entities:
  - {entity: nitc-group, effect: reads, facts: [NITC type]}
  contexts:
    web: {place: 'dashboard::administration::nitc-group'}
- text: The Product deletes the NITC group
  kind: product
  actor: super-user
  entities:
  - {entity: nitc-group, effect: removes}
  contexts:
    web: {place: 'dashboard::administration::nitc-group'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_nitc_group}
---

# Delete an NITC group

## Trigger

A group is no longer used.

## Outcome

The group is gone.
