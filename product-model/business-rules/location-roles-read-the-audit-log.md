---
appliesTo:
- {type: entity, id: audit-log-entry, effect: reads}
permits:
- related:
  - {verb: has, entity: location}
  - {verb: has, entity: location-role}
  - {verb: holds, entity: user}
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/audit_log.rs}
---

# Only users with a role at a location, and super users, read its audit log

Admin and Read only users read their location's log; only super users read the log across every location.
