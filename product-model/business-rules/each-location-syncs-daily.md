---
appliesTo:
- {type: capability, id: sync-members}
- {type: entity, id: location, facts: [Last successful member sync]}
references:
- {kind: code, role: implementation, target: api/src/bin/dispatcher-lambda.rs}
- {kind: code, role: implementation, target: infra/scheduler.tf}
---

# Each location linked to SES is synced once a day at its own hour

Locations are spread across the hours of the day, each always at the same hour, so every roster is refreshed once every 24 hours; an admin's Sync now runs one sooner.
