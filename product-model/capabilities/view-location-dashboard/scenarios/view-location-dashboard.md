---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Home for one of their locations
  kind: actor
  actor: user
  entities:
  - {entity: location, effect: reads, facts: [Name, Last successful member sync]}
  - {entity: period, effect: reads, facts: [Start time, End time, Category]}
  - {entity: kiosk, effect: reads, facts: [Last contact]}
  contexts:
    web: {place: 'dashboard::location-dashboard::home'}
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs#dashboard_summary}
- {kind: code, role: implementation, target: web/src/admin/pages/AdminHome.tsx}
---

# Open the location's home page

## Trigger

A user wants a quick view of the unit.

## Outcome

The user sees the location's activity at a glance, with virtual time counted separately where it applies.
