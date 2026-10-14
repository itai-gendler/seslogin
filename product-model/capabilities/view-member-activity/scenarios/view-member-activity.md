---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Activity beside a member
  kind: actor
  actor: user
  entities:
  - {entity: member, effect: reads, facts: [Given name, Surname]}
  - {entity: period, effect: reads, facts: [Start time, End time, Category]}
  - {entity: location, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'dashboard::location-dashboard::member-activity'}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityListMember.tsx}
---

# Look at one member's periods

## Trigger

A user checks a member's attendance.

## Outcome

The user sees the member's periods at their own and other units.
