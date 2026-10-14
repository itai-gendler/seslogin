---
kind: primary
routes:
  web: Web
steps:
- text: The Super user opens an NITC group, changes its type or tags and saves
  kind: actor
  actor: super-user
  entities:
  - {entity: nitc-group, effect: reads, facts: [NITC type, SES tags]}
  contexts:
    web: {place: 'dashboard::administration::nitc-group'}
- text: The Product saves the NITC group
  kind: product
  actor: super-user
  entities:
  - {entity: nitc-group, effect: changes, facts: [NITC type, SES tags]}
  contexts:
    web: {place: 'dashboard::administration::nitc-group'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_nitc_group}
---

# Change an NITC group

## Trigger

SES changes how a kind of training is tagged.

## Outcome

Events exported from then on carry the new type and tags.
