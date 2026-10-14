---
availability:
- {place: 'dashboard::location-dashboard'}
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_period}
---

# Add a period

An admin records a period for a member at the location, with its category, times and an optional comment.
