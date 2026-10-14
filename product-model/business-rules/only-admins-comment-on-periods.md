---
appliesTo:
- {type: entity, id: period, effect: changes, facts: [Comment]}
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
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_period_time_category}
---

# Only a location's admins and super users write a period's comment

A comment is an admin's note on the period; neither a kiosk sign-out nor a reminder link changes it.
