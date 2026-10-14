---
appliesTo:
- {type: capability, id: reactivate-kiosk}
- {type: entity, id: kiosk, facts: [Device key, Expires]}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#reactivate_session}
---

# A kiosk is reactivated only while its computer shows its QR code

Only a kiosk set up by QR code, not replaced or deleted, whose computer is switched on and showing its QR code, can be reactivated; the computer must then make contact within a short window.
