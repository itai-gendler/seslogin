---
appliesTo:
- {type: entity, id: location-role, effect: removes}
permits:
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_user}
---

# Only a super user takes away a user's role at a location

Removing a location from a user is for super users.
