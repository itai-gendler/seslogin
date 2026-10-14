---
availability:
- {place: 'dashboard::location-dashboard'}
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/query.rs}
---

# Browse periods

The periods and guest periods at the location, newest first and grouped by day: everyone who signed in or out there, members visiting from other units included. Filterable by name and category, with the incomplete periods — those still signed in — on a page of their own.
