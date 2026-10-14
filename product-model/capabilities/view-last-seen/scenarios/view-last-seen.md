---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Last seen and chooses a time range
  kind: actor
  actor: user
  entities:
  - {entity: member, effect: reads, facts: [Given name, Surname]}
  - {entity: period, effect: reads, facts: [Start time]}
  contexts:
    web: {place: 'dashboard::location-dashboard::last-seen'}
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs#last_period}
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityLastSeen.tsx}
---

# See when members were last seen

## Trigger

A coordinator looks for members who have stopped attending.

## Outcome

The user sees each own member's most recent sign-in at any location and how long ago it was.
