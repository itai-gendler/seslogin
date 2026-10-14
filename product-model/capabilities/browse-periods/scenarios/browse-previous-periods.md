---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Previous periods and filters by name or category
  kind: actor
  actor: user
  entities:
  - {entity: period, effect: reads, facts: [Start time, End time, Category, Comment, Signed in at, Signed out at, NITC export]}
  - {entity: guest-period, effect: reads, facts: [Guest name, Start time, End time, Comment]}
  - {entity: member, effect: reads, facts: [Given name, Surname, Home unit]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityList.tsx}
- {kind: code, role: implementation, target: web/src/admin/components/ActivityListTable.tsx}
---

# Look through previous periods

## Trigger

A user reviews who has been at the unit.

## Outcome

The user sees each period with its member or guest, times, category, kiosks and NITC export state.

## Edge cases

- A user who shows virtual time separately can hide periods in virtual categories.
