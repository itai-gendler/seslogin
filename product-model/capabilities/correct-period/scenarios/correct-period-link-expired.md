---
kind: validation
routes:
  web: Web
steps:
- text: The Member opens a link more than 48 hours old, or for a Period since deleted
  kind: actor
  actor: member
  entities:
  - {entity: period, effect: reads, facts: []}
  contexts:
    web: {place: 'time-entry-link::time-entry'}
- text: The Product shows that the link is not valid and to ask the unit for a new one
  kind: condition
  entities: []
  contexts:
    web: {place: 'time-entry-link::time-entry'}
references:
- {kind: code, role: implementation, target: web/src/period/PeriodEdit.tsx}
- {kind: code, role: implementation, target: api/src/period_link.rs}
---

# Open a link that no longer works

## Trigger

The link is old.

## Outcome

Nothing about the period is shown.
