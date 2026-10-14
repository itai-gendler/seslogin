---
kind: primary
routes:
  web: Web
steps:
- text: The Super user picks the NITC type and SES tags from those SES offers, and saves
  kind: actor
  actor: super-user
  entities: []
  contexts:
    web: {place: 'dashboard::administration::new-nitc-group'}
- text: The Product adds the NITC group
  kind: product
  actor: super-user
  entities:
  - {entity: nitc-group, effect: creates, facts: [NITC type, SES tags]}
  contexts:
    web: {place: 'dashboard::administration::new-nitc-group'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_nitc_group}
---

# Add an NITC group

## Trigger

A new kind of training is to be exported.

## Outcome

Categories can be put in the group.
