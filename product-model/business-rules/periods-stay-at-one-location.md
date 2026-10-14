---
appliesTo:
- {type: capability, id: sign-in-member}
- {type: capability, id: sign-out-member}
- {type: entity, id: period}
references:
- {kind: doc, role: intent, target: MANUAL.md}
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_register2}
---

# A period belongs to the location it was signed in at

Any member can sign in at any location's kiosk and the period belongs to that location; signing out at another location's kiosk opens a period there instead, and each location's period closes only at that location.
