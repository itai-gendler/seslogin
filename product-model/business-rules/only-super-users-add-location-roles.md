---
appliesTo:
- {type: entity, id: location-role, effect: creates}
permits:
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_user}
---

# Only a super user gives a user a role at a location

Location roles are given by super users only.
