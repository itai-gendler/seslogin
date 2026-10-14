---
kind: validation
routes:
  web: Web
steps:
- text: The User saves a member ID another member already has
  kind: actor
  actor: user
  entities:
  - {entity: member, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::member'}
- text: The Product refuses because the member ID is taken
  kind: condition
  entities:
  - {entity: member, effect: reads, facts: [Member ID]}
  contexts:
    web: {place: 'dashboard::location-dashboard::member'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#ensure_registration_number_available}
---

# Change a member ID to one already in use

## Trigger

A typo collides with another member.

## Outcome

The member keeps their details.
