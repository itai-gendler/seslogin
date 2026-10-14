---
appliesTo:
- {type: entity, id: kiosk, effect: reads, facts: [Setup code]}
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
- {kind: code, role: implementation, target: api/src/graphql/query.rs#code}
---

# Only a location's admins and super users see its kiosks' setup codes

A setup code turns a computer into the location's kiosk, so Read only users never see it.
