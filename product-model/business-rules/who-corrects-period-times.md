---
appliesTo:
- {type: entity, id: period, effect: changes, facts: [Start time, End time, Category]}
permits:
- related:
  - {verb: has, entity: member}
- related:
  - {verb: has, entity: location}
  - {verb: has, entity: location-role}
  - {verb: holds, entity: user}
  when:
  - {entity: location-role, fact: Role, is: Admin}
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_sign_out}
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_period_time_category}
- {kind: code, role: implementation, target: api/src/graphql/auth.rs#require_period_write_access}
---

# A period's times and category are set by its member, a location's admin or a super user

The member sets them when signing out at a kiosk and when correcting the period from a reminder link; an Admin at the period's location, or a super user, corrects them in the dashboard.
