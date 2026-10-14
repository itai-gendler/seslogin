---
appliesTo:
- {type: entity, id: guest-period, effect: creates}
permits:
- actors:
  - guest
  when:
  - {entity: kiosk, fact: Guests, is: 'On'}
references:
- {kind: code, role: implementation, target: web/src/kiosk/components/ScanController.tsx}
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_guest_sign_in}
---

# A guest signs in only at a kiosk that offers guests

Guests are signed in by name only at a kiosk whose Guests setting is on.
