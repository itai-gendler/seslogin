---
availability:
- {place: 'dashboard::location-dashboard'}
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs#last_period}
- {kind: code, role: implementation, target: web/src/admin/pages/ActivityLastSeen.tsx}
---

# View last seen

When each of the location's own members last signed in anywhere, sortable by name or by time.
