---
kind: primary
routes:
  web: Web
steps:
- text: The User opens a member added by hand, changes their names or member ID and saves
  kind: actor
  actor: user
  entities:
  - {entity: member, effect: reads, facts: [Given name, Surname, Member ID]}
  contexts:
    web: {place: 'dashboard::location-dashboard::member'}
- text: The Product saves the Member's details
  kind: product
  actor: user
  entities:
  - {entity: member, effect: changes, facts: [Given name, Surname, Member ID]}
  contexts:
    web: {place: 'dashboard::location-dashboard::member'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_person}
---

# Change a member's details

## Trigger

A member's details were entered wrongly.

## Outcome

The member's new details show everywhere, including on their past periods.
