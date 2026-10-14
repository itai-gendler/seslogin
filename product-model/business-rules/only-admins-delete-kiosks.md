---
appliesTo:
- {type: entity, id: kiosk, effect: removes}
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
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#delete_session}
---

# Only a location's admins and super users delete its kiosks

Deleting a kiosk is for an Admin at its location or a super user.
