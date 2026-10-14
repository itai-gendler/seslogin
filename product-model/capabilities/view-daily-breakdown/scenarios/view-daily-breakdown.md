---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Daily breakdown and chooses a time range
  kind: actor
  actor: user
  entities:
  - {entity: member, effect: reads, facts: [Given name, Surname]}
  - {entity: category, effect: reads, facts: [Name]}
  - {entity: period, effect: reads, facts: [Start time, End time]}
  contexts:
    web: {place: 'dashboard::location-dashboard::daily-breakdown'}
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs#period_summary_by_day_by_category_by_member}
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityDailyBreakdown.tsx}
---

# Read the daily breakdown for a range

## Trigger

A coordinator reviews a training weekend day by day.

## Outcome

The user sees each day's categories and who spent time in them.
