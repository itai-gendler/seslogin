---
appliesTo:
- {type: capability, id: sign-in-member}
- {type: capability, id: sign-out-member}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_register2}
---

# A member has at most one open period at a location

Entering a member ID at a kiosk signs the member out when they already have an open period at that kiosk's location, and signs them in otherwise.
