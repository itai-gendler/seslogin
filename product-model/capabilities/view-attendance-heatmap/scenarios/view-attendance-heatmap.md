---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Heatmap and chooses a time range
  kind: actor
  actor: user
  entities:
  - {entity: member, effect: reads, facts: [Given name, Surname]}
  - {entity: period, effect: reads, facts: [Start time, End time]}
  contexts:
    web: {place: 'dashboard::location-dashboard::heatmap'}
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs#period_summary_by_day_by_member}
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityHeatmap.tsx}
---

# Read the attendance heatmap

## Trigger

A coordinator looks for who attends regularly.

## Outcome

The user sees each own member's attendance per day.
