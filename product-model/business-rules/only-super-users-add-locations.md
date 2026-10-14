---
appliesTo:
- {type: entity, id: location, effect: creates}
permits:
- actors:
  - super-user
- unattended: true
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_location}
- {kind: code, role: implementation, target: api/src/location_sync.rs#run}
---

# Only super users and location sync add locations

Locations are added by hand by super users, or by the nightly location sync from SES.
