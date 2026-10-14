---
kind: primary
routes:
  web: Web
steps:
- text: The User opens Breakdown and chooses a time range
  kind: actor
  actor: user
  entities:
  - {entity: member, effect: reads, facts: [Given name, Surname]}
  - {entity: category, effect: reads, facts: [Name]}
  - {entity: period, effect: reads, facts: [Start time, End time]}
  contexts:
    web: {place: 'dashboard::location-dashboard::breakdown'}
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs#period_summary_by_member_by_category}
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityBreakdown.tsx}
---

# Read the breakdown for a range

## Trigger

A coordinator needs to know who did what.

## Outcome

The user sees each member's time by category and each category's time by member.
