---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the member's given name, surname and member ID and saves
  kind: actor
  actor: user
  entities:
  - {entity: member, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::new-member'}
- text: The Product adds the Member to the Location
  kind: product
  actor: user
  entities:
  - {entity: member, effect: creates, to: Active, facts: [Given name, Surname, Member ID, Home unit]}
  - {entity: location, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::new-member'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_person}
---

# Add a member by hand

## Trigger

Someone joins a unit that is not synced, or before the next sync.

## Outcome

The member can sign in at any kiosk.
