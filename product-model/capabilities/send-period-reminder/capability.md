---
availability:
- {place: 'dashboard::location-dashboard'}
domain: activity
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#send_period_edit_link}
---

# Remind a member about a period

An admin emails a member a reminder to check one of their periods, with a link that lets the member correct it themselves for 48 hours. Still on trial: offered only to users marked Developer.
