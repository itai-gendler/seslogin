---
availability:
- {place: 'dashboard::location-dashboard'}
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs#period_summary_by_day_by_member}
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityHeatmap.tsx}
---

# View the attendance heatmap

Day-by-day attendance of the location's own members over a chosen preset range, members still signed in counting for today.
