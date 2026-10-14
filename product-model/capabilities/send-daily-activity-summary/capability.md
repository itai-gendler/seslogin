---
availability:
- {place: 'dashboard::location-dashboard'}
references:
- {kind: code, role: implementation, target: api/src/activity_summary.rs}
---

# Send the daily activity summary

Each morning every enabled user who chose locations for the daily email is sent a summary of the previous day's activity at those locations.
