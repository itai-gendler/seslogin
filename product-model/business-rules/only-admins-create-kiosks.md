---
appliesTo:
- {type: entity, id: kiosk, effect: creates}
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
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_session}
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#enroll_session}
---

# Only a location's admins and super users create its kiosks

Creating a kiosk with a setup code, or enrolling one by QR code, is for an Admin at the location or a super user.
