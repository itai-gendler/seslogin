---
appliesTo:
- {type: capability, id: send-period-reminder}
- {type: entity, id: user, facts: [Developer]}
references:
- {kind: code, role: implementation, target: web/src/admin/components/ActivityListTable.tsx}
---

# Only a location's admins who are marked Developer send reminders

Reminders are still on trial: the Remind button is offered only to users marked Developer who are Admin at the period's location, and only for a member's period, never a guest's.
