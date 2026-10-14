---
availability:
- {place: 'dashboard::location-dashboard'}
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs#period_summary_by_day_by_category_by_member}
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityDailyBreakdown.tsx}
---

# View the daily breakdown

Each day's time per category and member over a chosen range.
