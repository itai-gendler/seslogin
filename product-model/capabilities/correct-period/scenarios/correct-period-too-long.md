---
kind: validation
routes:
  web: Web
steps:
- text: The Member saves times more than 24 hours apart, or an end before the start
  kind: actor
  actor: member
  entities: []
  contexts:
    web: {place: 'time-entry-link::time-entry'}
- text: The Product refuses and the Period keeps its times
  kind: condition
  entities:
  - {entity: period, effect: reads, facts: [Start time, End time]}
  contexts:
    web: {place: 'time-entry-link::time-entry'}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#validate_link_edit_duration}
---

# Give a period longer than a day

## Trigger

The member mistyped a date.

## Outcome

Nothing changes.
