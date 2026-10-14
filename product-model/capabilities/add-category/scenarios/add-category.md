---
kind: primary
routes:
  web: Web
steps:
- text: The Super user enters a name, whether it is virtual, and its NITC group and participant type, and saves
  kind: actor
  actor: super-user
  entities:
  - {entity: nitc-group, effect: reads, facts: [NITC type]}
  contexts:
    web: {place: 'dashboard::administration::new-category'}
- text: The Product adds the Category
  kind: product
  actor: super-user
  entities:
  - {entity: category, effect: creates, facts: [Name, Enabled, Virtual, NITC group, NITC participant type]}
  contexts:
    web: {place: 'dashboard::administration::new-category'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_category}
---

# Add a category

## Trigger

A new kind of activity is recognised.

## Outcome

The category can be picked in the dashboard; kiosks offer it once their own list includes it.
