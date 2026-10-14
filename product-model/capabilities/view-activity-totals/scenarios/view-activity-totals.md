---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Totals and chooses a time range
  kind: actor
  actor: user
  entities:
  - {entity: member, effect: reads, facts: [Given name, Surname]}
  - {entity: category, effect: reads, facts: [Name, Virtual]}
  - {entity: period, effect: reads, facts: [Start time, End time]}
  contexts:
    web: {place: 'dashboard::location-dashboard::totals'}
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs#period_summary_by_member}
- {kind: code, role: implementation, target: web/src/admin/components/ActivityTotalsDisplay.tsx}
---

# Read the totals for a range

## Trigger

A coordinator needs hours for a period of time.

## Outcome

The user sees time per member and per category; with virtual time shown separately, virtual categories are totalled on their own.
