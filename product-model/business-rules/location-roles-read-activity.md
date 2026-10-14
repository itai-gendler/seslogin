---
appliesTo:
- {type: entity, id: period, effect: reads, contexts: [{place: 'dashboard::location-dashboard'}]}
permits:
- related:
  - {verb: has, entity: location}
  - {verb: has, entity: location-role}
  - {verb: holds, entity: user}
- actors:
  - super-user
- unattended: true
references:
- {kind: code, role: implementation, target: api/src/graphql/auth.rs#require_location_access}
---

# Only users with a role at a location, and super users, see its activity in the dashboard

Admin and Read only users alike see a location's periods and reports; super users see every location's.
