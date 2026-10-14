---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete beside a member added by hand
  kind: actor
  actor: user
  entities:
  - {entity: member, effect: reads, facts: [Given name, Surname]}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
- text: The Product deletes the Member
  kind: product
  actor: user
  entities:
  - {entity: member, effect: changes, from: Active, to: Deleted, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_person}
---

# Delete a member

## Trigger

Someone has left a unit that is not synced.

## Outcome

The member is off the roster; their periods remain.
