---
appliesTo:
- {type: entity, id: guest-period, effect: removes}
permits:
- related:
  - {verb: has, entity: location}
  - {verb: has, entity: location-role}
  - {verb: holds, entity: user}
  when:
  - {entity: location-role, fact: Role, is: Admin}
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_period}
---

# Only a location's admins and super users delete a guest period

Deleting a guest's entry is for an Admin at its location or a super user.
