---
appliesTo:
- {type: capability, id: send-period-reminder}
- {type: entity, id: period}
references:
- {kind: code, role: implementation, target: api/src/period_link.rs#check_reminder_cooldown}
---

# A period's member is reminded at most once every fifteen minutes

A second reminder for the same period within fifteen minutes is refused before anything is sent.
