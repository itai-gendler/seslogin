---
appliesTo:
- {type: entity, id: guest-period, effect: changes, to: Signed out}
permits:
- actors:
  - guest
  when:
  - {entity: kiosk, fact: Guests, is: 'On'}
- related:
  - {verb: has, entity: location}
  - {verb: has, entity: location-role}
  - {verb: holds, entity: user}
  when:
  - {entity: location-role, fact: Role, is: Admin}
- actors:
  - super-user
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_guest_sign_out}
---

# A guest is signed out at a kiosk that offers guests, or by a location's admin or a super user

A guest leaving signs out from the guest list at a kiosk whose Guests setting is on; an Admin at the location, or a super user, can close a guest's entry from the dashboard.
