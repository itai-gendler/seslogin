---
appliesTo:
- {type: entity, id: location-role, effect: changes}
permits:
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_user}
---

# Only a super user changes a user's role at a location

Switching between Admin and Read only is for super users.
