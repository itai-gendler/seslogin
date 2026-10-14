---
kind: primary
routes:
  web: Web
steps:
- text: The Super user opens a category, changes it and saves
  kind: actor
  actor: super-user
  entities:
  - {entity: category, effect: reads, facts: [Name, Enabled, Virtual, NITC group, NITC participant type]}
  contexts:
    web: {place: 'dashboard::administration::category'}
- text: The Product saves the Category
  kind: product
  actor: super-user
  entities:
  - {entity: category, effect: changes, facts: [Name, Enabled, Virtual, NITC group, NITC participant type]}
  contexts:
    web: {place: 'dashboard::administration::category'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_category}
---

# Change a category

## Trigger

A category is retired or starts being exported.

## Outcome

New entries follow the change; existing periods keep their category.
