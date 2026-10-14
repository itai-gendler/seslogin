---
availability:
- {place: 'dashboard::location-dashboard'}
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs#period_summary_by_member_by_category}
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityBreakdown.tsx}
---

# View the activity breakdown

Time per member broken down by category, and per category broken down by member, over a chosen range.
