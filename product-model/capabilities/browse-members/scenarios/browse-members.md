---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Members and filters by name or member ID
  kind: actor
  actor: user
  entities:
  - {entity: member, effect: reads, facts: [Given name, Surname, Member ID, SES record, Missing from SES since]}
  - {entity: location, effect: reads, facts: [Last successful member sync]}
  contexts:
    web: {place: 'dashboard::location-dashboard::members'}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/MembersList.tsx}
---

# Look through a location's members

## Trigger

A user looks for a member.

## Outcome

The user sees the roster; members visiting from other units are not on it.
