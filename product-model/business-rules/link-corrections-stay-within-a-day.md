---
appliesTo:
- {type: capability, id: correct-period}
- {type: entity, id: period, facts: [Start time, End time]}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#validate_link_edit_duration}
---

# A period corrected from a link is at most 24 hours long

A member correcting a period from a link changes only its category and times, and the period may not be longer than 24 hours.
