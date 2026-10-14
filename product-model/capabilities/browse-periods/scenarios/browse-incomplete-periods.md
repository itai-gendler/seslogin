---
kind: alternative
routes:
  web: Web
steps:
- text: The User opens Incomplete periods
  kind: actor
  actor: user
  entities:
  - {entity: period, effect: reads, facts: [Start time, Category, Signed in at]}
  - {entity: guest-period, effect: reads, facts: [Guest name, Start time]}
  - {entity: member, effect: reads, facts: [Given name, Surname, Home unit]}
  contexts:
    web: {place: 'dashboard::location-dashboard::incomplete-periods'}
references:
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityCurrent.tsx}
---

# See who is still signed in

## Trigger

A user checks who is at the unit or who forgot to sign out.

## Outcome

The user sees every open period at the location.
