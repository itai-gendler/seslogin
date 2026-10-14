---
appliesTo:
- {type: entity, id: guest-period, effect: changes, facts: [Guest name, Start time, Comment]}
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
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_guest_period}
---

# Only a location's admins and super users correct a guest period

A guest's name, times and comment are changed only from the dashboard.
