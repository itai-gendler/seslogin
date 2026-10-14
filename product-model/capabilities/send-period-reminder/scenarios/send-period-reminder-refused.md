---
kind: validation
routes:
  web: Web
steps:
- text: The User chooses Remind for a member with no email address, or within fifteen minutes of the last reminder for that period
  kind: actor
  actor: user
  entities:
  - {entity: period, effect: reads, facts: []}
  - {entity: member, effect: reads, facts: []}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
- text: The Product refuses and says why
  kind: condition
  entities:
  - {entity: member, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'dashboard::location-dashboard::previous-periods'}
references:
- {kind: code, role: implementation, target: api/src/period_link.rs#check_reminder_cooldown}
---

# A reminder cannot be sent

## Trigger

The member has no address on record or was just reminded.

## Outcome

No email is sent.
