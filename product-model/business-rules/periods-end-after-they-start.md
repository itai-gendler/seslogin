---
appliesTo:
- {type: capability, id: sign-out-member}
- {type: capability, id: add-period}
- {type: capability, id: edit-period}
- {type: capability, id: correct-period}
references:
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#scan_sign_out}
- {kind: code, role: implementation, target: api/src/graphql/mutations.rs#create_period}
---

# A period ends after it starts

Signing out, recording, editing or correcting a period is refused unless its end comes after its start.
