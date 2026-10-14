---
appliesTo:
- {type: capability, id: sync-members}
- {type: entity, id: member, facts: [SES record]}
references:
- {kind: code, role: implementation, target: api/src/member_sync.rs#absence_candidate_cap}
---

# A sync that would mark too many members missing changes nothing

When more of a location's roster would be marked missing than the allowed share, that location's sync stops before making any change and is left for a person to look at.

## Rationale

Past that point a genuine mass departure cannot be told apart from a bad roster from SES.
