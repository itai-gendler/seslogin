---
appliesTo:
- {type: entity, id: location-role}
- {type: capability, id: add-user}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#validate_user_grants}
---

# A user holds one role at a location

A user is either Admin or Read only at a location, never both.
