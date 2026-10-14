---
appliesTo:
- {type: entity, id: location, effect: changes}
permits:
- actors:
  - super-user
- unattended: true
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_location}
---

# Only super users and the syncs change a location

A location's settings are changed by super users; location sync renames it and member sync records its last successful sync.
