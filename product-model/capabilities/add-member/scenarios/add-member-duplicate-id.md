---
kind: validation
routes:
  web: Web
steps:
- text: The User saves a member with a member ID another member already has
  kind: actor
  actor: user
  entities:
  - {entity: member, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::new-member'}
- text: The Product refuses because the member ID is taken
  kind: condition
  entities:
  - {entity: member, effect: reads, facts: [Member ID]}
  contexts:
    web: {place: 'dashboard::location-dashboard::new-member'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#ensure_registration_number_available}
---

# Add a member with a member ID already in use

## Trigger

The person is already on a roster.

## Outcome

No member is added.
