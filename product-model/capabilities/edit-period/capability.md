---
availability:
- {place: 'dashboard::location-dashboard'}
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_period_time_category}
---

# Edit a period

An admin corrects a period's category, times and comment, or a guest period's name, times and comment.
