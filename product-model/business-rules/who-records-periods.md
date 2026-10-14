---
appliesTo:
- {type: entity, id: period, effect: creates}
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
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_register2}
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_period}
---

# A period is opened by its member at a kiosk, or recorded by a location's admin or a super user

Members open their own periods by signing in at a kiosk; in the dashboard an Admin at the location, or a super user, records periods for members.
