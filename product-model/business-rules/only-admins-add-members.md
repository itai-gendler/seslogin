---
appliesTo:
- {type: entity, id: member, effect: creates}
permits:
- related:
  - {verb: has, entity: location}
  - {verb: has, entity: location-role}
  - {verb: holds, entity: user}
  when:
  - {entity: location-role, fact: Role, is: Admin}
- actors:
  - super-user
- unattended: true
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_person}
- {kind: code, role: implementation, target: api/src/graphql/auth.rs#require_location_write_access}
---

# Only a location's admins and super users add members there

A user who is Admin at a location, or a super user, adds members to it by hand; member sync adds the members SES holds.
