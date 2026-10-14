---
appliesTo:
- {type: entity, id: kiosk, effect: changes, facts: [Name, Mode, Guests, Quick pick categories, Who's here, Health check URL]}
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
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#update_session}
---

# Only a location's admins and super users change a kiosk's settings

A kiosk's name, mode, options and health check URL are changed by an Admin at its location or a super user.
