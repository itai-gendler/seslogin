---
availability:
- {place: 'dashboard::location-dashboard'}
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs#period_summary_by_member}
- {kind: code, role: implementation, target: web/src/admin/components/ActivityTotalsDisplay.tsx}
---

# View activity totals

Total time per member and per category at the location over a chosen range, everyone who signed in there included.
